
## $CLDOC.txt
```
THIS MEMBER ($CLDOC) DOCUMENTS THE CHANGES MADE TO THE QUEUE COMMAND
ON THE SHARE JES2 MODS TAPE.  THE CHANGES WERE MADE BY:

     JOHN KINN
     LOCKHEED, CALIFORNIA COMPANY
     PLANT A-1, BUILDING 67, DEPARTMENT 8321
     P.O. BOX 551
     BURBANK, CALIFORNIA 91520

     PHONE: (818) 847-7492

     SHARE INSTALLATION CODE = CL


CL001 -- USE THE NUMBER OF AVAILABLE TRACK GROUPS FOR ACTIVE SPOOL
         EXTENTS RATHER THAN THE MAXIMUM POSSIBLE IN USE FOR
         PERCENTAGE COMPUTATIONS IN MODULE CTGPS.

CL002 -- MODIFY THE FIND COMMAND TO ALLOW UNQUOTED STRINGS

CL003 -- ALTER THE FTIM COMMAND TO SUPPORT MVS/XA SYSLOG

CL004 -- ADD THE COMMAND JHIS TO THE HELP LIST.

CL005 -- FORMAT THE INFORMATION FOR A JQE IN THE SETUP QUEUE

CL006 -- WHEN QUEUE IS INVOKED, THE DATA SET NAME PREFIX FOR
         THE HASPCKPT AND HASPACE DATA SETS CAN BE SPECIFIED
         VIA THE KEYWORD PREFIX(XXXX).  THE UNIT AND VOLUME SERIAL
         CAN ALSO BE SPECIFIED BY GIVING THE UNIT AND VOL KEYWORDS
         RESPECTIVELY.  THUS THE SYNTAX OF THE INITIAL QUEUE COMMAND
         IS AS FOLLOWS:
           (1) QUEUE
           (2) QUEUE CMD
           (3) QUEUE * PREFIX(XYZ)
           (4) QUEUE CMD PREFIX(XYZ)
           (5) QUEUE * VOL(ABCDEF)
           (6) QUEUE CMD VOL(ABCDEF)
            ETC
         IN (1) THE DEFAULT PREFIX, UNIT, AND VOL (I.E. THE ONES
         ASSEMBLED IN QCOMMON) ARE USED AS WELL AS THE DEFAULT
         INITIAL COMMAND (ASSEMBLED AS HELP).
         IN (2) THE INITIAL COMMAND IS 'CMD' RATHER THAN 'HELP'
         IN (3) THE INITIAL COMMAND IS 'HELP' BUT THE JES2 DATA
         SET PREFIXES ARE CHANGED TO XYZ.
         IN (4) THE INITIAL COMMAND IS 'CMD' AND THE JES2 PREFIX
         IS XYZ.
         IN (5) THE INITIAL COMMAND IS 'HELP' BUT THE VOLUME SERIAL
         FOR THE CHECKPOINT IS CHANGED TO ABCDEF.
         IN (6) THE INITIAL COMMAND IS 'CMD' AND THE CHECKPOINT
         VOLUME SERIAL IS CHANGED TO ABCDEF.

CL007 -- DO NOT DISPLAY PDDB (IN 'ALL' MODE) IF IT IS A
         PLACEHOLDER

CL    -- 1) IOT COMMAND
         2) ALL FUNCTIONS ARE NOW SUPPORTED FOR SYSTEM JQES
               LIST, DJ, SPIN, SAVE, ETC.
         3) NON-CONTIGUOUS SPOOL EXTENTS NOW WORK

CL008 -- SL COMMAND WITH NO OPERANDS NOW WORKS (AS IT IS DOCUMENTED TO)

CL009 -- TGPS WILL NOTE THOSE JOBS CURRENTLY EXECUTING IN ITS
         TOP 15 USERS OF TRACK GROUPS

CL010 -- FIX ABEND0C4 IN LISTDS IF SKIPPING A SPANNED RECORD WITH
         CARRIAGE CONTROL
```

