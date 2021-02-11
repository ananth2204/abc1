```
//***FILE 220 is from Lee Conyers of the U.S. Department of         *   FILE 220
//*           Transportation in Washington, D.C.  This is a         *   FILE 220
//*           collection of E.D.P. Auditing tools, to be used       *   FILE 220
//*           in finding out information about an MVS system        *   FILE 220
//*           without much outside help (that's one of the          *   FILE 220
//*           things that E.D.P. Auditors do).  This is (of         *   FILE 220
//*           course) also useful for MVS Systems Programmers.      *   FILE 220
//*                                                                 *   FILE 220
//*           Most of the REXX EXECs in this collection have been   *   FILE 220
//*           converted into fixed blocked LRECL=80 format.  They   *   FILE 220
//*           are no longer contained (in IEBUPDTE - PDSLOAD        *   FILE 220
//*           format) in a single member, but they have now been    *   FILE 220
//*           separated into individual members, so that it will    *   FILE 220
//*           be easier to find them and use them.                  *   FILE 220
//*                                                                 *   FILE 220
//*           See File 221 for the REXX EXECs in this collection,   *   FILE 220
//*           in VB format with LRECL=255.                          *   FILE 220
//*                                                                 *   FILE 220
//*           This collection was developed, a long time ago,       *   FILE 220
//*           at the MVS/XA 2.2.3 level.  Most of the EXECs have    *   FILE 220
//*           now been converted, by Anthony Cieri, to run on       *   FILE 220
//*           z/OS 1.13, 2.1, and 2.2.                              *   FILE 220
//*                                                                 *   FILE 220
//*                < ------ >  z/OS 1.13  < ------ >                *   FILE 220
//*                < ------ >  z/OS 2.1   < ------ >                *   FILE 220
//*                                                                 *   FILE 220
//*    Note:  Lee Conyers has unfortunately passed on.              *   FILE 220
//*    ----                                                         *   FILE 220
//*           Most of the REXX execs in this collection have        *   FILE 220
//*           been upgraded to the z/OS 1.13 level by Tony Cieri.   *   FILE 220
//*           Tony's TSO userid and the ISPF date, will indicate    *   FILE 220
//*           which members have been updated (most of them).       *   FILE 220
//*                                                                 *   FILE 220
//*             Anthony J.Cieri                                     *   FILE 220
//*             SEI Investments                                     *   FILE 220
//*             1 Freedom Valley Drive                              *   FILE 220
//*             Oaks, PA 19456                                      *   FILE 220
//*                                                                 *   FILE 220
//*             (P) 610.676.4088                                    *   FILE 220
//*             (F) 484.676.4088                                    *   FILE 220
//*             Email: acieri@seic.com                              *   FILE 220
//*                                                                 *   FILE 220
//*                < ------ >  z/OS 1.13  < ------ >                *   FILE 220
//*                < ------ >  z/OS 2.1   < ------ >                *   FILE 220
//*                                                                 *   FILE 220
//*           I'd also suggest looking at the "SHOWzOS" TSO         *   FILE 220
//*           command on File 492 of this tape, to supply some      *   FILE 220
//*           more of this kind of information.  (S.G.)             *   FILE 220
//*                                                                 *   FILE 220
//*           INTRODUCTION TO THE AUDITMVS STARTER KIT              *   FILE 220
//*           ----------------------------------------              *   FILE 220
//*                                                                 *   FILE 220
//*     THIS FILE CONTAINS THE AUDITMVS STARTER KIT SOFTWARE.       *   FILE 220
//*     THE KIT CONSISTS OF UTILITY SOFTWARE TO COLLECT AND         *   FILE 220
//*     ANALYZE DATA FROM AN OPERATIONAL MVS SYSTEM.  IT WILL       *   FILE 220
//*     GREATLY ASSIST IN DOCUMENTING THE AUTHORIZED PROGRAM        *   FILE 220
//*     FACILITY (APF) ENVIRONMENT, INCLUDING ALL APF LIBRARIES,    *   FILE 220
//*     SUPERVISOR CALL (SVC) ROUTINES, EXTENDED SVC ROUTER (ESR)   *   FILE 220
//*     ROUTINES, PROGRAM CALL (PC) ROUTINES, AND LINK PACK AREA    *   FILE 220
//*     (LPA) PROGRAMS (I.E., PAGEABLE, MODIFIED, FIXED LPA; AND    *   FILE 220
//*     OTHER ITEMS ALONG THE LPA QUEUE).                           *   FILE 220
//*                                                                 *   FILE 220
//*     THE SOFTWARE CONSISTS MOSTLY OF REXX AND SAS PROGRAMS.      *   FILE 220
//*     IN ADDITION, THERE ARE SEVERAL ASSEMBLY LANGUAGE PROGRAMS   *   FILE 220
//*     TO DISASSEMBLE MVS SOFTWARE FROM OBJECT CODE BACK TO        *   FILE 220
//*     ASSEMBLY LANGUAGE.  THERE IS ALSO AN ASSEMBLY LANGUAGE      *   FILE 220
//*     PROGRAM THAT USES THE SNAP MACRO TO RETRIEVE THE PROGRAM    *   FILE 220
//*     CALL TABLE FROM THE PCAUTH ADDRESS SPACE.                   *   FILE 220
//*                                                                 *   FILE 220
//*     THE CONTENTS OF THIS DISKETTE SHOULD BE UPLOADED TO THE     *   FILE 220
//*     MVS SYSTEM THAT IS TO BE AUDITED.  ALL OF THE FILES,        *   FILE 220
//*     EXCEPT THE REXX PROGRAMS, MAY BE PLACED INTO INDIVIDUAL     *   FILE 220
//*     MEMBERS OF A STANDARD FB 80 PARTITIONED DATA SET (PDS).     *   FILE 220
//*     THE REXX PROGRAMS SOMETIMES EXCEED LINE LENGTHS BEYOND 72   *   FILE 220
//*     CHARACTERS--THEREFORE, A VB 255 PDS IS RECOMMENDED.  BOTH   *   FILE 220
//*     FB 80 AND VB 255 FORMATS ARE SUPPORTED BY THE ISPF/PDF      *   FILE 220
//*     EDITOR.  TO SUMMARIZE, THE FOLLOWING                        *   FILE 220
//*     DISKETTE-DIRECTORY-TO-MVS-PDS UPLOAD STRUCTURE IS           *   FILE 220
//*     SUGGESTED:                                                  *   FILE 220
//*                                                                 *   FILE 220
//*     FILE MEMBER                 MVS PDS AND DCB INFO            *   FILE 220
//*     ------------------    --------------------------------      *   FILE 220
//*                                                                 *   FILE 220
//*     ADVCAATS              USERID.DISASM.CNTL      FB   80       *   FILE 220
//*     MISC                  USERID.CNTL             FB   80       *   FILE 220
//*     REXX  (FILE 221)      USERID.EXEC             VB  255       *   FILE 220
//*     SAS                   USERID.SAS.CNTL         FB   80       *   FILE 220
//*                                                                 *   FILE 220
//*     SOME OF THE STARTER KIT PROGRAMS ALSO REQUIRE A NUMBER OF   *   FILE 220
//*     MVS SUPPORT FILES.  FOR EXAMPLE, THE IO* REXX PROGRAMS      *   FILE 220
//*     ARE DATA COLLECTORS WHICH WRITE TO VARIOUS VB 255           *   FILE 220
//*     PHYSICAL SEQUENTIAL DATA SETS.  THESE DATA SETS ARE THEN    *   FILE 220
//*     READ BY THE SAS PROGRAMS FOR ANALYSIS AND REPORTING.  YOU   *   FILE 220
//*     WILL HAVE TO ALLOCATE AND NAME THESE TO YOUR OWN            *   FILE 220
//*     PREFERENCE, AND EDIT THE REXX AND SAS PROGRAMS              *   FILE 220
//*     ACCORDINGLY.  THERE IS ONE SUPPORT DATA SET THAT MUST BE    *   FILE 220
//*     FORMATTED SPECIFICALLY TO SUPPORT THE OUTPUT OF THE SNAP    *   FILE 220
//*     MACRO.  SEE THE ASSEMBLY LANGUAGE PROGRAM (SNAPPC.ASM IN    *   FILE 220
//*     THE MISC DIRECTORY) FOR THESE SPECIFIC DCB PARAMETERS.      *   FILE 220
//*                                                                 *   FILE 220
//*     ADVCAATS                                                    *   FILE 220
//*     --------                                                    *   FILE 220
//*                                                                 *   FILE 220
//*     THIS LIBRARY CONTAINS SOURCE CODE FOR A OLD, OLD (BUT       *   FILE 220
//*     VERY USEFUL) PUBLIC DOMAIN DISASSEMBLER.  THE               *   FILE 220
//*     DISASSEMBLER HAS BEEN EXTENDED TO PERFORM IN-STORAGE        *   FILE 220
//*     DISASSEMBLY IF THE CODE RESIDES BELOW THE 16 MB LINE.       *   FILE 220
//*     SEE THE FILE $$README FOR MORE INFORMATION.                 *   FILE 220
//*                                                                 *   FILE 220
//*     MISC                                                        *   FILE 220
//*     ----                                                        *   FILE 220
//*                                                                 *   FILE 220
//*     THIS LIBRARY CONTAINS SEVERAL *.JCL FILES.  ALLOCGDG.JCL    *   FILE 220
//*     SHOWS HOW TO DEFINE A GENERATION DATA GROUP (GDG) SHOULD    *   FILE 220
//*     YOU WANT TO BUILD A SYSTEM OF AUDIT JOBS THAT MAINTAIN      *   FILE 220
//*     SNAPSHOT CYCLES OF DATA SETS FOR YOUR MVS SYSTEM.           *   FILE 220
//*     IKJEFT01.JCL SHOWS HOW TO RUN YOUR REXX PROGRAMS IN         *   FILE 220
//*     "BATCH MODE" TSO.  OTHER JCL FILES PROVIDE EXAMPLES OF      *   FILE 220
//*     LENGTHY JOB STREAMS FOR MULTIPLE AUDIT STEPS.  THIS         *   FILE 220
//*     LIBRARY ALSO CONTAINS THE SNAPPC.ASM FILE FOR OBTAINING     *   FILE 220
//*     YOUR MVS SYSTEMS PC TABLE.                                  *   FILE 220
//*                                                                 *   FILE 220
//*     REXX     (FOUND IN FILE 221)                                *   FILE 220
//*     ----                                                        *   FILE 220
//*                                                                 *   FILE 220
//*     THIS LIBRARY CONTAINS A WIDE VARIETY OF REXX PROGRAMS       *   FILE 220
//*     THAT COLLECT DATA FROM AN OPERATIONAL MVS SYSTEM.  ALL      *   FILE 220
//*     ARE STAND ALONE PROGRAMS EXCEPT FOR #NUCLKUP, WHICH IS AN   *   FILE 220
//*     EXTERNAL REXX CALLABLE PROCEDURE THAT SEACHES THE NUCLEUS   *   FILE 220
//*     MAP FOR AN ENTRY NAME AND RETURNS ITS ENTRY POINT           *   FILE 220
//*     ADDRESS.  #NUCLKUP IS CURRENTLY CALLED BY IOSVCT, IOESRT,   *   FILE 220
//*     LISTSVCT, AND LISTESRT.  SDUMP IS A GENERAL PURPOSE         *   FILE 220
//*     FORMATTED DISPLAY STORAGE DUMP PROGRAM.  THE VSDATA1        *   FILE 220
//*     PROGRAM IS A MODIFIED VERSION OF SDUMP WHICH DISPLAYS       *   FILE 220
//*     SEVERAL IN-STORAGE CONTROL BLOCKS.                          *   FILE 220
//*                                                                 *   FILE 220
//*     THE IO* SERIES OF PROGRAMS COLLECT DATA AND WRITE TO        *   FILE 220
//*     "WORK.DATA" DATA SETS.  THE LIST* SERIES OF PROGRAMS CAN    *   FILE 220
//*     ALL BE EXECUTED INTERACTIVELY TO DISPLAY MVS INTERNALS      *   FILE 220
//*     DATA TO YOUR TERMINAL SCREEN.  ACRONYMS USED WITHIN THE     *   FILE 220
//*     NAMING SCHEME FOR THESE PROGRAMS ARE:                       *   FILE 220
//*                                                                 *   FILE 220
//*        ADSP     ADDRESS SPACE                                   *   FILE 220
//*        APFP     APF LIBRARIES PROGRAMS                          *   FILE 220
//*        APFT     APF TABLE                                       *   FILE 220
//*        CATS     CATALOGS                                        *   FILE 220
//*        CONS     CONSOLES                                        *   FILE 220
//*        DASD     DIRECT ACCESS STORAGE DEVICES LIST              *   FILE 220
//*        DCQ      DEVICE CLASS QUEUE                              *   FILE 220
//*        ENV      ENVIRONMENTAL INFORMATION                       *   FILE 220
//*        ESRT     ESR TABLE                                       *   FILE 220
//*        LLT      LINKLIST LIBRARIES TABLE                        *   FILE 220
//*        LLTP     LLT LIBRARIES PROGRAMS                          *   FILE 220
//*        LPAQ     LPA QUEUE                                       *   FILE 220
//*        LPAT     LPA LIBRARIES TABLE                             *   FILE 220
//*        NUCM     NUCLEUS MAP                                     *   FILE 220
//*        PART     PAGING ACTIVITY REFERENCE TABLE                 *   FILE 220
//*        PDSD     PDS DIRECTORY                                   *   FILE 220
//*        PDSM     PDS MEMBERS                                     *   FILE 220
//*        PCAUTH   PROGRAM CALL AUTHORIZATION TABLE                *   FILE 220
//*        PLPA     PAGEABLE LPA PROGRAMS                           *   FILE 220
//*        SART     SWAPPING ACTIVITY REFERENCE TABLE               *   FILE 220
//*        SDUMP    DISPLAY 31-BIT STORAGE                          *   FILE 220
//*        SDUMPE   DISPLAY 64-BIT STORAGE BUT TRUNCATE HI 4 CHARS  *   FILE 220
//*        SDUMPG   DISPLAY 64-BIT STORAGE - DISPLAY 83 BYTES WIDE  *   FILE 220
//*        SFT      SYSTEM FUNCTION TABLE                           *   FILE 220
//*        SMAP     STORAGE MAP INFORMATION                         *   FILE 220
//*        SMF      SYSTEM MANAGEMENT FACILITY INFORMATION          *   FILE 220
//*        SSN      SUBSYSTEM NAME TABLE                            *   FILE 220
//*        SVCJ     SVC JOURNAL TABLE                               *   FILE 220
//*        SVCT     SVC TABLE                                       *   FILE 220
//*        TAPE     TAPE DEVICES LIST                               *   FILE 220
//*        VMAP     VIRTUAL STORAGE MAP                             *   FILE 220
//*                                                                 *   FILE 220
//*     THE NOT@OR FILE IS A READY REFERENCE OF THE EBCDIC HEX      *   FILE 220
//*     CODES FOR THE "AND" AND "OR" CHARACTERS.  THESE TWO         *   FILE 220
//*     CHARACTERS ARE HARD TO REMEMBER WHEN ONE USES SEVERAL       *   FILE 220
//*     DIFFERENT MICROCOMPUTER KEYBOARD MAPS ASSOCIATED WITH       *   FILE 220
//*     VARIOUS 3270 EMULATION SOFTWARE PACKAGES.                   *   FILE 220
//*                                                                 *   FILE 220
//*     SAS                                                         *   FILE 220
//*     ---                                                         *   FILE 220
//*                                                                 *   FILE 220
//*     THIS LIBRARY CONTAINS SAS PROGRAMS WHICH REPORT FROM THE    *   FILE 220
//*     VARIOUS FILES CREATED BY THE IO* SERIES OF REXX PROGRAMS.   *   FILE 220
//*     THE APFPDUP, LLTPDUP, LPAPDUP, ESRMATCH, PCMATCH, AND       *   FILE 220
//*     SVCMATCH PROGRAMS DEMONSTRATE THE POWER OF THE SAS MERGE    *   FILE 220
//*     FUNCTION.                                                   *   FILE 220
//*                                                                 *   FILE 220
//*                                                                 *   FILE 220
//*           LEE CONYERS                                           *   FILE 220
//*           U.S. DEPARTMENT OF TRANSPORTATION                     *   FILE 220
//*           700 4TH STREET SW                                     *   FILE 220
//*           ROOM 7404, M-35                                       *   FILE 220
//*           WASHINGTON, DC  20590                                 *   FILE 220
//*           (202) 366-1126                                        *   FILE 220
//*                                               -- VLC (3/27/94)  *   FILE 220
//*                                                                 *   FILE 220
//*    Note from Sam Golob     (March 5, 2014)                      *   FILE 220
//*                                                                 *   FILE 220
//*    Addition to CBT File 220, from CBT File 221.                 *   FILE 220
//*                                                                 *   FILE 220
//*    I converted many of the LIST*** REXXes to FB-80, so I        *   FILE 220
//*    could include them in my SYSPROC concatenation which is      *   FILE 220
//*    FB-80, as opposed to VB-255.  They are here in this          *   FILE 220
//*    member called REXXES, which is really a PDS in IEBUPDTE      *   FILE 220
//*    (PDSLOAD) format, for your use and pleasure.  These are      *   FILE 220
//*    really valuable and easily installable tools, to help        *   FILE 220
//*    you (or the auditors) to get a better insight into the       *   FILE 220
//*    specific workings of your MVS system.                        *   FILE 220
//*                                                                 *   FILE 220
//*    The REXXes that I have not yet converted, are the ones       *   FILE 220
//*    which don't seem to work right under z/OS 1.13               *   FILE 220
//*    (although I may have missed one or two which do work).       *   FILE 220
//*    These are on my "to do" list, to improve, both in the        *   FILE 220
//*    FB-80 and VB-255 versions.                                   *   FILE 220
//*                                                                 *   FILE 220
//*    The LISTDASD and LISTTAPE REXXes have been fixed.            *   FILE 220
//*                                                                 *   FILE 220
//*    The LISTDCQ REXX has been fixed.                             *   FILE 220
//*                                                                 *   FILE 220
//*    The IO*** members have not been converted.                   *   FILE 220
//*                                                                 *   FILE 220
//*    Lee Conyers (who has passed on) was really an expert         *   FILE 220
//*    auditor and he knew a lot about what makes the system        *   FILE 220
//*    tick, especially in those areas that an auditor has to       *   FILE 220
//*    watch.  It is a pleasure to be able to use his               *   FILE 220
//*    excellent tools.  That is why I have tried to make them      *   FILE 220
//*    even more useful, for today's environment.                   *   FILE 220
//*                                                                 *   FILE 220
//*    For the record, SHOWzOS on CBT File 492 (load module         *   FILE 220
//*    collection on CBT File 614) is also extremely useful to      *   FILE 220
//*    supplement this information obtainable with the REXXes       *   FILE 220
//*    here.                                                        *   FILE 220
//*                                                                 *   FILE 220
//*    We have included a TSO command to clear the screen, which    *   FILE 220
//*    is needed by the REXXes in File 221 and member REXXES in     *   FILE 220
//*    this file.  This is member CLEAR and its assembly JCL,       *   FILE 220
//*    member CLEAR$.                                               *   FILE 220
//*                                                                 *   FILE 220
//*    All the best of everything to all of you.                    *   FILE 220
//*                                                                 *   FILE 220
//*    Sam                                                          *   FILE 220
//*                                                                 *   FILE 220

//***FILE 221 is from Lee Conyers of the U.S. Department of         *   FILE 221
//*           Transportation in Washington, D.C.  See File 220      *   FILE 221
//*           for a description of this entire collection of        *   FILE 221
//*           E.D.P. auditing tools.  This file contains the        *   FILE 221
//*           REXX execs from the collection, that have been        *   FILE 221
//*           separated out because of their DCB format, which      *   FILE 221
//*           is VB with LRECL(255).  This file is in IEBCOPY       *   FILE 221
//*           format.                                               *   FILE 221
//*                                                                 *   FILE 221
//*                < ------ >  z/OS 2.1   < ------ >                *   FILE 221
//*                                                                 *   FILE 221
//*    Note:  Lee Conyers has unfortunately passed on.              *   FILE 221
//*    ----                                                         *   FILE 221
//*           Most of the REXX execs in this collection have        *   FILE 221
//*           been upgraded to the z/OS 1.13 level by Tony Cieri.   *   FILE 221
//*           Tony's TSO userid and the ISPF date, will indicate    *   FILE 221
//*           which members have been updated (most of them).       *   FILE 221
//*                                                                 *   FILE 221
//*             Anthony J.Cieri                                     *   FILE 221
//*             SEI Investments                                     *   FILE 221
//*             1 Freedom Valley Drive                              *   FILE 221
//*             Oaks, PA 19456                                      *   FILE 221
//*                                                                 *   FILE 221
//*             (P) 610.676.4088                                    *   FILE 221
//*             (F) 484.676.4088                                    *   FILE 221
//*             Email: acieri@seic.com                              *   FILE 221
//*                                                                 *   FILE 221
//*           Many of these execs have been converted to FB-80      *   FILE 221
//*           format from VB-255.  The converted execs can be       *   FILE 221
//*           found on CBT File 220 as member REXXES.  This         *   FILE 221
//*           member is in IEBUPDTE (PDSLOAD) format, with the      *   FILE 221
//*           ISPF statistics preserved.  Use the PDSLOAD program   *   FILE 221
//*           from File 093 to restore the FB-80 pds of REXX        *   FILE 221
//*           execs, corresponding to most of the execs on this     *   FILE 221
//*           file.                                                 *   FILE 221
//*                                                                 *   FILE 221
//*                < ------ >  z/OS 2.1   < ------ >                *   FILE 221
//*                                                                 *   FILE 221

```
