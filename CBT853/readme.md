```
//***FILE 853 is from Paul Edwards and contains the GCC C-Language  *   FILE 853
//*           compiler and library, ported to MVS, z/OS, etc.       *   FILE 853
//*           This release is GCC 3.4.6 MVS 1.0.  The GCC compilers *   FILE 853
//*           for MVS can be found at:                              *   FILE 853
//*                                                                 *   FILE 853
//*           http://gccmvs.sourceforge.net    and see also:        *   FILE 853
//*                                                                 *   FILE 853
//*           http://pdos.sourceforge.net                           *   FILE 853
//*                                                                 *   FILE 853
//*           email:  mutazilah@gmail.com                           *   FILE 853
//*                                                                 *   FILE 853
//*         Welcome to GCCMVS (GCC for MVS, CMS and VSE)            *   FILE 853
//*         a freely available 31-bit mainframe compiler            *   FILE 853
//*         for C Language.                                         *   FILE 853
//*                                                                 *   FILE 853
//*     GCCMVS is a standalone compiler designed to run on MVS      *   FILE 853
//*     (from z/OS all the way back to MVS 3.8j, and probably       *   FILE 853
//*     beyond to PCP, but no-one has tested (or at least           *   FILE 853
//*     reported) back that far) or CMS (z/VM and predecessors)     *   FILE 853
//*     and VSE (z/VSE back to DOS/VS R34). It consists of two      *   FILE 853
//*     distinct parts. Firstly, the standard GCC 3.4.6             *   FILE 853
//*     compiler with some required code changes for MVS and        *   FILE 853
//*     CMS. Secondly, PDPCLIB, which is a C runtime library        *   FILE 853
//*     required for GCC to be able to run, and also for your       *   FILE 853
//*     own programs to be able to run. Both things are             *   FILE 853
//*     required, and both things are what is dubbed "GCCMVS".      *   FILE 853
//*     Note that the licence for the GCC part is GPL while         *   FILE 853
//*     PDPCLIB is public domain (explicit PD notice). Because      *   FILE 853
//*     PDPCLIB is pure public domain, it means that there are      *   FILE 853
//*     no licencing restrictions on executables you produce        *   FILE 853
//*     yourself. ie commercial use is fine, and you can even       *   FILE 853
//*     sell PDPCLIB (original or modified, including               *   FILE 853
//*     proprietary modifications, with or without source) if       *   FILE 853
//*     you find a market.                                          *   FILE 853
//*                                                                 *   FILE 853
//*     The source code and executables for GCCMVS can be found     *   FILE 853
//*     at sourceforge                                              *   FILE 853
//*     <http://sourceforge.net/projects/gccmvs>, in the            *   FILE 853
//*     "downloads" link. There is also an old port of GCCMVS       *   FILE 853
//*     to MUSIC/SP which is available here                         *   FILE 853
//*     <http://webpages.mcgill.ca/staff/group3/dedwar1/web>.       *   FILE 853
//*     Unfortunately the author of the MUSIC/SP version (Dave      *   FILE 853
//*     Edwards) passed away, but the mainline source code does     *   FILE 853
//*     MUSIC/SP now too, but it lacks nice packaging.  The MVS     *   FILE 853
//*     version also works under PDOS/390.                          *   FILE 853
//*                                                                 *   FILE 853
//*     Porting the compiler to the mainframe opened up the         *   FILE 853
//*     floodgates to lots of C code being able to be ported.       *   FILE 853
//*     The downloads section contains some such applications.      *   FILE 853
//*     The most impressive one is probably the "diff3"             *   FILE 853
//*     utility. If you have never heard of a three-way diff,       *   FILE 853
//*     you will not regret learning what it can do for you.        *   FILE 853
//*                                                                 *   FILE 853

```