## $ONLDOC.txt
```
THIS MEMBER ($ONLDOC) DOCUMENTS CHANGES MADE TO THE QUEUE COMMAND BY:

     ROBERT M. JINKINS
     OAK RIDGE NATIONAL LABORATORY
     BLDG. 4500-N  MS-259
     P.O. BOX X
     OAK RIDGE, TENNESSEE  37830

     PHONE: (615) 574-7208/5300
             FTS  624-7208/5300

     SHARE INSTALLATION CODE = OR

     LAST UPDATE = MAR 84


ONL01 -- CREATED THE &QBGEN GOBAL SET SYMBOL TO CONTROL THE EXPANSION
         OF JES2 AND SYSTEM CONTROL BLOCK DSECTS SEPARATELY FROM THE
         EXPANSIONS OF MACROS WITHIN THE CODE CONTROLED BY &QGEN.  THE
         QPRBGEN MACRO WAS ALSO CREATED FOR THIS PURPOSE.

ONL02 -- CREATED A COMMAND FUNCTION AUTHORIZATION CSECT (MEMBER AUTH)
         AND A MACRO USED TO REQUEST AUTHORIZATION CHECKING (QAUTHCK).
         ALL CODE CONCERNED WITH WHO USES WHICH QUEUE SUBCOMMAND, AND
         ON WHICH JOBS, HAS BEEN MOVED TO THE AUTH CSECT.  SEE THE
         COMMENTS AT THE BEGINNING OF THE AUTH CSECT FOR ADDITIONAL
         INFORMATION.

         THE HELP CSECT WAS REWRITTEN TO ALLOW CONTROL OVER WHO CAN
         LOOK AT HELP INFORMATION FOR WHICH SUB-COMMANDS.  SEE THE
         COMMENTS AT THE BEGINNING OF THE HELP CSECT FOR ADDITIONAL
         INFORMATION.

         CODE WAS ALSO ADDED TO THE INIT CSECT TO VERIFY A TSO
         ENVIRONMENT AND TO VERIFY SOME FIELDS IN THE COMMAND PROCESSER
         PARAMETER LIST (CPPL).  THIS CODE SUPERCEEDS THE UF010 CHANGE.

         THE FOLLOWING MODS WERE RELOCATED:

              FCI01 (CODE FOR MVS/SP JES2 WAS ALSO ADDED)
              RNB03
              RNB05
              RNB08

              NOTES:
               (1) SOME CHANGES WERE MADE TO THE ABOVE RELOCATED
                   CODE.  HOWEVER, THE OLD PARSE TEXT WAS USED TO
                   AID IN THE IDENTIFICATION OF ALL CODE PERTAINNING
                   TO A GIVEN FUNCTION.
               (2) AS OF JUNE 1983, THE ABOVE RELOCATED CODE HAS
                   NOT BEEN TESTED BY FCI OR RNB.

         THE FOLLOWING MODS WERE SUPERCEEDED:

              RNB02
              UF033

ONL03 -- ENSURED THAT JCT'S AND IOT'S READ FROM THE SPOOL BELONG TO
         THE JOB FOR WHICH THEY WERE READ.

ONL04 -- CHANGED THE LISTDS CSECT TO DISTINGUISH BETWEEN EMPTY AND
         NONEXISTENT DSID'S.  ALSO, SINCE THE DSID FIELD IS OFTEN
         CLEARED BY AUTHORIZATION CHECKING CODE, A SEPERATE FIELD IN
         THE QCOMMON CSECT IS USED TO KEEP TRACK OF THE LAST DSID FOR
         THE "L * +/-" COMMAND.  THE FINDJOB, LIST, AND LISTDS CSECT'S
         USE THE NEW FIELD.

ONL05 -- CHANGED THE JLOG COMMAND TO BETTER DETERMINE IF THERE IS
         A VALID JOB LOG.  THIS SUPERCEEDS THE RNB04 CHANGE.

ONL06 -- USES THE &QONL GOBAL SET SYMBOL TO ALLOW THE GENERATION
         OF ONL'S OWN BRAND OF CONTROL IN THE AUTH CSECT.

ONL07 -- ADDED THE THE FOLLOWING COMMAND ABBREVIATIONS:

            DELE FOR DEL
            CANC FOR CAN

ONL08 -- USES THE &QONL GOBAL SET SYMBOL TO SKIP TESTING A V-TYPE
         ADDRESS CONSTANT BEFORE LOADING QUEUECMN TO PREVENT GETING
         CONDITION CODES ON THE LINK-EDIT.

ONL09 -- ADDED THE &QDSPRFX GOBAL SET SYMBOL TO DEFINE THE FIRST LEVEL
         QUALIFIERS FOR THE HASPCKPT AND HASPACE DATA SET NAMES.  THE
         DEFAULT IS 'SYS1'.  A VALUE OF 'JES2' IS USED IF &QONL IS SET
         TO ONE.

ONL10 -- CHANGED THE "DC" COMMAND TO SUPPORT AN OPERAND OF "J" (JOB)
         IN ADDITION TO "B", "S", AND "T" (BATCH, STC, AND TSU).

ONL11 -- ADDED SP V1.3.3 SUPPORT FOR THE DD COMMAND.

ONL12 -- USES THE &QONL GOBAL SET SYMBOL IN CSECT REPOS TO DO AN
         'OLD TIME' FIND IF THE STRING BEGINS WITH A SLASH ("/").

ONL13 -- QUOTED STRING SPECIFICATIONS FOR THE FIND COMMAND MAY BE
         DELIMITED WITH DOUBLE QUOTES AS WELL AS SINGLE QUOTES.
         THE FIND COMMAND HELP INFORMATION HAS ALSO BEEN UPDATED.

ONL14 -- DEFINED THE QFLG1SDS BIT TO INDICATE WHEN THE CURRENT JOB
         IS A SYSTEM DATA SET JOB AND DOES NOT HAVE A JCT.  THE
         FLAG IS DEFINED IN QCOMMON, SET IN FINDJOB, AND IS TESTED
         BY VARIOUS MODULES.

ONL15 -- ADDED ACF2 SP 1.3.3 SUPPORT TO THE JHIST COMMAND.

ONL16 -- ADJUSTED ALL JCT ADDRESSABILITY BY BUFSTART-BUFDSECT.

ONL17 -- USES THE &QONL GOBAL SET SYMBOL IN CSECT CJHIST TO FORMAT
         INSTALLATION SPECIFIC INFORMATION.

```

