
## $$DOC.txt
```
                    MVS SoftwareMVS Software

Source Code

Here you'll find a collection of useful programs I've written on IBM's
MVS operating system.

Macro Library  -  members are part of SRCLIB

My experience with the stack architecture of 8-bit
microprocessors---as well as the Concept 14 macros---inspired me
to write a macro library that simulates a stack architecture for
S/390. The macro library is assigned the acronym PSM, which
stands for Pseudo Stack Machine or Paul Scott's Macros depending
on my mood. The PSM macros used in the code exhibits are:

PENTER    --- Module entry linkage with optional stack construction
PEXIT     --- Module exit linkage with auto stack destruction
PCALL     --- Call external entry point reentrantly
PUSHREG   --- Push one or more registers onto stack
POPREG    --- Pop one or more registers from stack

Copyright -- 1988-1989, Paul A. Scott, All rights reserved. |
Comments (0)

JCL String Compare

PSU001 --- Sets the step condition code to the boolean result of
the string comparison specified in the PARM field. This allows
conditional execution of subsequent steps based on the comparison

Example:
//STEP0001 EXEC PGM=PSU001,PARM=('&DAY,EQ,FRI')
//*

Notes:
  Either string may be a sybolic parameter (very handy)
  Allowed conditionals are EQ, NE, GT, GE, LT, LE
  Both strings are treated as characters even if all numeric
  The shorter of two otherwise equal strings is the lesser
  The step return code is 0 if the condition is true, 1 if false

Copyright -- 1988-1989, Paul A. Scott, All rights reserved. |
Comments (0)

JCL Instream Data

PSU002 --- Writes one or more lines of text in the PARM field to
SYSOUT. The first character of the PARM field is the line
separator and is not included in the output.

Example:
//STEP0001 EXEC PGM=PSU002,
//            PARM=('\',                       RECORD SEPARATOR
//            ' C INDD=SYSUT1,OUTDD=SYSUT2\',  CARD #1
//            ' S M=(MEMBERA,MEMBERB) ')       CARD #2
//SYSOUT  DD  DSN=&&IEBCOPY,UNIT=VIO, ...
//*

Notes:
  Sybolic parameters are allowed
  The PARM field is limited to 100 characters
  If necessary, use multiple steps with SYSOUT DD DISP=MOD,...
  The step return code is always 0
  Any failure results in a system ABEND code

Copyright -- 1988-1989, Paul A. Scott, All rights reserved. |
Comments (0)

JCL Dataset Editor

PSU003 --- Copy SYSUT1 to SYSUT2 while replacing one string with
another. Specify one or more "old=new" strings in the PARM field,
delimited by a comma.  All occurences of old in SYSUT1 will be
replaced with new in SYSUT2 during the copy operation.

Example:
//STEP0001 EXEC PGM=PSU003,
//            PARM=('&&PREFIX=PROD.LOAN.SL',
//            '&&UNIT=SYSDA')
//SYSIN    DD  DUMMY,DCB=(RECFM=FB,LRECL=80,BLKSIZE=80)
//SYSUT1   DD  DSN=PROD.CONTROL.JCL(LOAN001),DISP=SHR
//SYSUT2   DD  DSN=PROD.CONTROL.JCL(LOAN001),DISP=SHR
//*

Notes:
  Symbolic parameters are allowed
  A string containing & must be specified as &&
  A search string begining with & obeys JCL symbolic replacement
  rules of concatenation
  The PARM field is limited to 100 characters
  SYSIN may be used to specify up to 500 replacement strings
  (source configurable)
  The PARM and SYSIN strings are combined, if present
  If SYSUT2 and SYSUT1 are identical, then records are updated in
  place

Copyright -- 1988-1989, Paul A. Scott, All rights reserved. |
Comments (0)

Calendar Generator
PSU004 --- Generate a calendar for the current (or specified) year.

Example:
//STEP0001 EXEC PGM=PSU004,PARM=('1989')
//SYSOUT    DD  SYSOUT=*
//*

Alternately, use a CLIST to generate a calendar in ISPF edit.

Notes:
  Specify a 4-digit year in the PARM field
  If the PARM is blank or invalid, the current year is substituted
  The calendar is written to DD name SYSOUT
  SYSOUT is forced to DCB=(RECFM=FBA,LREC=121,BLKSIZE=6171)
  The return code is always 0

Copyright -- 1988-1989, Paul A. Scott, All rights reserved. |
Comments (0)

Once you've had a chance to review the code above, you may want to grab the
Installation Job Stream that will install all of the programs, plus an
IVP and documentation. Change only the JOB statement and the parameters
on the first PROC statement. The Job Stream is set up to take care of
the rest.

Important: The installation requires MVS/ESA or above and Assembler H.
```

