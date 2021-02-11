```
//***FILE 885 is from Albert Cheng and contains an updated          *   FILE 885
//*           Disassembler program which handles the new Jump       *   FILE 885
//*           instructions, and so forth.  The new disassembler     *   FILE 885
//*           is called HDISASM to distinguish it from older        *   FILE 885
//*           programs of this type.                                *   FILE 885
//*                                                                 *   FILE 885
//*           email:  albertcpcheng@hotmail.com                     *   FILE 885
//*                                                                 *   FILE 885
//*     The difference between this version and File 217.           *   FILE 885
//*                                                                 *   FILE 885
//*     1. It supports RI and RIL instructions                      *   FILE 885
//*        AHI, LHI, CLI, Jx, BRAS                                  *   FILE 885
//*        AFI, LFI, CFI                                            *   FILE 885
//*                                                                 *   FILE 885
//*        Thankfully IBM has introduced the new assembler          *   FILE 885
//*        instructions to simplify assembler coding.  For          *   FILE 885
//*        example, if you use relative branch instructions,        *   FILE 885
//*        there is no need to specify the program base             *   FILE 885
//*        registers in the assembler program.                      *   FILE 885
//*                                                                 *   FILE 885
//*     2. It supports most RRE, RXE and RXY instructions.          *   FILE 885
//*                                                                 *   FILE 885
//*     3. Bigger SYMBOL table.                                     *   FILE 885
//*                                                                 *   FILE 885
//*     4. Uses linkage stack for save area, and macro SVLNK is     *   FILE 885
//*        no longer required.  Use RI instructions (i.e.           *   FILE 885
//*        change BE to JE, AH to AHI etc.) to elminate each        *   FILE 885
//*        program base register having a 4K restriction.  Only     *   FILE 885
//*        1 program register is now necessary to keep track        *   FILE 885
//*        the internal variable of HDISASM.  New routines can      *   FILE 885
//*        added into HDISASM without a major change to the         *   FILE 885
//*        logic of HDISASM.                                        *   FILE 885
//*                                                                 *   FILE 885
//*     5. Pre-assembler is also performed even with no USING       *   FILE 885
//*        statement, as relative jump instructions do not          *   FILE 885
//*        required a program base register.                        *   FILE 885
//*                                                                 *   FILE 885
//*     The difference between HDISASM with ASMDASM:                *   FILE 885
//*                                                                 *   FILE 885
//*     1. Conditional branch instructions use the extended         *   FILE 885
//*        mnemonics.                                               *   FILE 885
//*                                                                 *   FILE 885
//*     2. ULABL is extended from 8 charcters to 12 characters      *   FILE 885
//*                                                                 *   FILE 885

```