## $RNBDOC.txt
```
THIS DATASET WAS OBTAINED FROM FILE 322 ON VER193 OF THE CBT TAPE, AND
WAS THEN MODIFIED AT RAINIER NATIONAL BANK.

RNB00 -                - MOVED DSECTS AROUND FOR IFOX ASSEMBLER
        Q4  (DDNAME)
        Q10 (INIT)
        Q12 (JLOG)
        Q15 (LISTDS)
        Q20 (SEARCH)
        Q25 (FINDPDDB)
        Q26 (SYSOUT)
        Q33 (CPPDB)
RNB01 - Q1  (QUEUE)    - FIX TO FINAL TPUT MESSAGE TO ALLOW TO WORK WITH
                           BOTH TCAM AND VTAM
RNB02 - Q10 (INIT)     - REMOVE PART OF UF010: DON'T USE OPER AUTHORITY
                           TO SET QXAUTH. ALSO UF024: DON'T USE DBC.
RNB03 - Q10 (INIT)     - FOR RACF: IF &QRACF = 1, AND IF &QNEWUSR ISN'T
                           NULL, THEN IF APF-AUTHORIZED CHANGE THE
                           USERID IN THE ACEE SO THE USER CAN ACCESS A
                           RACF-PROTECTED SPOOL/CHECKPOINT DATA SET.
      - Q16 (PARSE)    - IF &QRACF = 1 THEN USE RACF TO CHECK AUTHORITY
                           TO USE THE XP COMMAND.
      - Q17 (READSPC)  - IF &QRACF = 1 THEN WHEN A JCT IS READ FROM THE
                           SPOOL BLANK THE PASSWORD AND NEWPASSWORD.
      - Q22 (XDS)      - IF &QRACF = 1 THEN DO A SPECIAL CHECK TO SEE IF
                           THE USER IF ALLOWED TO DO THE XDS COMMAND.
RNB04 - Q12 (JLOG)     - FIX TO ALLOW JLOG TO WORK FOR JOBS THAT ARE IN
                           EXECUTION BUT THAT HAVEN'T FINISHED THE FIRST
                           STEP. THIS WILL SHOW ONLY THE 'JOB STARTED'
                           MESSAGE.
RNB05 - Q14 (LIST)     - IF &QRNB = 1 THEN DO THE FOLLOWING:
                           (1) REMOVE THE PART OF UF005 THAT ALLOWS L TO
                               PROCESS DSID'S < 101 AND THAT ALLOWS AUTH
                               USERS TO LIST ANY JOB.  THIS REQUIRES THE
                               XD COMMAND TO BE USED TO LIST STRANGE
                               THINGS.
                           (2) ALLOW TSO USERS TO ACCESS ANY JOB THAT
                               STARTS WITH THEIR USERID OR THAT HAS A
                               NOTIFY FOR THEIR USERID. THIS WILL NOT
                               BE ALLOWED FOR USERID'S STARTING WITH
                               'PJS' DUE TO LOCAL RESTRICTIONS.
                           (3) ALLOW TSO USERS WHOSE USERID'S START WITH
                               'TEC' TO PROCESS ANY 'TEC...' JOB OR ANY
                               JOB WITH A NOTIFY FOR A TEC USER. ALSO
                               ALLOW THEM TO PROCESS OUTPUT FROM STARTED
                               TASKS.
RNB06 - Q16 (PARSE)    - ADDED THE FOLLOWING COMMAND ABBREVIATIONS FOR
                           CONSISTENCY WITH PREVIOUS VERSIONS:
                                 JC  FOR JCL
                                 JL  FOR JLOG
                                 JM  FOR JMSG
                                 SL  FOR SLOG
                                 FT  FOR FTIM
                                 DE  FOR DEL
                                 RE  FOR REQ
                         ALSO, IF &QRNB = 1, DELETE COMMANDS TSO, EXEC,
                           AND MODEL.
RNB07 - Q24 (ACTIVE)   - WHEN LISTING BATCH JOBS SAY THEY
                           ARE ON THE XEQ QUEUE INSTEAD OF THE INPUT
                           QUEUE TO BE MORE CONSISTENT WITH WHAT THE
                           OPERATORS USUALLY SEE.
RNB08 - Q26 (SYSOUT)   - IF &QRNB = 1, ALLOW USERS TO MANIPULATE JOBS
                           THAT START WITH THEIR USERID'S OR THAT HAVE
                           A NOTIFY FOR THEIR USERID, UNLESS THE USERID
                           STARTS WITH 'PJS'.
                         IF &QRNB = 1, ALLOW 'TEC' USERS TO MANIPULATE
                           ANY TEC JOB OR STARTED TASK OUTPUT.
RNB09 - Q26 (SYSOUT)   - IF &QRNB = 1, FOR A REQ OPERATION, IF A NEW
                           CLASS IS NOT GIVEN, USE CLASS C AS THE
                           DEFAULT NEW CLASS.
RNB10 - Q27 (PRINT)    - IF &QRNB = 1, USE C AS THE DEFAULT SYSOUT
                           CLASS.
RNB11 - Q4  (DDNAME)   - ALLOW DDNAME COMMAND TO BE
                           ISSUED AS   DDNAME JOBID S
                           WHERE THE S INDICATES THAT THE SPIN DATA
                           SETS SHOULD ALSO BE LISTED. THIS WAS ADDED
                           BECAUSE WE HAVE SOME LONG RUNNING BATCH JOBS
                           (IMS) THAT SPIN THINGS AND THE STANDARD Q
                           COMMAND DOESN'T SEARCH THE SPIN Q FOR BATCH
                           JOBS.
RNB12 - Q4  (DDNAME)   - IF &QSP = 1, DON'T FORMAT THE MESSAGE 'ALREADY
                           PRINTED', AS IT APPEARS THAT THE FLAG BIT
                           IN THE PDDB IS NOT USED ANY MORE, CAUSING
                           ALL SPIN DATA SETS TO APPEAR PRINTED, EVEN
                           WHEN THEY'RE NOT.
RNB13 - Q5  (DISPLAY)  - FIX SOME PROBLEMS WITH TCAM
                           AND THE PROCESSING OF THE TEST-REQUEST,
                           SYSTEM-REQUEST, AND THE PA2/PA3 KEYS.
RNB14 - Q5  (DISPLAY)  - BUG FIX FOR FULL-SCREEN PROCESSING. WITH THIS
                           FIX THE USER CAN ENTER A COMMAND IN EITHER
                           INPUT FIELD, NOT JUST THE BOTTOM ONE.
RNB15 - Q5  (DISPLAY)  - RESTORE THE PFK DEFINITIONS FOR
                           PF7/8 TO '- 27' AND '+ 27' AS ORIGINALLY
                           SUPPLIED BY THE ICBC MOD. WE DON'T HAVE
                           THE OTHER 3278 MODELS, AND SCROLLING IS
                           EASIER THIS WAY. WITH NERDC'S CHANGES TO
                           MAKE THE KEYS 'PB' AND 'PF' IT IS DIFFICULT
                           TO SCROLL UP OR DOWN A FEW LINES.
RNB16 - Q20 (SEARCH)   - PROCESS BOTH THE LOCAL AND REMOTE QUEUES FOR
                           JOBS AWAITING PRINT/PUNCH.
                         ALSO FIX A BUG IN UF020 THAT WAS CLEARING THE
                           JOEFLAG  WHEN JUST THE JOEJQE POINTER SHOULD
                           BE CLEARED.
RNB17 - Q7  (FORMAT)   - WHEN FORMATTING JOES:
                           (1) IF THE JOE IS BEING PROCESSED BY PSO,
                               INDICATE EXT-WTR FOR A DEVICE TYPE.
                           (2) USE $JOEBUSY FLAG TO INDICATE WHETHER JOB
                               IS REALLY PRINTING/PUNCHING. OTHERWISE,
                               AN INTERRUPTED JOB STILL SHOWS AS ON THE
                               PRINTER/PUNCH.
                           (3) FOR SP2, FIX A BUG IN GETTING TO THE
                               CHECKPOINT JOE AND IN COMPUTING THE LINES
                               LEFT TO PRINT/PUNCH.
                           (4) FOR SP2, IF THE JOE IS NOT ACTIVE, BUT
                               THE CHECKPOINT JOE IS VALID, SHOW THE
                               LINES LEFT, NOT THE ORIGINAL LINE COUNT.
RNB18 - Q7  (FORMAT)   - DISTINGUISH BETWEEN JOES WITH REMOTE ROUTING
                           AND THOSE WITH SPECIAL LOCAL ROUTING (DESTID
                           INITIALIZATION STATEMENT IN JES PARMS).
RNB19 - Q20 (SEARCH)   - FOR STATUS OR DJ COMMANDS IN THE SP2 VERSION,
                           ALSO SEARCH THE DUMP Q, THE CONVERSION Q,
                           AND THE OUTPUT Q. THIS ALLOWS THE USER TO
                           FIND HIS JOB IF IT'S AWAITING DUMP, AWAITING
                           CONVERSION, OR AWAITING OUTPUT PROCESSING.
      - Q7  (FORMAT)   - WHEN LISTING JQE'S, DON'T ASSUME INPUT QUEUE
                           BUT USE JQETYPE INSTEAD. ALSO, SPECIAL
                           HANDLING FOR AWAITING CONVERSION, AWAITING
                           DUMP, AND AWAITING OUTPUT.
RNB20 - Q7  (FORMAT)   - DISTINGUISH BETWEEN NORMAL HOLD, HELD VIA $HA,
                           AND DUPLICATE HOLD. ALSO, FOR JOES, IF THE
                           SELECT=NO FLAG IS ON, FLAG WITH S=N TO SHOW
                           WHY THE OUTPUT WON'T PRINT.
RNB21 - Q7  (FORMAT)   - FIX THE SETDEVIC ROUTINE FOR SP2 SO THE PROPER
                           DEVICE NAMES SHOW UP FOR JOBS ON PRINTERS,
                           ETC.
RNB22 - Q6  (FINDJOB)  - IF JOBNAME = *, AFTER READING THE JCT, ENSURE
                           THAT JQEJNAME = JCTJNAME AND THAT QPJOBID =
                           JCTJBKEY IN CASE THE JOB HAS PURGED AND THE
                           JCT HAS BEEN REUSED SINCE WE LAST READ THE
                           CHECKPOINT. THIS IS UNLIKELY, BUT SEEMS TO BE
                           POSSIBLE.
RNB23 - Q8  (HELP)     - MISCELLANEOUS CHANGES TO THE NERDC HELP INFO.
                           THE ORIGINAL NERDC VERSION IS MEMBER $Q8, AND
                           THE OLD RNB MEMBER IS #Q8.
RNB24 - Q23 (INITS)    - BUG FIX, AS SUGGESTED BY JACK SHUDEL
RNB25 - Q7  (FORMAT)   - ADD 'COUNT' OPTION TO THE HO COMMAND TO HELP
                           FIND WHICH JOBS ARE TIEING UP SPOOL SPACE.
                           WHEN THE COUNT OPTION IS USED, THE JCT FOR
                           EACH JQE WITH HELD OUTPUT WILL BE READ AND
                           THE JCT TOTAL LINE COUNT WILL BE DISPLAYED.
RNB26 - Q24 (ACTIVE)   - BUG FIX (SORT OF): THE DC COMMAND WAS SHOWING
                           A LOT OF STRANGE JOBS. THIS FIX MAKES IT MORE
                           REASONABLE, BUT IT'S STILL NOT QUITE RIGHT.
                           ALL OF THE STARTED TASKS, E.G. TCAM, DON'T
                           SHOW UP.

========================================================================
KNOWN PROBLEMS:
  (1) DC S DOESN'T SHOW ALL OF THE STARTED TASKS.
  (2) JOE PRIORITIES ARE (PROBABLY) INCORRECT, AS THE CALCULATIONS
      CHANGED FOR SP2 AND Q HASN'T BEEN UPDATED TO REFLECT THAT.
  (3) IT APPEARS THAT THE LINE COUNTS FOR JOBS ON A REMOTE PRINTER ARE
      MAINTAINED DIFFERENTLY THAT FOR JOBS ON A LOCAL PRINTER. THIS HAS
      NOT BEEN FULLY RESEARCHED YET, BUT IT SEEMS THAT THE LINE COUNT
      REPORTED BY Q FOR A JOB ON A REMOTE PRINTER IS APPROXIMATELY THE
      NUMBER OF LINES PRINTED, NOT THE NUMBER THAT REMAIN TO BE PRINTED.
  (4) ONLY 2 (POSSIBLY 3) CHARACTER REMOTE NUMBERS CAN BE USED.
  (5) NJE NODE NUMBERS ARE IGNORED.
  (6) THE NJE JOB/SYSOUT TRANSMITTERS AND RECEIVERS ARE IGNORED AS
      DEVICES AND AS QUEUES.
```