## $$MACDOC.txt
```
             MVS Software Documentation --- PSM Macro Library

                     MVS Software Documentation


Copyright -- 1988-2003, Paul A. Scott, All rights reserved.

PSM Macro Library

Quick Links:  PCALL   PENTER   PEXIT   POPREG   PUSHREG   ZIC   ZICM

PCALL --- Call External Entry Point
One of the advantages to using the PSM macros is the simplicity
they provide.  Although PCALL is a replacement for the standard
system CALL macro, and performs the same function, it is greatly
simplified.

PCALL does not require separate list and execute forms. It is
implicitly reentrant, building its parameter list dynamically on
the stack. You need only supply an entry point and any optional
parameters.  A prerequiste to using PCALL is a consistent use of
PENTER and PEXIT throughout your code. That is, there must be a
stack available when you invoke PCALL.

Syntax:

label    PCALL entrypoint[,(parm[[,parm]...])]

Parameters:

      label  Optional.  Code label to assign a location symbol to the
      first expanded instruction.

      entrypoint  Required.  Specify the name of an external symbol
      to which the program should transfer control..

      parm  Optional.  Specify one or more of: a constant, literal,
      equated symbol, or location symbol; essentially anything
      that the LA instruction can generate a base/displacement
      for. You may also specify a register if it is enclosed in
      parentheses.

      The entire list of parameters must be enclosed in parentheses.

Copyright -- 1988-2003, Paul A. Scott, All rights reserved.

PENTER --- Program Entry Linkage

There is probably no other macro solution more often reinvented
than program entry and exit code, and there's always a "good"
reason for doing so. This is no exception. In order to implement
a pseudo-stack machine, it was necessary to provide automatic
stack creation, destruction and management. PENTER is part of
this solution.

PENTER is used in four ways: (1) conventional program linkage;
(2) PSM program linkage with stack creation; (3) PSM program
linkage without stack creation; (4) "C" style program linkage.
The latter usage supports an unfinished C compiler and runtime
library project, and should be avoided. In most cases, you'll use
PSM linkage, although conventional linkage is available if
needed. Note that PSM linkage is fully compatible with
conventional linkage.

In addition to program linkage and stack allocation/management,
PENTER also provides automatic register equates, code
addressability, and allocation of local storage. This latter
feature means PENTER is reentrant (as are all PSM macros), and
assists the programmer in writing reentrant code.

When multiple PENTER/PEXIT pairs are used in a single source
module, there is no need to DROP register addressability between
them. PENTER will automatically DROP any previously generated
USING.

PENTER generates standard register equates. However, no equate is
generated for the register assigned to the stack pointer (global
symbol &SP) or the base pointer (global symbol &BP). This will
help to prevent inadvertantly destroying the stack. PENTER uses
the global symbol &REGS to both announce its equates and check
for equates from the IBM supplied YREGS macro. If it can be
determined that register equates have already been defined,
PENTER will issue a warning to avoid using the registers assigned
to &BP and &SP.

Syntax:

label    PENTER type[,BASE=12|reg|(reg,reg,...)]
                [,VARS=(addr,length)][,STACK=n]

Parameters:

      label  Required.  Code label to name the CSECT for this
      entry point. Do not code a CSECT statement; PENTER will
      automatically generates one for the label supplied.

      type  Optional.  May be blank or one of: MAIN, FUNC, CMAIN

             blank  Conventional program linkage. Storage is
            obtained for a save area, VARS local storage space
            (if requested), and a minimal stack to support the
            other PSM macros. The STACK parameter is not
            permitted.  Sub-programs of this program should not
            use type FUNC; they should use conventional program
            linkage.

             MAIN  PSM program linkage. Storage is obtained for a
            save area, VARS local storage, and a full stack. The
            STACK parameter must request enough stack to meet the
            needs of this program and all sub-programs of type
            FUNC. Use MAIN for programs directly invoked by the
            system, or by LINK and ATTACH.

             FUNC  PSM program linkage. This program will use the
            stack passed by the caller, and will pass the stack
            pointer to called programs. The program save area and
            any VARS local storage is carved off the stack. Use
            FUNC for sub-programs of MAIN and other FUNC
            routines.

             CMAIN  Not fully implemented. Do not use CMAIN.

      BASE=12|reg|(reg,...)  Optional.  By default, register 12 is
      used as the program base register. If more base registers
      are required, you can use BASE to provide more. However, if
      you do, you must specify all the base registers, including
      the first one. This is unlike VARS which always provides
      the first base register and cannot be overridden. For
      example:

      ... ,BASE=12

      ... ,BASE=(12,11)

      Note that when mulitple base registers are given, they must
      be separated with commas and the entire group of registers
      surrounded by parentheses.  If only one register is given,
      the parentheses are optional.

      Important: Never use a higher numbered register in your
      program than the highest numbered base register! This is
      because of an undocumented feature (a real feature, not a
      bug). The only exceptions are registers 14 and 15, which
      may be used safely. For example, if your highest base
      register is 5, then registers 6 through 13 are off limits
      within your program! It is therefore recommended to use
      register 12 as a base register, unless you are keenly aware
      of the circumstances.

      STACK=n  Optional.  Specify the number of 4K blocks of
      storage to allocate to the stack. This must include enough
      space for local stack operations (such as PUSHREG and
      POPREG), and all program linkage, local variables, and
      stack operations performed by called programs. Local
      variable storage for this program (from VARS) is then added
      to the total.

      Unfortunately, there is no easy way to determine the
      correct value, and no rule of thumb would suffice. However,
      stack sizes of 4K (STACK=1) to 8K (STACK=2) are typical
      unless large amounts of local storage are used, or a
      program is highly recursive.

      There is currently no stack overflow/underflow checking.

      VARS=(addr,length)  Optional.  Allocate space for local
      storage and provide addressability. The addr parameter
      should be a DSECT label, and length is the DSECT length
      (usually specified as a symbol created with a statement at
      the end of the DSECT such as "VARSLEN EQU *-label").

      Addressability is automatically established on the DSECT
      using global symbol &BP (the base pointer---defaults to
      register 13). This is usually sufficient to cover local
      storage. However, if additional base registers are
      required, they may be appended to the end of the parameter
      list separated by commas. You cannot override the first
      base register; it is always defined as &BP. For example:

        ... ,VARS=(VARDSECT,VARLEN,4)

      would generate "USING VARDSECT,&BP,4" to provide 8192 bytes
      of addressability. Note that there is a small amount of
      storage carved out of the total for save area and overhead,
      so it is possible that if you are very, very close to the
      limit, you might need to allocate a second base register..

      Do not specify a register assigned to the &BP or &SP global
      symbols. These are registers 13 and 3 by default. PENTER
      should admonish you if you try, but to avoid insult, please
      don't show it any disrespect.



Copyright -- 1988-2003, Paul A. Scott, All rights reserved.

PEXIT --- Program Exit Linkage

Unlike the Hotel California where you can never leave, when you
PENTER you must eventually PEXIT.

PEXIT undoes the effects of PENTER. It's a good idea to pack a
souvenir on your way out---in the form of a return code---but if
you don't, then one of zero value will be supplied for you.

PEXIT will unwind the stack and automatically free any storage
obtained by its corresponding PENTER.

Just before returning to the caller, PEXIT leaves behind a
breadcrumb by setting the rightmost bit in the return address
field of the caller's save area. This might be useful in the
extremely unlikely event your program dumps and you're
wondering---while examing the storage dump---if the program was
called at some time in the recent past.

Note that PEXIT is designed to be coded only once for each
PENTER. Do not code more than one PEXIT without an intervening
PENTER.

Syntax:

[label]  PEXIT [RC=(reg)|n]

Parameters:

      label  Optional.  Code label to assign a location symbol to
      the first expanded instruction.

      RC=(reg)|n  Optional.  To supply a return code in a
      register, specify the register within parentheses. For
      example:

             PEXIT RC=(15)  Exit using the return code in register 15.

            To specify a numeric return code, specify the number
            directly or code an equate symbol. For example:

             PEXIT RC=4  Exit with return code 4.

             PEXIT RC=ERROR4  Exit with the value of equate
             symbol ERROR4.

            There is no support for supplying a return code
            directly from a memory location. Instead, load the
            value into a register and invoke PEXIT with register
            notation.

            If a return code is not supplied, then RC=0 is
            automatically generated.


Copyright -- 1988-2003, Paul A. Scott, All rights reserved.

PUSHREG --- Push Registers Onto Stack

PUSHREG will push one or more registers, or range of registers,
onto the stack.

The stack pointer &SP is incremented when the operation is
complete.  Registers are pushed from left to right as coded on
the MACRO instruction.

The condition code in the PSW is preserved across PUSHREG.
However, it is recommended that you don't depend on the condition
code being static.

No registers other than &SP are changed.

Syntax:

[label]  PUSHREG reg|(reg,reg)[[,reg|(reg,reg)]...]

Parameters:

      label  Optional.  Code label to assign a location symbol to
      the first expanded instruction.

      reg  At least one required.  Code reg as a number from 0 to
      15, or one of the symbols R0 through R15.

      Code a range of registers by specifying two registers
      separated by a comma and enclosed in parentheses. If the
      first register in a range is higher than the second
      register, the range wraps through registers 15 and 0.

      The rules are best explained by example:

             PUSHREG R14  pushes register 14 onto the stack.
             PUSHREG R9,(R15,R1)  pushes registers 9, 15, 0, and
                   1 onto the stack.


Copyright -- 1988-2003, Paul A. Scott, All rights reserved.

POPREG --- Pop Registers From Stack

POPREG will pop one or more registers, or range of registers,
from the stack.

The stack pointer &SP is decremented when the operation is
complete.

Registers are popped from right to left as coded on the MACRO
instruction, exactly opposite the direction used by PUSHREG. This
allows you to code the same operands on both PUSHREG and POPREG.

Use great care when the POPREG parameter list does not exactly
match its corresponding PUSHREG. In particular, you cannot
successfully pop registers pushed earlier than the last unpopped
register. Although it is possible to have more than one POPREG
undo the effect of a single PUSHREG, this practice is strongly
discouraged.

The condition code in the PSW is not preserved across POPREG; it
was decided that speed was the more important goal.

No registers other than &SP and those being popped are changed.

Syntax:

[label]  POPREG reg|(reg,reg)[[,reg|(reg,reg)]...]

Parameters:

      label  Optional.  Code label to assign a location symbol to
      the first expanded instruction.

      reg  At least one required.  Code reg as a number from 0 to
      15, or one of the symbols R0 through R15.

      Code a range of registers by specifying two registers
      separated by a comma and enclosed in parentheses. If the
      first register in a range is higher than the second
      register, the range wraps through registers 15 and 0.

      The rules are best explained by example:

             POPREG R14  pops register 14 from the stack.
             POPREG R9,(R15,R1)  pops registers 1, 0, 15, and 9
                  from the stack.


Copyright -- 1988-2003, Paul A. Scott, All rights reserved.

ZIC --- Zero and Insert Character

It is quite common when using the IC instruction to first clear
the target register. ZIC is designed to do this automatically,
relieving the programmer of that responsibility.

At first it seems like a simple task to simply clear the target
register before issuing IC. However, it is possible (although
unlikely) that the target register is also a base or index
register used by IC. In that case, it is necessary to mask off
the unused bits in the target register after the IC instruction
is completed. Because the masking operation is slower, ZIC makes
every effort to clear the register before issuing IC.

If ZIC cannot determine that it is safe to clear the target
register first (faster), then it will mask off the unused bits
(slower) after the fact. The programmer can assist ZIC by using
base-index-displacement notation whenever possible, but this is
not required.

Syntax:

[label]  ZIC reg,addr

Parameters:

      label  Optional.  Code label to assign a location symbol to
      the first expanded instruction.

      reg  Required.  Code reg as a number from 0 to 15, or one
      of the symbols R0 through R15. Of course, you shouldn't use
      a register assigned to an active USING, or the base (&BP)
      or stack (&SP) registers.

      addr  Required.  A location sybmol referencing the address
      of the character to insert. Alternately, the
      base-index-displacement format may be used.

ZIC is coded in exactly the same manner as IC. There are no known
problems or side-effects.

Copyright -- 1988-2003, Paul A. Scott, All rights reserved.

ZICM --- Zero and Insert Characters Under Mask

It is quite common when using the ICM instruction to first clear
the target register. ZICM is designed to do this automatically,
relieving the programmer of that responsibility.

At first it seems like a simple task to simply clear the target
register before issuing ICM. However, it is possible (although
unlikely) that the target register is also a base register used
by ICM. In that case, it is necessary to mask off the unused bits
in the target register after the ICM instruction is completed.
Because the masking operation is slower, ZICM makes every effort
to clear the register before issuing ICM.

If ZICM cannot determine that it is safe to clear the target
register first (faster), then it will mask off the unused bits
(slower) after the fact. The programmer can assist ZICM by using
register notation whenever possible, but this is not required.

Syntax:

[label]  ZICM reg,mask,addr

Parameters:

      label  Optional.  Code label to assign a location symbol to
      the first expanded instruction.

      reg  Required.  Code reg as a number from 0 to 15, or one
      of the symbols R0 through R15. Of course, you shouldn't use
      a register assigned to an active USING, or the base (&BP)
      or stack (&SP) registers.

      mask  Required.  A value from 0 to 16 representing the byte
      or bytes in reg that will participate in the insert
      operation. Typically, you would use binary representation,
      such as B'1111' (all bytes participate).

      addr  Required.  A location sybmol referencing the address
      of the character(s) to insert. Alternately, the
      base-displacement format may be used.

ZICM can be coded in exactly the same manner as ICM. There are no
known problems or side-effects.

Copyright -- 1988-2003, Paul A. Scott, All rights reserved.
```

