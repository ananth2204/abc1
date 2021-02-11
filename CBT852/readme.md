```
//***FILE 852 is from Paul Edwards and contains the GCC C-Language  *   FILE 852
//*           compiler and library, ported to MVS, z/OS, etc.       *   FILE 852
//*           This release is GCC 3.2.3 MVS 9.0                     *   FILE 852
//*           The GCC compilers for MVS can be found at:            *   FILE 852
//*                                                                 *   FILE 852
//*           http://gccmvs.sourceforge.net    and see also:        *   FILE 852
//*                                                                 *   FILE 852
//*           http://pdos.sourceforge.net                           *   FILE 852
//*                                                                 *   FILE 852
//*           email:  mutazilah@gmail.com                           *   FILE 852
//*                                                                 *   FILE 852
//*        Please note that I am no longer using GCC 3.4.6          *   FILE 852
//*        because it has too many bugs in it that I can't fix.     *   FILE 852
//*                                                                 *   FILE 852
//*        This latest version is really good technically.          *   FILE 852
//*        I can produce 31/ANY load modules that still             *   FILE 852
//*        work on MVS 3.8J and MVS/380 in 31-bit.                  *   FILE 852
//*        It's also AM32 clean.                                    *   FILE 852
//*                                                                 *   FILE 852
//*        Welcome to GCCMVS (GCC for MVS, CMS and VSE)             *   FILE 852
//*        a freely available 31-bit mainframe compiler             *   FILE 852
//*        for C Language.                                          *   FILE 852
//*                                                                 *   FILE 852
//*     GCCMVS is a standalone compiler designed to run on MVS      *   FILE 852
//*     (from z/OS all the way back to MVS 3.8j, and probably       *   FILE 852
//*     beyond to PCP, but no-one has tested (or at least           *   FILE 852
//*     reported) back that far) or CMS (z/VM and predecessors)     *   FILE 852
//*     and VSE (z/VSE back to DOS/VS R34). It consists of two      *   FILE 852
//*     distinct parts. Firstly, the standard GCC 3.2.3             *   FILE 852
//*     compiler with some required code changes for MVS and        *   FILE 852
//*     CMS. Secondly, PDPCLIB, which is a C runtime library        *   FILE 852
//*     required for GCC to be able to run, and also for your       *   FILE 852
//*     own programs to be able to run. Both things are             *   FILE 852
//*     required, and both things are what is dubbed "GCCMVS".      *   FILE 852
//*     Note that the licence for the GCC part is GPL while         *   FILE 852
//*     PDPCLIB is public domain (explicit PD notice). Because      *   FILE 852
//*     PDPCLIB is pure public domain, it means that there are      *   FILE 852
//*     no licencing restrictions on executables you produce        *   FILE 852
//*     yourself. i.e. commercial use is fine, and you can even     *   FILE 852
//*     sell PDPCLIB (original or modified, including               *   FILE 852
//*     proprietary modifications, with or without source) if       *   FILE 852
//*     you find a market.                                          *   FILE 852
//*                                                                 *   FILE 852
//*     The source code and executables for GCCMVS can be found     *   FILE 852
//*     at sourceforge                                              *   FILE 852
//*     <http://sourceforge.net/projects/gccmvs>, in the            *   FILE 852
//*     "downloads" link.  There is also an old port of GCCMVS      *   FILE 852
//*     to MUSIC/SP which is available here                         *   FILE 852
//*     <http://webpages.mcgill.ca/staff/group3/dedwar1/web>.       *   FILE 852
//*     Unfortunately the author of the MUSIC/SP version (Dave      *   FILE 852
//*     Edwards) passed away, but the mainline source code does     *   FILE 852
//*     MUSIC/SP now too, but it lacks nice packaging.  The MVS     *   FILE 852
//*     version also works under PDOS/390.                          *   FILE 852
//*                                                                 *   FILE 852
//*     Porting the compiler to the mainframe opened up the         *   FILE 852
//*     floodgates to lots of C code being able to be ported.       *   FILE 852
//*     The downloads section contains some such applications.      *   FILE 852
//*     The most impressive one is probably the "diff3"             *   FILE 852
//*     utility. If you have never heard of a three-way diff,       *   FILE 852
//*     you will not regret learning what it can do for you.        *   FILE 852
//*                                                                 *   FILE 852

```
