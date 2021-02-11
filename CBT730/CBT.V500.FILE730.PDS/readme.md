
## @FILE730.txt
```
//***FILE 730 is from Hal Merritt, and contains a generalized       *   FILE 730
//*           version of a sample IBM program which allows you to   *   FILE 730
//*           run COBOL programs in batch under a z/OS.e LPAR.      *   FILE 730
//*           A description of the program follows:                 *   FILE 730
//*                                                                 *   FILE 730
//*           email:  hal.merritt@att.net                           *   FILE 730
//*                                                                 *   FILE 730
//*      This routine or front end is the documented way to         *   FILE 730
//*       run most any COBOL program in batch under z/OS.e.         *   FILE 730
//*       There is no documented restriction as to version of       *   FILE 730
//*       complier, but the COBOL program must be linked with       *   FILE 730
//*       LE runtimes.                                              *   FILE 730
//*                                                                 *   FILE 730
//*      Orginal program from topic 6.3.5 of SC26-4818-05 IBM       *   FILE 730
//*      Language Environment for MVS & VM Programming Guide        *   FILE 730
//*      Release 5.                                                 *   FILE 730
//*                                                                 *   FILE 730
//*      There are two main modifications.  One, the return         *   FILE 730
//*      code from the called program is percolated instead         *   FILE 730
//*      of dropped.  Look for L R15,SUBRETC  near the label        *   FILE 730
//*      DONE.                                                      *   FILE 730
//*                                                                 *   FILE 730
//*      The second is to call a program named in the               *   FILE 730
//*      parm rather than from a hard coded entry. This             *   FILE 730
//*      code starts near label PARM2.                              *   FILE 730
//*                                                                 *   FILE 730
//*      What happens is the program name is extracted from         *   FILE 730
//*      the parm, then the parm pointers are adjusted so           *   FILE 730
//*      that the called program is unaware anything is             *   FILE 730
//*      unusual.  The program name is expected to be the           *   FILE 730
//*      first one to eight bytes delimited by a comma or           *   FILE 730
//*      blank.  The parm pointers are adjusted to the first        *   FILE 730
//*      position past the delimiter.                               *   FILE 730
//*                                                                 *   FILE 730
//*      Of course, the maximum parm length usable by the           *   FILE 730
//*      called program is reduced by the length of the             *   FILE 730
//*      module name plus one.  Other than that, the called         *   FILE 730
//*      program should not need any modifications.                 *   FILE 730
//*                                                                 *   FILE 730
//*      We call this routine PIPICALL, and stow it in a            *   FILE 730
//*      linklist library.  The JCL modifications are:              *   FILE 730
//*                                                                 *   FILE 730
//*         Before =>                                               *   FILE 730
//*      //MYSTEP   EXEC PGM=MYPROG,PARM=MYPARM                     *   FILE 730
//*                                                                 *   FILE 730
//*         After  =>                                               *   FILE 730
//*      //MYSTEP  EXEC PGM=PIPICALL,PARM='MYPROG,MYPARM'           *   FILE 730
//*                                                                 *   FILE 730
//*       Function :  CEEPIPI - Initialize the PIPI                 *   FILE 730
//*                             environment, call a PIPI HLL        *   FILE 730
//*                             program, and terminate the          *   FILE 730
//*                             environment.                        *   FILE 730
//*                                                                 *   FILE 730
//*     1.  Call CEEPIPI to initialize a subroutine environment     *   FILE 730
//*         under LE.                                               *   FILE 730
//*     2.  Call CEEPIPI to load and call a reentrant HLL           *   FILE 730
//*         subroutine.                                             *   FILE 730
//*     3.  Call CEEPIPI to terminate the LE PIPI environment.      *   FILE 730
//*                                                                 *   FILE 730
//*     Note:  PIPICALL is not reentrant.                           *   FILE 730
//*                                                                 *   FILE 730
```

