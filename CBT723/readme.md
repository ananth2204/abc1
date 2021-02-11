```
//***FILE 723 is from Jim Moore, and contains some application      *   FILE 723
//*           code to show how much storage is available to your    *   FILE 723
//*           session.  CLCCSTOR and SHOWMEM provide this service   *   FILE 723
//*           from an ISPF environment.  SHOWSTOR provides a        *   FILE 723
//*           similar service for an IDMS/DC environment.           *   FILE 723
//*                                                                 *   FILE 723
//*           email:  JB Moore<conlogco@comcast.net>                *   FILE 723
//*                                                                 *   FILE 723
//*     This is a small bit of ISPF code to show 24/31 bit          *   FILE 723
//*     memory limits, usage, and how much is still available.      *   FILE 723
//*     It consists of two small COBOL programs and one panel.      *   FILE 723
//*     Compile and link the COBOL into some load library           *   FILE 723
//*     accessible to ISPF (ISPLLIB, STEPLIB or TSOLIB tasklib)     *   FILE 723
//*     and slap the panel into some ISPPLIB as member name         *   FILE 723
//*     SHOWMEMP.                                                   *   FILE 723
//*                                                                 *   FILE 723
//*     You can get the same thing (an TONS of other stuff) by      *   FILE 723
//*     using ISPVCALL STATUS from Option 6 (TSO) of ISPF.  I       *   FILE 723
//*     wrote it more to demonstrate how to put an ISPF             *   FILE 723
//*     "wrapper" around generic code (callable from anywhere).     *   FILE 723
//*     This is why one of the programs is named CLCCSTOR (the      *   FILE 723
//*     "generic" subroutine) and the other one has as its          *   FILE 723
//*     name, the command name:  SHOWMEM.                           *   FILE 723
//*                                                                 *   FILE 723
//*     Invoke as: Command ===> TSO SHOWMEM                         *   FILE 723
//*                                                                 *   FILE 723
//*     The panel contents is renewable when you press ENTER.       *   FILE 723
//*                                                                 *   FILE 723

```