## $SBGDOC.txt
```
    CHANGES MADE TO QUEUE 1.3.6-2.1.5 BY SAM GOLOB OF NEWSWEEK.     SBG
                                                                    SBG
 ****  SEE NOTE AT BOTTOM  *****                                    SBG
                                                                    SBG
          MAILING ADDRESS:    SAM GOLOB                             SBG
                              P.O. BOX 906                          SBG
                              TALLMAN, NY 10982-0906                SBG
                                                                    SBG
                                                                    SBG
          EMAIL:  SBGOLOB@ATTGLOBAL.NET AND/OR                      SBG
                  SBGOLOB@AOL.COM                                   SBG
                                                                    SBG
                                                                    SBG
07 OCT 86  MODS FROM SAM GOLOB OF NEWSWEEK - LIVINGSTON N.J.        SBG
              ALLOW A DSID OF 0 TO BE A VALID DSID FOR A JOB.       SBG
           THE REASON FOR THIS MODIFICATION IS THAT RSCS VERSION    SBG
           2.1 GIVES DSID'S OF 0 FOR JOBS IT SENDS TO MVS FOR       SBG
           PRINTING.  MAKE -1, OR X'FFFF' THE INVALID DSID INSTEAD  SBG
           OF ZERO.  (THESE MODIFICATIONS ARE MARKED BY MY INITIALS SBG
           AND BY AN ISPF USERID OF "RSCS2.1").                     SBG
                                                                    SBG
   NOTE.  AFTER DISPLAYING A REAL DATASET, QUEUE WILL REMEMBER      SBG
            ITS JOB NUMBER AND DSID.  IF YOUR NEXT COMMAND AFTER    SBG
            DISPLAYING A REAL DATASET, DISPLAYS A NON-VALID         SBG
            DATASET (FOR INSTANCE--YOU DO A LIST, AND THEN A        SBG
            HELP COMMAND), A REPOSITION UP OR DOWN WILL GET YOU     SBG
            BACK TO YOUR FORMER REAL DATASET.  THIS IS SURPRISING   SBG
            BUT TRUE.                                               SBG
          IF YOU WANT TO NULLIFY THIS "MEMORY" OF THE LAST REAL     SBG
            DATASET YOU LOOKED AT, I HAVE INCLUDED A MEMBER         SBG
            CALLED NULLDSID.  JUST PUT ITS CODE AT THE BEGINNING    SBG
            OF ANY NON-REAL-DATASET COMMAND, AND THE "MEMORY"       SBG
            WILL VANISH FROM THAT COMMAND.                          SBG
```

