```
//***FILE 860 is from Gerhard Postpischil and contains quite a      *   FILE 860
//*           bit of source code.  This file is intended to be      *   FILE 860
//*           used together with Gerhard's macro collection on      *   FILE 860
//*           File 861, and with File 862.                          *   FILE 860
//*                                                                 *   FILE 860
//*       My dear friend, and programmer par excellence, Gerhard    *   FILE 860
//*       Postpischil, has passed away.  Please send support        *   FILE 860
//*       requests to:   Sam Golob  email: sbgolob@cbttape.org      *   FILE 860
//*                                                                 *   FILE 860
//*     - - - - - - - - - - - - - - - - - - - - - - - - - - - -     *   FILE 860
//*                                                                 *   FILE 860
//*     Description and Notes for use:                              *   FILE 860
//*                                                                 *   FILE 860
//*     Files 860, 861, and 862 should really be looked at          *   FILE 860
//*     together.                                                   *   FILE 860
//*                                                                 *   FILE 860
//*     This file (860) contains (mostly) assembler programs        *   FILE 860
//*     without JCL.                                                *   FILE 860
//*                                                                 *   FILE 860
//*     File 861 contains most macros required for proper           *   FILE 860
//*     assembly.                                                   *   FILE 860
//*                                                                 *   FILE 860
//*     File 862 contains additional files with procedures,         *   FILE 860
//*     parmlib data, and other supporting material. It also        *   FILE 860
//*     contains auxiliary macros, as PVTMACS, once available       *   FILE 860
//*     from IBM on optional source material tapes. Some            *   FILE 860
//*     macros not available have been concocted from dumps         *   FILE 860
//*     or IBM documentation.                                       *   FILE 860
//*                                                                 *   FILE 860
//*     The programs all ran in production at some point, but       *   FILE 860
//*     some were used under OS/360 only, and some only under       *   FILE 860
//*     MVS/ESA and later. A few members came straight from the     *   FILE 860
//*     CBT for me to look at, but haven't been used yet (e.g.,     *   FILE 860
//*     the HASPX exits, DSAT9).                                    *   FILE 860
//*                                                                 *   FILE 860
//*     Before assembling anything, look at members OPTIONGB and    *   FILE 860
//*     SYSPARM in the macro file. If you have any of the SVCs      *   FILE 860
//*     installed, set their SVC numbers correctly (OS/360,         *   FILE 860
//*     pre-XA only - not used in later systems).  The exception    *   FILE 860
//*     is @SERVICE, described later. Note that the options have    *   FILE 860
//*     provision for ESA and later systems, but only a few         *   FILE 860
//*     members will function correctly. Note that large 3390s      *   FILE 860
//*     were never used nor tested.  If you wish to start from      *   FILE 860
//*     scratch and assemble/link everything, run the SUBnnnnn      *   FILE 860
//*     modules first, then the @nnnnnnn modules (only one of       *   FILE 860
//*     the @SRVJnnn module, matching your JES2 release; this       *   FILE 860
//*     module needs the alias @SRVJES2). Then do individual        *   FILE 860
//*     programs as desired.                                        *   FILE 860
//*                                                                 *   FILE 860
//*     Some modules will not assemble because the macros they      *   FILE 860
//*     reference (USERCVT, USERVOLT, A$GDA, ...) are parts of      *   FILE 860
//*     a proprietary security and accounting system. However,      *   FILE 860
//*     the code may still be useful as groundwork for your own     *   FILE 860
//*     adaptations.                                                *   FILE 860
//*                                                                 *   FILE 860
//*     - - - - - - - - - - - - - - - - - - - - - - - - - - - -     *   FILE 860
//*                                                                 *   FILE 860
//*       At any given MVS system level, the users of the           *   FILE 860
//*       various programs here, may have to do some coding         *   FILE 860
//*       work to fit the programs to their current system.         *   FILE 860
//*       These programs are being presented as-is, for their       *   FILE 860
//*       educational value, and also for their utility value.      *   FILE 860
//*                                                                 *   FILE 860
//*       A bit of Gerhard's history has to be presented and        *   FILE 860
//*       explained, in order to understand this collection.        *   FILE 860
//*       Gerhard has been using MVS from the beginning.  Many      *   FILE 860
//*       programs dated in the 1980's were intended to be          *   FILE 860
//*       run on MVS SP 1.3.x.  XA and ESA followed, into the       *   FILE 860
//*       1990's.  In the 2000's, Gerhard began running MVS         *   FILE 860
//*       3.8J (the free version from circa 1975 which was          *   FILE 860
//*       highly modified in the subsequent years).  So the         *   FILE 860
//*       history of Gerhard's efforts went from MVS/SP, thru       *   FILE 860
//*       XA, thru ESA, and then back to MVS 3.8J, where he         *   FILE 860
//*       started.                                                  *   FILE 860
//*                                                                 *   FILE 860
//*       Gerhard's latest programs are, for the most part,         *   FILE 860
//*       intended to be assembled and run on MVS 3.8J, but         *   FILE 860
//*       they may, or may not, have to be fixed (but they          *   FILE 860
//*       certainly have to be assembled) for other system          *   FILE 860
//*       levels.                                                   *   FILE 860
//*                                                                 *   FILE 860
//*       There is immense value in this collection,                *   FILE 860
//*       because of the great range of topics covered in           *   FILE 860
//*       the programs.  Although many of the programs were         *   FILE 860
//*       originally taken from the CBT Tape, Gerhard has           *   FILE 860
//*       conscientiously fixed many bugs in them, over the         *   FILE 860
//*       years.                                                    *   FILE 860
//*                                                                 *   FILE 860
//*       If you changed something and made it useful, or you       *   FILE 860
//*       made it runnable at a certain system level, please        *   FILE 860
//*       send the changed program(s) back to Sam Golob             *   FILE 860
//*       (sbgolob@cbttape.org), as a courtesy, so that other       *   FILE 860
//*       people won't have to do the same work over again.         *   FILE 860
//*                                                                 *   FILE 860
//*       If you have any question about what was done to any       *   FILE 860
//*       specific program, or why he wrote any specific macro,     *   FILE 860
//*       you should try to email Gerhard or call him, for          *   FILE 860
//*       further information.  You should look at pds member       *   FILE 860
//*       DOC on File 862 to learn more about some of the           *   FILE 860
//*       programs that are here.                                   *   FILE 860
//*                                                                 *   FILE 860

```
