
## $DOC.txt
```
This version of the disassembler originated from CBT and the original
author is Dick Thornton in 1986.  You can refer another version of
disassembler in CBT file 217 if the load module does not have RI, RIL
and RRE instruction.

The difference between this version with file 217.
1. It supports RI and RIL instructions
   AHI, LHI, CLI, Jx, BRAS
   AFI, LFI, CFI
   Thanks that IBM introduced the new assembler instructions to simplify
   assembler coding (ie Use relative branch instruction, it is no need
   to specify the program base registers in the assembler program).
2. It supports most RRE, RXE and RXY instructions.
3. Bigger SYMBOL table
4. Use linkage stack to save area and macro SVLNK is no longer required
   Use RI instructions (ie change BE to JE, AH to AHI and etc) to
   eliminate each program base register only have 4K restriction. Only
   1 program register to keep track the internal variable of HDISASM.
   New routines can added into HDISASM without major change to the
   logic of HDISASM.
5. Pre-assembler is also performed even no USING statement, as relative
   jump instruction does not required program base register.

The difference between HDISASM with ASMDASM
1. Conditional branch instructions use the extended mnemonics.
2. ULABL is extended from 8 to 12 characters

Sample Output of HDISASM
         AHI   R1,4
         J     A001FC6                     BRANCH
A001FBC  MVC   2(1,R1),1(R5)               COPY DATA
         AHI   R1,3
A001FC6  MVI   0(R1),X'5D'
A001FCA  LR    R10,R1
         S     R10,A0002B8
         L     R9,A0002E4
         BR    R9                          BRANCH
A001FD6  MVC   A000334(8),4(R12)           COPY DATA
         LA    R1,A00033B
A001FE0  CLI   0(R1),C' '                  COMPARE
         JNE   A001FEC                     BRANCH IF NOT EQUAL
         BRCT  R1,A001FE0                  CALL SUBRTN
A001FEC  LTR   R10,R10                     TEST

3. Provide more comments for some assembler instructions


Technical problems
==================
1. Undocmented Assmembler instructions
   The following assembler instructions are not documented in "Principle
   of Operations".
   0105, 0106
   B25F, B264, B265, B266, B267 and B268
2. Does not support load module in PDSE.
3. Does not support RRF op codes.

Program description of dissassembler
====================================
HDISASM is a one-pass disassembler which produces an assembler language
source program from a CSECT within a load module. Control cards permit
specification of areas containing no instructions, allow base registers
to be provided so that symbolic labels may be created during
disassembly, and definition of DSECTs to be used during disassembly.
Conditional branch instructions use the extended mnemonics, where
possible, and explicit registers are denoted by R0, R1, ... R15.
Informational comments are given on SVC's, and various BAL instructions
to aid in creating a documented source program.

1. JCL requirements:
      a. EXEC card:        To execute PGM=HDISASM. A parm field may
                           be specified if floating point and/or
                           privileged instructions are to be
                           found in the module.
      b. STEPLIB DD card:  Optional, specify the PDS containing
                           the module HDISASM.
      c. LOADLIB DD card:  optional, specify PDS containing the
                           modules HDISASM1 and HDISASM2, if other than
                           a linklist library or STEPLIB.
      d. SYSLIB DD card:   specify PDS containing the module to be
                           disassembled.
      e. SYSPRINT DD card: optional, specify the printed
                           output dataset. BLKSIZE must be
                           specified as a multiple of 121.
                           RECFM=FBA,LRECL=121 is hard coded.
      f. SYSPUNCH DD card: optional, specify printed output
                           dataset. BLKSIZE must be specified
                           as a multiple of 80.
                           RECFM=FB,LRECL=80 is hard coded.
      g. SYSIN DD card:    contains control cards. The MODULE-CSECT
                           card is required. BLKSIZE must be a
                           multiple of 80. RECFM=FB,LRECL=80 is
                           hard-coded.


2. PARM field on the EXEC card: Omit the parm field, unless floating
        point and/or privileged instructions are to be found in the
        CSECT being disassembled. When the parm field is not specified,
        entries for the privileged and floating point instructions are
        erased from the internal instruction tables used during
        disassembly. Valid PARM fields are:

            PARM=(SUPVR)     assemble privileged instructions
            PARM=(FLTPT)     assemble floating point instructions
            PARM=(SUPVR,FLTPT) assemble both privileged and
                             floating point instructions.


3. Control cards entered in the SYSIN dataset.
        Data is contained only in columns 1-72. Columns 73-80 may be
        used for any desired purpose. Comment cards may be entered with
        an asterisk (*) in column 1. In addition, columns beyond the
        last specified may be used for any purpose. Leading zeros must
        be included in all fields giving hex or decimal data. Name
        fields must be left justified with trailing blanks. Hex fields
        may contain only the hex digits 0-9 and A-F, while decimal
        fields may contain only digits 0-9.  The MODUKE-CSECT card must
        be the first card in the input stream. DSECT definitions may not
        include any other control cards. Using cards for DSECTs must be
        entered at some point after the DSECT definition. Data-only
        cards and program USING cards may be entered in any order except
        within DSECT definitions.


   a. MODULE-CSECT card (required), must be the first card in the SYSIN
        stream. Specifies the module name and CSECT name. Module name
        is required, and must name an entry in the directory of the PDS
        specified by the SYSLIB DD card. CSECT name is optional. If
        specified, the named CSECT must exist in the module. If omitted,
        the CSECT with ESDid=0001 is disassembled.
      format: free-form, with module name preceding CSECT name.
              At least one blank must separate module name and
              CSECT name. The names may be surrounded by any number
              of blanks (see the JCL example).


   b. Data-only card (optional). Used to describe areas of the CSECT
                being disassembled which contain no instructions. Use of
                this card eliminates creation of instructions from
                constant data. Up to 256 data-only cards may be entered.
                These cards may occur anywhere in the SYSIN stream after
                the MODULE-CSECT card, but not within a DSECT definition
                set.
      format:
              col  1-4  : literal 'data'
              col   5   : blank
              col  6-11 : offset to beginning of area in hex
              col   12  : blank
              col 13-18 : offset to end of area in hex



   c. DSECT definitions (optional). A DSECT is defined by a header card
              followed by a variable number of field definition cards
              (up to 9999 of them). No other control card may be entered
              within a DSECT definition. Up to 256 DSECT definitions may
              be entered.

      DSECT header card format:
           col 1-8    : DSECT name
           col 9      : blank
           col 10-14  : literal 'DSECT'
           col 15     : blank
           col 16-19  : number of field cards to follow (decimal)

      DSECT field card format:
           col 1-8    : field name
           col 9      : blank
           col 10-13  : offset to left end of field (decimal)
                        maximum offset is 4095
           col 14     : blank
           col 15-17  : length of field in bytes (decimal)
                        maximum length is 256



   d. Ulabl cards. These cards define user labels to be placed on
                 statements within the program. If program base
                 registers are set up with using cards, these will also
                 be generated as symbolic operands on instructions.
                 Format is:

           col  1-5   : literal 'ulabl'
           col   6    : blank
           col  7-18  : label name
           col  19    : blank
           col 20-25  : offset to left end of field, in hex.
           col  26    : blank
           col 27-29  : length of field in dec. 256 is max.

   e. Using cards. These cards define base register usage. Up to 256
                 using cards may be entered. Use of these cards permits
                 the disassembler to convert explicit base-displacement
                 addresses to symbolic labels. Labels created within the
                 program will be 7 characters long. The first character
                 is 'A', followed by the 6-hex-digit offset to the
                 label. A using card must be entered for each DSECT to
                 be used.

     format:

          col 1-5   : literal 'USING'
          col 6     : blank
          col 7-12  : offset to begin loc for using range in hex
                      (this is where the using statement will occur)
          col 13    : blank
          col 14-19 : offset to ending loc for using range in hex
                      (this is where the drop statement will occur)
          col 20    : blank
          col 21    : base resister to be used (hex, 1-F)
          col 22    : blank
          col 23    : type, P=program base, D=DSECT base
          col 24    : blank
          col 25-30 : initial base register value if type P in hex
          col 25-32 : DSECT name if type D


4. Suggestions for use: On the first pass, do not use a SYSPUNCH DD
          card, but print the SYSPRINT listing. Use the listing to
          determine which registers are used as program base registers,
          their initial values, and their ranges. Make up USING cards
          for these. Find any places where no instructions should be
          generated (only constants), and make up data-only cards for
          these ranges. If you can determine any registers that are
          bases for areas which can be used for DSECTs (CVT reference,
          etc.), determine the range of valid use, and make up DSECT
          definitions and using cards for these. Make a second run,
          including the above cards, and creating a source program
          output with the SYSPUNCH DD card.



5. Output description:

   a. SYSPUNCH: this output contains the disassembled source program.
           Statement names begin in column 1, mnemonics begin in column
           10, operands in col 16, and an occasional comment begins in
           column 44. A sequence number (by tens) is in columns 73-80.
           Comments are included to show the macro name associated with
           SVC's, and other statements are flagged to aid in
           identification of certain operations:

              BALR 14,15              LINKAGE
              BALR X,0                ADDRESS SET
              other BALR'S            NON-STD LINKAGE
              BAL 0,XXX and BAL 1,XXX PARM SET BRCH
              BAL X,XXX               PERFORM
              BCTR Rx,0               DECREMENT REGISTER BY ONE
              BRAS Rx,XXX             CALL SUBRTN
              BSM  Rx,Rx              RETURN AND SET AMODE
              CPYA instructions       COPY ACCESS REGISTER
              MVC instructions        COPY DATA
              SAC instructions        ASC MODE TO AR MODE/PRIMARY MODE
              STM instructions        SAVE REGS
              STAM instructions       SAVE ACCESS REGS
              LM  instructions        RESTORE REGS
              B/JO instructions       BRANCH IF ONE
              B/JZ  instructions      BRANCH IF ZERO
              B/JE  instructions      BRANCH IF EQUAL
              B/JNE instructions      BRANCH IF NOT EQUAL
              B/J instructions        BRANCH
              BR R14                  EXIT
              Abs. location X'10'     CVT ADDRESS
              Abs. location X'4C'     CVT ADDRESS
              Other abs. locations    PSA REFERENCE

           When used in explicitly in instructions, registers are
           specified as R0, R1,... R15. An YREGS macro is generated at
           the end of the program to create the appropriate EQU
           statements. If any DSECTs were defined in the SYSIN dataset,
           they will be near the end of the source program. The extended
           mnemonics are used for conditional branches wherever
           possible.



    b. SYSPRINT content:

       directory information: contains data from the directory
                              entry of the module containing
                              the CSECT to be disassembled.
       ESD table: a formatted list of all external symbol entries
                              found in the module.
       RLD table: a formatted listing of all relocation dictionary
                              entries pertaining to this CSECT.
       user entered cards: a list of the cards entered by the user,
                              with diagnostics, if appropriate.
       phase 1 label table: a list of all the labels to be used during
                              disassembly including those developed from
                              ESD entries, RLD entries, and generated
                              names resulting from using card
                              processing.
       text: a storage-dump formatted listing of the text which
                              comprises the CSECT being disassembled.
       source listing: a printout of the generated source program
                              statements, including the hex value which
                              resulted in the instruction's creation.


6. User Abends:

        HDISASM may end with one of two user abends:

        U0777 - There is an invalid parm specified.
        U0888 - Check in the SYSPRINT listing for an error message
                describing the error causing the abend (e.g. table
                overflow).


Program processing description.

 HDISASM functions:

 . Process the parm field, if any: set indicators used by
   HDISASM1 and HDISASM2 to set up their instruction tables.
 . Open all files.
 . Get storage for the symbol table, RLD table, and data-only
   tables (244,768 bytes total).
 . Process the module-CSECT card to obtain the member
   and CSECT names.
 . Issue BLDL against SYSLIB to obtain directory info for
   the member specified. If the specified member is an
   alias, re-issue a BLDL for the real member. Print
   directory information.
 . Point to the member in the SYSLIB PDS, and process the
   member. Load modules contain an external symbol dictionary
   followed by text and relocation dictionary information.
   all ESD info for the module precedes the first control
   record. A control record precedes each block of text.
   RLD info for the text follows each text block. Processing
   of load module information is as follows:
   a. Build an external symbol table, using the CESD blocks.
   b. Search for the desired CSECT as the table is being built. This
      CSECT must be found before the first control record.
   c. Read blocks until a control record for the desired CSECT is found
      (by ESD-id).
   d. When found, issue GETMAIN for an area large enough to contain the
      entire text.
   e. Place text blocks in contiguous storage locations and maintain
      during disassembly.
   f. Use RLD information for the CSECT to build the RLD table.
 . Load and perform HDISASM1.
 . If any errors found by HDISASM1, terminate processing.
 . Print the final label table to be used during disassembly.
 . Load and execute HDISASM2.
 . Generate the DSECT entries.
 . Generate the YREGS macro and end statements
 . Terminate processing
 . Note: The OP code table is created base upon IBM OP code table
         ASMADOP and you can find it HLASM Toolkit loadlib.

 HDISASM1 functions:

 HDISASM1 is the second phase of disassembly, and is performed by
 HDISASM. A common data area, defined in HDISASM, is passed to this
 program on entry.

 The SYSIN file is read to exhaustion. Using cards are reformatted and
 stored in a table - up to 256 using statements may be entered. DSECT
 cards may follow the using statements. When used, DSECT statements are
 reformatted, and built into tables. A maximum of 256 DSECTs may be
 entered. Data only cards may be included before, between, or after
 DSECTs to show areas in the program where no instructions occur. Up to
 256 data only areas may be specified.

 At eof on SYSIN, a pseudo dis-assembly pass is made using the text
 stored by HDISASM. Any resolvable address within the text is used to
 create a new entry in the label table, which will be used by HDISASM2
 in the actual dis-assembly pass.

 Disassembly tables are set up similarly to those used by HDISASM2 for
 the simulated disassembly performed in this module when any program
 base register using statements are entered.

 Storage is obtained for the DSECT table and using table, and addresses
 of these tables are stored in the common parameter area. Using and
 DSECT cards are edited, reformatted, and placed in the appropriate
 tables. If any errors are found, they are printed, and the disassembly
 will be terminated on return to HDISASM.

 Storage is obtained for the label table, and a simulated dis-assembly
 is performed to create label table entries for labels which will be
 generated for base-displacement addresses by HDISASM2. On return to
 HDISASM, these labels will be sorted with external symbol and RLD
 labels to form the final label table to be used by HDISASM2.



 HDISASM2 functions:

 This sub-program is called by HDISASM after completion of processing by
 HDISASM1. The final label table and module text is in an area of
 storage. A common parameter area is defined in HDISASM, and passed to
 this program.

 Text bytes are used to create assembly language statements, and
 machine instruction statements. Output is written to the SYSPUNCH
 dataset for further processing by other modules.

 A text byte is considered to be an instruction if it occurs on a
 halfword boundary, is a valid op-code, and is followed by a valid
 op-code. Unconditional branches need not be followed by a valid
 op-code, however. The privileged and floating point instructions are
 not treated as instructions unless the user specified their inclusion
 at exec time.



Installation.

 a. Assemble and link the three csects, HDISASM, HDISASM1, and HDISASM2.
    The three csects will all be linked into a single module with entry
    point HDISASM.
 b. The SVC table and instruction op code tables in HDISOPTB should be
    checked for operating system validity, and currency with the
    hardware from time to time. You can refer IBM opcode table ASMADOP
    or "Principle of Operations"
 c. Direct technical inquiries, comments, suggestions for improvements,
    etc, to:
         albertcpcheng@hotmail.com

Future enhancement.
 a. Support MVS, CICS and DB2 mapping
 b. This version only format mnemonics up to 6 characters. It will
    support OPCODE with mnemonics longer than 6 characters. For example
    Instruction ALGHSIK is 7 characters.
 c. Format opcode E700-E7FF and EC00-ED49
```

