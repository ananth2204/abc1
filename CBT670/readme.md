```
//***FILE 670 is from Deru Sudibyo, and contains a REXX math        *   FILE 670
//*           function package, similar to math functions for       *   FILE 670
//*           PL/I.                                                 *   FILE 670
//*                                                                 *   FILE 670
//*           email:  "Deru Sudibyo" <deru.sudibyo@gmail.com>       *   FILE 670
//*                                                                 *   FILE 670
//*     Includes a fix to the FRAC function in the DRXMATH member.  *   FILE 670
//*                                                                 *   FILE 670
//*   A short description of this function package:                 *   FILE 670
//*                                                                 *   FILE 670
//*     This function package was originally DRXMATFN which is      *   FILE 670
//*     for VM/CMS.  No enhancement yet, except just to make it     *   FILE 670
//*     run on OS/390 or z/OS.  Hence, legacy HFP is still used     *   FILE 670
//*     which is low precision and accuracy, since the last         *   FILE 670
//*     touch was in 1993 on VM/ESA on ESA/370 machine.   Next      *   FILE 670
//*     plan is to convert it to BFP once I have enough time.       *   FILE 670
//*                                                                 *   FILE 670
//*     This package can be used as a supplement to your REXX       *   FILE 670
//*     to provide several math functions such as sin(), cos(),     *   FILE 670
//*     tan() etc.   Hence, your REXX will look like PL/1.          *   FILE 670
//*     Without such a package, REXX doesn't support any math       *   FILE 670
//*     functions.   However, it just for availability.   There     *   FILE 670
//*     is no guarantee for the performance, since all REXX         *   FILE 670
//*     variables are internally presented as text strings.         *   FILE 670
//*                                                                 *   FILE 670
//*     Member Names                                                *   FILE 670
//*     ============                                                *   FILE 670
//*       $LOADLIB : Load library in TSO XMIT format                *   FILE 670
//*       DRXFLOC  : Source code of package & package directory     *   FILE 670
//*       DRXMATH  : Source code of package only module             *   FILE 670
//*       @RXCSECT : Local macro                                    *   FILE 670
//*       @RXENTRY : Local macro                                    *   FILE 670
//*       @RXEXIT  : Local macro                                    *   FILE 670
//*       @RXFDIR  : Local macro                                    *   FILE 670
//*       DRXFUNC  : Local macro                                    *   FILE 670
//*       ASSEMBLE : Assembling & linkage editor procedure          *   FILE 670
//*       JDRXFLOC : Job to generate the package                    *   FILE 670
//*       JDRXTEST : Job for batch testing                          *   FILE 670
//*       TTEST0   : Rexx program for testing                       *   FILE 670
//*       TTEST1   : Rexx program for testing                       *   FILE 670
//*       TTEST2   : Rexx program for testing                       *   FILE 670
//*       TTEST3   : Rexx program for testing                       *   FILE 670
//*       TTEST5   : Rexx program for testing                       *   FILE 670
//*       TTEST6   : Rexx program for testing                       *   FILE 670
//*                                                                 *   FILE 670

```