## $UFDOC.txt
```

UF MODIFICATION DESCRIPTIONS


FOR FURTHER INFORMATION ON THESE MODIFICATIONS PLEASE CONTACT:

JACK SCHUDEL
NORTHEAST REGIONAL DATA CENTER
233 SSRB, UNIVERSITY OF FLORIDA
GAINESVILLE, FLORIDA  32611
(904) 392-4601
SHARE CODE - UF


THIS VERSION OF QUEUE WAS DERIVED FROM FILE 278 OF THE CBT MODS TAPE,
WHICH HAD BEEN OBTAINED FROM VERSION 18 OF THE SHARE JES2 PROJECT TAPE.
IT HAS BEEN RUN ON THE FOLLOWING VERSIONS OF JES2 (ASSUMING THAT THE
APPROPRIATE SYSPARM OPTIONS HAVE BEEN SET):
       JES2 4.1
       JES2 NJE 3.1
       MVS/SP-JES2 RELEASE 3

IN THE NERDC ENVIRONMENT, USE OF THE QUEUE COMMAND IS RESTRICTED TO
SYSTEMS PROGRAMMING PERSONNEL INVOLVED IN JES2 MAINTENANCE, AND THERE
HAVE BEEN SEVERAL COMMANDS ADDED FOR THIS USAGE.  AN ATTEMPT HAS BEEN
MADE TO REQUIRE THAT THE COMMANDS THAT ALLOW THE UNRESTRICTED ACCESS
TO SPOOL DATA AND CONTROL BLOCKS BE AVAILABLE TO ONLY AUTHORIZED USERS,
BUT THERE WERE ALSO CHANGES MADE TO ALLOW THOSE AUTHORIZED USERS FULL
ACCESS TO THE SYSTEM WITHOUT HAVING ANY NAMING CONVENTION RESTRICTIONS
IMPOSED UPON THEM.  IT IS THEREFORE NORMAL FOR AN AUTHORIZED USER
TO BE ABLE TO USE THE LIST COMMAND AGAINST ANY JOB IN THE SYSTEM
INSTEAD OF HAVING TO USE THE XD COMMAND.

THE COMMAND ONLY NEEDS TO RUN AUTHORIZED FOR THE FOLLOWING COMMANDS
CANCEL, REQUEUE, AND PURGE. IF YOU DO NOT MARK THE CODE AC=1, THESE
THREE COMMANDS WILL NOT FUNCTION.

INSTALLATION PROCEDURE FOR QUEUE:

     1. Q0 IS THE COMMON AREA.
        QCOMMON, QSTART, QSTOP, QTILT, AND $JQT ARE MACROS.
        OTHER MEMBERS NOT STARTING WITH $ OR # ARE RENT SOURCE MODULES
        (SEE MEMBER $NERJCL FOR A COMPLETE LIST).
        (USERS OF THE OLD QUEUE COMMAND WILL NOTICE THAT ALL OF THE
         Q1 - QNN MODULES HAVE BEEN RENAMED TO MAKE LIFE EASIER ON ME.)
        #HELP IS THE TSO HELP MEMBER.
        $NERJCL IS THE JCL TO ASSEMBLE AND LINK QUEUE.
        TABLE IS A SAMPLE SMP JOB TO AUTHORIZE THE QUEUE COMMAND.

     2. EDIT MEMBER QCOMMON CHANGING THE FOLLOWING PARAMETERS:

        UNIT=XXXX THE DEVICE TYPE FOR SYS1.HASPCKPT.
        VOLSER=YYYYYY THE VOLUME SERIAL FOR SYS1.HASPCKPT.
        SID1-SID7=ZZZZ THE SMF IDS FOR EACH CPU IN THE COMPLEX. THE
        IDS MUST BE IN THE SAME ORDER AS IN THE INITIALIZATION DECK.

        AT PRESENT THERE IS SUPPORT IN THE INITIALIZATION MODULE TO
        DYNAMICALLY ALLOCATE THE CHECKPOINT ON EITHER 3330, 3330-1,
        3350, OR 3380. IF YOU ARE FORTUNATE ENOUGH TO HAVE A DRUM OR
        SOMETHING ELSE YOU WILL HAVE TO MODIFY INIT TO ADD SUPPORT.

        EDIT THE MACRO QSTART TO INDICATE THE OPTIONS DESIRED,
        OR SPECIFY THEM AS SYSPARM INPUT TO THE ASSEMBLER.
        IT WILL BE NECESSARY TO LOOK AT THE MACRO FOR A DESCRIPTION
        OF THE OPTIONS AVAILABLE.

     3. EDIT MEMBER $NERJCL TO CHANGE THE JCL TO FIT YOUR STANDARDS.
        DO NOT ALTER THE ORDER OF THE ASSEMBLY SYSLIBS AS THERE IS A
        CONFLICT ON THE MACRO QSTART.  THE DBCSYMED PROGRAM THAT IS USED
        AFTER THE ASSEMBLIES IS A PART OF THE YALE DBC PROGRAM PRODUCT
        AVAILABLE FROM CSR.  IT EDITS THE GENERATED SYM CARDS IN THE
        OBJECT DECK TO REMOVE NULL ENTRIES AND MOST OF THE DUPLICATE
        ONES.  IF THE PROGRAM IS NOT AVAILABLE, SIMPLY DELETE THE STEP
        AND CHANGE THE ASSEMBLER SYSPUNCH REFERENCE.

        THE SUPPLIED JCL GENERATES A SINGLE LOAD MODULE WHICH IS NOT
        REENTRANT.  THIS IS IDEAL FOR TESTING, BUT MAY NOT BE DESIRED IN
        A PRODUCTION ENVIRONMENT.  TO GENERATE A REENTRANT VERSION OF
        THE COMMAND, LINK ALL MODULES EXCEPT Q0 AS A SINGLE PROGRAM
        NAMED QUEUE (ALIAS Q) INTO SYS1.LPALIB.  IT WILL NEED AN
        AUTHORIZATION CODE OF 1 IF YOU DESIRE TO USE THE CANCEL,
        REQUEUE, AND PURGE COMMANDS.  THE LINKEDIT OF MODULE QUEUE WILL
        GENERATE AN UNRESOLVED EXTERNAL REFERENCE FOR MODULE QUEUECMN,
        WHICH IS NORMAL AND SHOULD BE IGNORED.  MODULE Q0 SHOULD THEN BE
        ASSEMBLED AND LINKED INTO SYS1.LINKLIB OR SYS1.CMDLIB WITH A
        NAME OF QUEUECMN.  IF YOU WANT TO CHANGE THE NAME OF QUEUECMN,
        THE ONLY REFERENCE TO IT IS IN MEMBER INIT WHERE THE LINK IS
        ISSUED.

     4. IF THE CANCEL, REQUEUE, AND PURGE COMMANDS ARE DESIRED, ADD
        QUEUE (ALIAS Q) TO THE IKJEFTE2 MODULE WHICH IS THE TSO LIST
        OF AUTHORIZED COMMANDS. A SAMPLE SMP JOB IS PROVIDED IN THE
        MEMBER TABLE. QUEUE CAN BE RUN UNDER SPF BUT THE SUBCOMMANDS
        USING THE SUBSYSTEM INTERFACE (CANCEL, REQUEUE, AND DELETE)
        WILL BE INOPERABLE, ALL OTHER COMMANDS WILL FUNCTION NORMALLY.
        IF YOU DON'T MIND THE INTEGRITY PROBLEM YOU CAN ADD CODE TO
        QUEUE TO USE A SPECIAL SVC TO GET INTO SUPERVISOR STATE AND
        HAVE FULL FACILITY UNDER SPF.

USERS THAT DO NOT HAVE THE UICC JTIP PACKAGE INSTALLED WILL NEED TO
EITHER CHANGE THE QSTART MACRO OR SPECIFY NOJTIP IN THE ASSEMBLER
SYSPARM OPTIONS.

USERS THAT DO NOT HAVE THE YALE DBC PACKAGE INSTALLED SHOULD
EITHER CHANGE THE QSTART MACRO OR SPECIFY NODBC IN THE ASSEMBLER
SYSPARM OPTIONS.  IF DBC IS SPECIFIED BUT THE PACKAGE DOES NOT
EXIST, ALL THAT WILL HAPPEN IS THAT A MESSAGE WILL FLASH ON THE
USER'S TERMINAL INDICATING THAT THE LOAD FOR MODULE DBC FAILED.
THIS MESSAGE CAN BE IGNORED.

SOME OF THE CODE MAY BE DEPENDENT ON ASSEMBLER H, BUT ALL THAT SHOULD
BE NEEDED IS TO MOVE SOME OF THE DSECTS AROUND TO GET THEM IN THE
PROPER ORDER FOR THE OTHER ASSEMBLERS.

FOR FURTHER INFORMATION ON THE SUPPORT FOR MVS/SP-JES2 RELEASE 2 AND
ABOVE, SEE MEMBER $SP.

TO MAKE IT EASIER TO ENTER CERTAIN COMMANDS, COMMAND NAMES MAY NOW
BE UP TO FOUR CHARACTERS.

MEMBER $LOG IS A CHRONOLOGICAL LIST OF THE CHANGES THAT HAVE BEEN MADE
TO THIS PROGRAM, AND SHOULD BE CONSULTED BY USERS WHO HAVE A PREVIOUS
VERSION AND WANT TO KNOW WHAT HAS BEEN CHANGED.

FOLLOWING IS A LIST OF THE INDIVIDUAL MODIFICATIONS:

UF001  ALLOW QUEUE COMMAND TO ASSEMBLE USING NJE3.1 SOURCE CODE.
       A FEW EQUATES AND ADDITIONAL DSECTS WERE INCLUDED, WHICH SHOULD
       BE OK FOR NON-NJE SOURCE AS WELL.

UF002  ALLOW QCOMMON TO BE LINKED IN FOR TESTING.
       WE RUN WITH SEVERAL DIFFERENT SPOOL PACK FORMATS DURING TEST,
       AND IT IS CONVENIENT TO HAVE MULTIPLE VERSIONS OF QUEUE TO
       SUPPORT THESE DIFFERENT TEST VERSIONS.
       IT IS ALSO MUCH SIMPLER TO RUN UNDER TSO TEST.

UF003  SUPPORT FOR 3278 MODELS 2, 3, 4, AND 5.
       WE HAVE A WIDE ASSORTMENT OF TERMINALS IN-HOUSE, SO QUEUE WAS
       MODIFIED TO SUPPORT ALL TERMINAL TYPES AS BASIC MODEL 2, AND
       TO ALLOW THE USER TO SWITCH TO THE LARGER SCREEN FORMAT AT ANY
       TIME DURING HIS SESSION.
       THIS CODE IS CURRENTLY RUNNING UNDER ACF/VTAM REL 2, BUT WAS
       DEVELOPED UNDER ACF/VTAM REL 1, AND HAS ALSO RUN WITH TCAM AT
       THE 8011 LEVEL.

UF004  ADD A TITLE CARD FOR Q0 (QCOMMON).

UF005  DO NOT CHECK FOR JOBNAME MATCHING TSO LOGON ID IF QXAUTH=1.
       ALSO ALLOW READING DSID'S LESS THAN 101 IF QXAUTH=1.
       DSID'S LESS THAN 101 ARE SOMETIMES USEFUL TO LOOK AT;  THE
       INTERNAL TEXT FILE MAKES IT EASIER TO LOCATE THE PROPER DSID
       IN A SYSGEN WHERE ALL STEPNAMES ARE "ASM", AND IN A VM NETWORK
       ENVIRONMENT IT IS COMMON TO HAVE OUTPUT DSID'S OF 1.

UF006  ONLY READ THE CHECKPOINT IF THE INFORMATION IS NEEDED.
       THE READ OF THE CHECKPOINT IS REMOVED FROM THE MAIN EXECUTION
       LOOP, SINCE IT IS REALLY SILLY TO READ A LARGE CHECKPOINT DATASET
       WHEN THE USER COMMAND IS TO JUST REPOSTITION WITHIN THE CURRENT
       FILE.

UF007  CHANGE COMMANDS "DD *" AND "L * DSID" TO USE THE LAST JOBNAME
       IF A "*" IS SPECIFIED.  THIS MAKES IT EASIER TO TYPE, AND CODE
       IS ADDED TO SKIP THE CHECKPOINT READ FOR PERFORMANCE REASONS.
       IT IS STRONGLY RECOMMENDED THAT THE "*" BE USED INSTEAD OF THE
       JOB NAME/NUMBER SINCE THE RESPONCE TIME IS SO MUCH BETTER.

UF008  HAVE THE FINDPDDB ROUTINE START AT THE FIRST IOT IF PDDB IS NOT
       FOUND.  A MIXTURE OF SPIN AND REGULAR PDDB'S USED TO CAUSE
       THE ROUTINE TO SCAN TO THE END OF THE IOT'S AND STAY THERE WHILE
       TRYING TO LOCATE THE FIRST REGULAR PDDB AFTER A SPUN ONE.

UF009  ADD SYNAD ROUTINE AND ADDITIONAL CHECKING TO READSPC ROUTINE SO
       THAT THE SYSTEM WILL NOT FAIL DURING XB PROCESSING.

UF010  IF USER HAS TSO OPERATOR AUTHORITY, SET FLAG BIT IN QFLAG1,
       AND FORCE QXAUTH ON.

UF011  ADD MODULE HEXDUMP (Q28) WHICH WILL GENERATE AN ABEND FORMAT
       DUMP OF THE DATA PASSED TO IT.

UF012  CHANGE HEXBLK (Q9) TO USE HEXDUMP FOR FORMATTING THE READ
       BUFFER.

UF013  CHANGE HEXBLK (Q9) TO ALLOW ADDITIONAL INPUT PARAMETERS FOR
       DUMPING CURRENT BLOCK, AND OFFSETS INTO THE REQUESTED BLOCK.
       IF THE BLOCK ADDRESS PARAMETER IS "+", THE BUFFER CHAINED FROM
       THE CURRENT BUFFER WILL BE DUMPED.

UF014  CHANGE PARSE (Q16) TO USE 4 CHARACTER COMMAND NAMES, AND
       CHANGE LOGIC FOR DETERMINING IF A COMMAND IN PRIVILEGED.

UF015  ADD MODULE CJQE (Q29) TO DUMP JQE IN HEX.

UF016  ADD MODULE CJCT (Q30) TO DUMP JCT IN HEX WITH OPTIONAL
       OFFSET SPECIFIED.

UF017  ADD MODULE CTSO (Q31) TO ALLOW ANY TSO COMMAND TO BE ISSUED
       WHILE IN QUEUE.

UF018  CHANGE DEFAULT STARTUP COMMAND TO "HELP" SO GET STARTED FASTER.

UF019  ALLOW SYSPARM TO CHANGE &QXXX DEFAULTS.

UF020  SUPPORT FOR SP2 LEVEL OF JES2.
       NOTE: THERE ARE PROBABLY SOME BUGS IN THE DISPLAY COMMANDS AT
             THIS LEVEL.  THEY ARE BEING FIXED AS THEY ARE DISCOVERED,
             BUT SINCE THE NERDC DOES NOT NORMALLY USE THESE COMMANDS,
             IT MAY TAKE SOME TIME TO DISCOVER THE ERRORS.

UF021  SUPPORT FOR SP2 PTF UZ52546 (8110 LEVEL SET).

UF022  ADD MODULE CHCT (Q32) TO DUMP HCT CHECKPOINTED AREA.

UF023  ADD SYMDEL/SYMNODEL STATEMENTS AROUND DSECTS TO REDUCE
       NUMBER OF SYM ENTRIES IN FINAL LOAD MODULE.
       (THE DBCSYMED PROGRAM READS IN THE GENERATED OBJECT
       DECKS AND REMOVES SYM ENTRIES THAT APPEAR BETWEEN
       SYMDEL/SYMNODEL DSECT DEFINITIONS.  THIS CAN CUT THE
       SIZE OF THE FINAL LOAD MODULE BY MORE THAN HALF.)

UF024  ADD DIE COMMAND TO FORCE AN ABEND SO CAN GET BACK INTO THE
       DEBUGGING ENVIRONMENT, AND ESTABLISH ESTAE DURING INIT.

UF025  ADD PDDB COMMAND TO LIST PDDB'S FOR A JOB.  THIS IS USEFUL WHEN
       THE DD COMMAND FAILS FOR SUCH THINGS AS SYSOUT RECEIVED FROM
       OTHER NODES AS WELL AS DURING DEBUGGING OF MISC PROBLEMS.
       IF &QJTIP IS ON, THE PROC, STEP, AND DDNAMES WILL BE FORMATTED.

UF026  ADD JOE COMMAND TO DUMP JOES FOR A JOB.

UF027  FIX XI COMMAND TO PROPERLY LIST ALL INITIATOR CLASSES.

UF028  CHANGE SAVE COMMAND TO ALLOW QPARM3 TO SPECIFY THE VOLSER
       THAT THE DATASET IS TO BE ALLOCATED TO.
       (QPARM2 IS USED TO SPECIFY THE DATASET TYPE.  IT WASN'T
       DOCUMENTED, EITHER.)
       NOW THE COMMAND IS:
         SAVE DSN <DSTYPE> <VOLSER>

UF029  CHANGE Q7 FORMAT TO FIX ERROR IN TESTING FOR JOB ACTIVE ON A
       PRINTER.

UF030  ADD JOB HISTORY COMMAND (Q35).
       THE MODEL FOR THIS COMMAND WAS PROVIDED BY KEN TRUE OF INTEL.

UF031  CHANGE TRANSLATE IN THE DISPLAY (Q5) MODULE TO CHANGE X'FF'
       TO A BLANK.  THIS IS REQUIRED FOR REMOTE 3278'S.

UF032  ADD &QNERDC GLOBAL TO ALLOW FOR LOCAL DEPENDENCIES.
       SO FAR ONLY Q35 JOB HISTORY USES THIS FLAG.

UF033  CHANGE Q8 HELP TO PRINT BLANK LINES TO FORCE THE PLUS SIGN TO
       BE GENERATED AT THE BOTTOM OF EACH PAGE TO INDICATE TO THE USER
       THAT MORE DATA FOLLOWS.  THIS CODE FROM KEN TRUE AT INTEL.

UF034  CHANGE Q6 FINDJOB TO GENERATE ERROR MESSAGE IF A "*" WAS USED
       AS THE JOBID, BUT THE JQE FIELD HAS NOT YET BEEN INITIALIZED.
       THIS IS A PROBLEM FOR USERS WHO DO A STATUS COMMAND, SEE ONLY
       ONE JOB LISTED, AND THEN THINK THAT THEY CAN USE THE "*" TO
       DISPLAY THAT JOB.

UF035  CHANGE Q6 FINDJOB SO THAT IF THE COMMAND WAS SYSLOG THEN
       IF QPARM1 IS NULL OR "SYSLOG" THEN LOCATE THE SYSLOG
          FOR THE ACTIVE SYSTEM.
       IF QPARM1 IS NOT NUMERIC, AND NOT "SYSLOG" THEN IT IS ASSUMED
          TO BE THE SMFID OF THE SYSTEM WHOSE LOG IS DESIRED.
          FOR THIS TO WORK IT IS NECESSARY FOR THE SYSTEM ID'S
          TO BE PROPERLY DEFINED IN QSTART.

UF036  ADD Q36 (SPIN) COMMAND PROCESSOR.
       A NEW COMMAND 'SPIN' WILL CAUSE A COPY OF THE CURRENT DATASET
          TO BE SPUN TO SYSOUT.
       AT THIS TIME, THERE ARE NO OPTIONS FOR THE COMMAND, BUT IT
          WOULD BE NICE TO ADD OPTIONS FOR DEST, SYSOUT CLASS, FORMS,
          AND RANGE OF LINE NUMBERS.
       THIS REQUIRED CHANGES TO ALLOCATE AND QSTART, AS WELL.

UF037  CHANGE Q10 TO ADD SUPPORT FOR 3380.

UF038  ADD TGPS COMMAND TO LIST THE TOP 20 USERS OF SPOOL SPACE.
       THIS IS A VERY USEFUL COMMAND TO USE WHEN YOUR SPOOL VOLUMES
       ARE NEARLY FULL AND YOU WOULD REALLY LIKE TO KNOW WHO HAS ALL
       OF THE SPACE.  OUR EXPERIENCE HAS SHOWN THAT WHEN THE SPOOLS
       GET FULL, THE TOP 20 JOBS (OUT OF OVER 1000) WILL HAVE ABOUT
       30% OF THE TRACK GROUPS.  THIS COMMAND ACTUALLY COUNTS THE TRACK
       GROUPS ASSIGNED TO EACH JOB, BY READING ALL OF THE ALLOCATION
       IOT'S.  BY DOING IT THIS WAY YOU GET THE ACTUAL SPACE USED, AND
       DO NOT GET THROWN OFF BY JOBS THAT WRITE ONE LINE TO EACH OF
       THOUSANDS OF SPUN SYSOUTS.
       *** NOTE ***:  THIS COMMAND DOES AN INCREADIBLE AMOUNT OF I/O AND
       TAKES A LONG TIME TO COMPLETE.  IN OUR ENVIRONMENT, RUNNING ON A
       TEST CPU WHICH FREQUENTLY GETS LOCKED OUT FROM THE SHARED SPOOLS
       BY THE FASTER PRODUCTION MACHINES, IT CAN TAKE AS LONG AS FIVE
       MINUTES FOR THE RESPONCE TO COME BACK, BUT SOMETIMES IT IS THE
       ONLY WAY.
       *** NOTE ***:  THE PERCENT COLUMN INDICATES THE PERCENT OF TRACK
       GROUPS USED OUT OF THE DEFINED NUMBER OF TRACK GROUPS FOR THE
       SYSTEM.  IF YOU HAVE ALLOWED FOR EXTRA SPOOLS, THE NUMBERS WILL
       DISPLAYED WILL BE LOWER THAN ACTUAL.

UF039  CHANGE CHECKPOINT READ TO MULTIPLE DECB'S BASED ON NCP.
       THE IDEA FOR THIS CODE CAME FROM THE UCLA/UOC VERSION OF THE
       QUEUE COMMAND.

UF040  ALLOW +/-NNN TO BE SPECIFIED ON THE LIST * COMMAND.

UF041  CHANGE TSO COMMAND PROCESSOR TO PROPERLY CLEAR SCREEN FOR TCAM.

UF042  ALLOW QCOMMON PARAMETERS TO BE SPECIFIED IN QSTART.
       THIS WILL CAUSE ALL OF THE COMMONLY CHANGED OPTIONS TO BE
       SPECIFIED IN ONLY ONE PLACE.

UF043  MOVE PFK DEFINITIONS TO QCOMMON, AND SET VIA QSTART.
       BY MOVING THE DEFINITIONS TO QCOMMON, IT WILL BE POSSIBLE
       FOR THE MODEL COMMAND TO SET THE PROPER VALUES FOR PFK 7/8,
       THE SCROLL COMMANDS, FOR THE DISPLAY SIZE.

UF044  CHANGE READSPC TO DO FURTHER VALIDITY CHECKING ON THE VALUE
       OF MTTR THAT IS PASSED TO IT.  THIS SHOULD ELIMINATE OCCASIONAL
       S0C4 AND S0C1 ABENDS FROM OCCURRING.

UF046  SUPPORT FOR JES2 AT THE SP 1.3.3 LEVEL (HJE2329).
       THIS SUPPORT IS ENABLED BY SPECIFYING SYSPARM(SP133), OR
       CHANGING THE QSTART MACRO TO DEFAULT &QSP133 TO 1.

UF047  ADD WRITER NAME TO JOE DISPLAY IN FORMAT ROUTINE.

UF048  SUPPORT FOR SP 1.3.4.  (ADD $DRAINED EQUATE FOR HCT EXPANSION).

UF049  FIX TO CKPT TO RESOLVE OCCASIONAL ABEND S0C4.
       CODE IN INIT ASSUMES THAT THE HEADER RECORD IN THE CHECKPOINT
       DATASET THAT INCLUDES THE HCT SAVEAREA WILL BE AT LEAST 4096
       BYTES LONG, AND THE READ FOR THAT AREA IN "CKPT" HAS A LENGTH
       OF 4096 CODED IN THE DECB.  CODE IN "CKPT" BUMPS THE I/O AREA
       POINTER BY THE LENGTH READ FROM THE DECB, CAUSING PROBLEMS
       IF THE HEADER RECORD IS LESS THAT 4K BYTES LONG.
       CODE IS CHANGED IN "CKPT" TO BUMP THE POINTER BY 4K.

```

