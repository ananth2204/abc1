```
//***FILE 862 is from Gerhard Postpischil and contains members      *   FILE 862
//*           which are each really IEBUPDTE (PDSLOAD) unloaded     *   FILE 862
//*           pds'es.  These are related to Gerhard's contributions *   FILE 862
//*           on Files 860 and 861, but they are in addition to     *   FILE 862
//*           them.  And some of his documentation in the DOC       *   FILE 862
//*           member, may apply to the materials in File 860.       *   FILE 862
//*                                                                 *   FILE 862
//*       My dear friend, and programmer par excellence, Gerhard    *   FILE 862
//*       Postpischil, has passed away.  Please send support        *   FILE 862
//*       requests to:   Sam Golob  email: sbgolob@cbttape.org      *   FILE 862
//*                                                                 *   FILE 862
//*           Member LOADLIB is in TSO XMIT format.                 *   FILE 862
//*                                                                 *   FILE 862
//*           Member REVLMOD is in REVIEW REVLMOD format, to help   *   FILE 862
//*           the MVS 3.8 people recreate the load library.         *   FILE 862
//*                                                                 *   FILE 862
//*     - - - - - - - - - - - - - - - - - - - - - - - - - - - -     *   FILE 862
//*                                                                 *   FILE 862
//*     Description and Notes for use:                              *   FILE 862
//*                                                                 *   FILE 862
//*     Files 860, 861, and 862 should really be looked at          *   FILE 862
//*     together.                                                   *   FILE 862
//*                                                                 *   FILE 862
//*     This file (860) contains (mostly) assembler programs        *   FILE 862
//*     without JCL.                                                *   FILE 862
//*                                                                 *   FILE 862
//*     File 861 contains most macros required for proper           *   FILE 862
//*     assembly.                                                   *   FILE 862
//*                                                                 *   FILE 862
//*     File 862 contains additional files with procedures,         *   FILE 862
//*     parmlib data, and other supporting material. It also        *   FILE 862
//*     contains auxiliary macros, as PVTMACS, once available       *   FILE 862
//*     from IBM on optional source material tapes. Some            *   FILE 862
//*     macros not available have been concocted from dumps         *   FILE 862
//*     or IBM documentation.                                       *   FILE 862
//*                                                                 *   FILE 862
//*     The programs all ran in production at some point, but       *   FILE 862
//*     some were used under OS/360 only, and some only under       *   FILE 862
//*     MVS/ESA and later. A few members came straight from the     *   FILE 862
//*     CBT for me to look at, but haven't been used yet (e.g.,     *   FILE 862
//*     the HASPX exits, DSAT9).                                    *   FILE 862
//*                                                                 *   FILE 862
//*     Before assembling anything, look at members OPTIONGB and    *   FILE 862
//*     SYSPARM in the macro file. If you have any of the SVCs      *   FILE 862
//*     installed, set their SVC numbers correctly (OS/360,         *   FILE 862
//*     pre-XA only - not used in later systems).  The exception    *   FILE 862
//*     is @SERVICE, described later. Note that the options have    *   FILE 862
//*     provision for ESA and later systems, but only a few         *   FILE 862
//*     members will function correctly. Note that large 3390s      *   FILE 862
//*     were never used nor tested.  If you wish to start from      *   FILE 862
//*     scratch and assemble/link everything, run the SUBnnnnn      *   FILE 862
//*     modules first, then the @nnnnnnn modules (only one of       *   FILE 862
//*     the @SRVJnnn module, matching your JES2 release; this       *   FILE 862
//*     module needs the alias @SRVJES2). Then do individual        *   FILE 862
//*     programs as desired.                                        *   FILE 862
//*                                                                 *   FILE 862
//*     Some modules will not assemble because the macros they      *   FILE 862
//*     reference (USERCVT, USERVOLT, A$GDA, ...) are parts of      *   FILE 862
//*     a proprietary security and accounting system. However,      *   FILE 862
//*     the code may still be useful as groundwork for your own     *   FILE 862
//*     adaptations.                                                *   FILE 862
//*                                                                 *   FILE 862

```