## $WGHDOC.txt
```
                          William G. Hecox
                          NASA/GSFC
                          Code 931, Bldg. 28 Rm S224
                          Greenbelt, MD. 20771
                          (301) 286-3993
                          Z8WGH@GIBBS.BITNET
                          Z8WGH@GIBBS.GSFC.NASA.GOV

20 AUG 86  WGH  - INSTALLED AT NASA GODDARD NSESCC INCLUDED LOCAL MODS.

                  INCLUDE RECFM AND LRECL IN PDDB DISPLAY
                          CPDDB
                  TTY SUPPORT  (LINE TERMINALS)
                          QUEUE, DISPLAY
                  EASY SEARCH: ALLOW BLANK OR = AS WELL AS *
                          FINDJOB
                  FIX EXIT CLEAR MSG FOR LARGE SCREENS
                          QUEUE
                  PUT IN TCAM/VTAM TEST IN CTSO SO WILL LOOK SAME
                          QUEUE, CTSO
                  INCREASE BLKSIZE TO 6160 ON SAVE COMMAND
                          SAVE
                  FIX TO PICK UP TWO BYTES FOR RMT/LCL FIELD
                          FORMAT
                  ALLOW ALL USERS TO ISSUE TSO COMMANDS
                          AUTH
                  MODIFIED SEARCH AND FORMAT TO INCLUDE ALL QUEUES
                   AND DISPLAY FIELDS ASSOCIATED WITH NJE
                          SEARCH, FORMAT, $JQT
                  MODIFIED DDNAMES HASPCKPT AND HASPACE1 TO
                   HASPCKPQ AND HASPACQ1 RESPECTIVELY
                   TO ALLOW SDSF AND QUEUE TO BE EXECUTING
                   SIMULTANEOUSLY UNDER ISPF
                          INIT, QCOMMON

           WGH  - ADDITIONAL ENHANCEMENTS (AFTER AUG 86)

                  ADDED #LINES PARM TO SAVE AND SPIN COMMAND
                          SAVE, SPIN
                  ADDED DEST AND USRID PARM TO SPIN COMMAND
                          SPIN
                  EASY QUEUE: ALLOW (LIST JOB DSID) ENTER DSID ONLY
                          LIST
                  PROCESS CLIST SUBCOMMANDS
                          INIT, DISPLAY
                  ADDED FOUR COMMANDS TO SUPPORT CLIST SUB-COMMANDS
                          STACK, TERMINAL, QUIET, TALK
                  ENHANCED HCT COMMAND TO REQUEST SPECIFIC BLOCKS
                  BY NAME (JQT, JOT, ETC) + OFFSET
                          CHCT
                  MODIFIED INIT TO PARSE INITIAL COMMAND
                  QUEUE VOL(CKPT) UNIT(33XX) PRE(SYSX) 1STCMD P1 - P4
                          INIT
                  MODIFIED DC TO DISPLAY CORRECT STEP AND PROCSTEP NAMES
                          INIT
                  RETRIEVE SMFID FIELDS FROM CHECKPOINT DAS RECORDS
                          INIT
                  NEW SUBCOMMAND -  PFX LEVEL  - CHANGES DEFAULT USERID
                      FOR STATUS COMMAND

   MAR 91  WGH  - MODIFIED VERSION XA 2.2 RECEIVED FROM J. SCHUDEL
                  WITH ABOVE MODS.

   AUG 92  WGH  - MODIFIED TO RUN WITH JES2 4.2  .
                          MINOR CHANGES TO ABOUT 20 MODULES
                          MOSTLY CONTROL BLOCK CHANGES.
                   SEARCH - CHANGED TO CHECK 3 OUTPUT QUEUES
                          PER CLASS AND CHECK NEW HELD OUTPUT JOE
                          QUEUE.
                   NOTE CHANGE IN FORMAT OF INITIAL COMMAND.

            --    QUEUE VOL(CKPT) UNIT(33XX) PRE(SYSX) 1STCMD P1 - P4 --

```

