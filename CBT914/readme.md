```
//***FILE 914 is from Steve McColley and contains the Shared Spool  *   FILE 914
//*           Mods (previously known as the "Mellon Mods" for JES2) *   FILE 914
//*           which should be good for z/OS 2.1.                    *   FILE 914
//*           (They were tested on a z/OS 2.1 system.)              *   FILE 914
//*           system.)                                              *   FILE 914
//*                                                                 *   FILE 914
//*                Stephen McColley                                 *   FILE 914
//*                McColley Systems Group Inc.                      *   FILE 914
//*                SGMcColley@MVSProgrammer.com                     *   FILE 914
//*                http://WWW.MVSProgrammer.com                     *   FILE 914
//*                770-335-0478                                     *   FILE 914
//*                                                                 *   FILE 914
//*                                                                 *   FILE 914
//*                SSSS H   H  AAA  RRRR  EEEEE DDDD                *   FILE 914
//*               S     H   H A   A R   R E     D   D               *   FILE 914
//*                SSS  HHHHH AAAAA RRRR  EEEE  D   D               *   FILE 914
//*                   S H   H A   A R  R  E     D   D               *   FILE 914
//*               SSSS  H   H A   A R   R EEEEE DDDD                *   FILE 914
//*                                                                 *   FILE 914
//*                   SSSS PPPP   OOO   OOO  L                      *   FILE 914
//*                  S     P   P O   O O   O L                      *   FILE 914
//*                   SSS  PPPP  O   O O   O L                      *   FILE 914
//*                      S P     O   O O   O L                      *   FILE 914
//*                  SSSS  P      OOO   OOO  LLLLL                  *   FILE 914
//*                                                                 *   FILE 914
//*                     M   M  OOO  DDDD   SSSS                     *   FILE 914
//*                     MM MM O   O D   D S                         *   FILE 914
//*                     M M M O   O D   D  SSS                      *   FILE 914
//*                     M   M O   O D   D     S                     *   FILE 914
//*                     M   M  OOO  DDDD  SSSS                      *   FILE 914
//*                                                                 *   FILE 914
//*                     for JES2 2.1 - HJE7790                      *   FILE 914
//*                                                                 *   FILE 914
//*                                                                 *   FILE 914
//*      DISCLAIMER -                                               *   FILE 914
//*                                                                 *   FILE 914
//*    ***********************************************************  *   FILE 914
//*    *                                                         *  *   FILE 914
//*    *  THE MODS ON THIS TAPE HAVE BEEN USED SUCCESSFULLY AND  *  *   FILE 914
//*    *  TO THE BEST OF OUR KNOWLEDGE THEY ARE OPERATIONAL,     *  *   FILE 914
//*    *  HOWEVER NO WARRANTY IS MADE TO THE ACCURACY OF THE     *  *   FILE 914
//*    *  MODS AND NO RESPONSIBILITY IS ASSUMED FOR ANY          *  *   FILE 914
//*    *  MODIFICATION DIRECTLY OR INDIRECTLY CAUSED BY THE USE  *  *   FILE 914
//*    *  OF THE MODIFICATIONS.  IT IS THE USERS RESPONSIBILITY  *  *   FILE 914
//*    *  TO EVALUATE THE USEFULLNESS OF THE MATERIAL.           *  *   FILE 914
//*    *                                                         *  *   FILE 914
//*    *  WE DO NOT GUARANTEE TO KEEP ANY MATERIAL PROVIDED UP   *  *   FILE 914
//*    *  TO DATE, NOR DO WE GUARANTEE TO PROVIDE ANY            *  *   FILE 914
//*    *  CORRECTIONS OR EXTENSIONS MADE IN THE FUTURE.          *  *   FILE 914
//*    *                                                         *  *   FILE 914
//*    ***********************************************************  *   FILE 914
//*                                                                 *   FILE 914
//*                                                                 *   FILE 914
//*     This is the installation PDS for the Shared Spool Mods      *   FILE 914
//*     for JES2 2.1.  The Shared Spool Mods were formerly known    *   FILE 914
//*     as the Mellon Shared Spool Mods.                            *   FILE 914
//*                                                                 *   FILE 914
//*     All who use the shared spool mods, owe a debt of            *   FILE 914
//*     gratitude to Mellon Bank for the original implementaion     *   FILE 914
//*     of the shared spool mods, but because it has been           *   FILE 914
//*     maintained outside of Mellon for over 18 years, and has     *   FILE 914
//*     been rewritten twice since then, we will refer to the       *   FILE 914
//*     mods as the SHARED SPOOL MODS from now on.  Once again      *   FILE 914
//*     - - - -                                                     *   FILE 914
//*                    THANK YOU MELLON BANK !                      *   FILE 914
//*                                                                 *   FILE 914
//*      In this PDS you should find the following members.         *   FILE 914
//*                                                                 *   FILE 914
//*                  ( ADMINISTRATIVE MEMBERS )                     *   FILE 914
//*    @@README -   That is this member, you are reading it.        *   FILE 914
//*                                                                 *   FILE 914
//*    DISCLAIM -   Our standard disclaimer -                       *   FILE 914
//*                 we guarantee / warrant nothing!                 *   FILE 914
//*                                                                 *   FILE 914
//*    INSTALL  -   This member describes how to get                *   FILE 914
//*                 install documentation.                          *   FILE 914
//*                 - or just read the next few lines...            *   FILE 914
//*                                                                 *   FILE 914
//*              ( DOCUMENTATION - PDF AND DOC FORMAT MANUALS )     *   FILE 914
//*                                                                 *   FILE 914
//*    There are three (3) seperate manuals.  They are provided     *   FILE 914
//*    in two (2) different formats each.  You must transfer        *   FILE 914
//*    them to your pc with a binary transfer to the correct        *   FILE 914
//*    file type for each before you can use them.  SSM****P        *   FILE 914
//*    members are manuals in PDF format.  SSM****D are members     *   FILE 914
//*    in WORD format and should be downloaded as .DOC files.       *   FILE 914
//*                                                                 *   FILE 914
//*    SSMINSTP -   Shared Spool Mods installation manual           *   FILE 914
//*                 - PDF format (simply download to your           *   FILE 914
//*                 PC as ssminst.pdf - binary xfer)                *   FILE 914
//*                                                                 *   FILE 914
//*    SSMINSTD -   Shared Spool Mods installation manual           *   FILE 914
//*                 - Word Document (simply download to             *   FILE 914
//*                 your PC as ssminst.doc - binary xfer)           *   FILE 914
//*                                                                 *   FILE 914
//*    SSMUSERP -   Shared Spool Mods Users Guide - PDF             *   FILE 914
//*                 format (simply download to your PC as           *   FILE 914
//*                 ssmuser.pdf - binary xfer)                      *   FILE 914
//*                                                                 *   FILE 914
//*    SSMUSERD -   Shared Spool Mods Users Buide - Word            *   FILE 914
//*                 Document (simply download to your PC            *   FILE 914
//*                 as ssmuser.doc - binary xfer)                   *   FILE 914
//*                                                                 *   FILE 914
//*    SSMOPSGP -   Shared Spool Mods Operations Guide -            *   FILE 914
//*                 PDF format (simply download to your PC          *   FILE 914
//*                 as ssmopsg.pdf - binary xfer)                   *   FILE 914
//*                                                                 *   FILE 914
//*    SSMOPSGD -   Shared Spool Mods Operations Guide -            *   FILE 914
//*                 Word Document (simply download to your          *   FILE 914
//*                 PC as ssmopsg.doc - binary xfer)                *   FILE 914
//*                                                                 *   FILE 914
//*                   ( SMP INSTALLATION MEMBERS )                  *   FILE 914
//*    LSES500  -   The SMP/e usermod that you can use to           *   FILE 914
//*                 install the entire package.                     *   FILE 914
//*                                                                 *   FILE 914
//*    LSES500J -   Sample JCL to run the RECEIVE / APPLY Check     *   FILE 914
//*        / APPLY (You must apply lses500 or use the non-smp       *   FILE 914
//*        install method).                                         *   FILE 914
//*                                                                 *   FILE 914
//*                 ( NON-SMP INSTALLATION MEMBERS )                *   FILE 914
//*                                                                 *   FILE 914
//*    ALOCLIBS -  NON-SMP STEP 1 - ALLOCATE NEW LIBRARIES.         *   FILE 914
//*                                                                 *   FILE 914
//*    COPYLIBS -  NON-SMP STEP 2 - POPULATE NEW LIBRARIES.         *   FILE 914
//*                                                                 *   FILE 914
//*              ( COMMON JES2 PARMS NEEDED FOR PACKAGE )           *   FILE 914
//*    JES2PARM -   SAMPLE JES2 PARMS NEEDED TO IMPLEMENT THE       *   FILE 914
//*                 PACKAGE.                                        *   FILE 914
//*                                                                 *   FILE 914
//*    *** The following members are used as input to the  ***      *   FILE 914
//*    ***  COPYLIBS job which is part of the NON_SMP/E    ***      *   FILE 914
//*         install path.                                           *   FILE 914
//*                                                                 *   FILE 914
//*    RAWASM   -  IEBUPDTE format input to populate the ASM        *   FILE 914
//*                library.                                         *   FILE 914
//*                                                                 *   FILE 914
//*    RAWJCL   -  IEBUPDTE format input to populate the JCL        *   FILE 914
//*                library.                                         *   FILE 914
//*                                                                 *   FILE 914
//*    RAWMACS  -  IEBUPDTE format input to populate the MACROS     *   FILE 914
//*                library.                                         *   FILE 914
//*                                                                 *   FILE 914
//*    *** The members with the general name form of SAMP****   *** *   FILE 914
//*    *** are optional IVP (Installation Verification          *** *   FILE 914
//*    *** Procedures) jobs.  member SAMPINDX contains an index *** *   FILE 914
//*    *** of all the SAMP**** jobs.                            *** *   FILE 914
//*                                                                 *   FILE 914
//*                                                                 *   FILE 914
//*    *** THEN WE HAVE THE FOLLOWING FOUR MEMBERS - THEY ARE   *** *   FILE 914
//*    *** NOT REALLY PART OF THE SHARED SPOOL MODS - BUT WE    *** *   FILE 914
//*    *** HAVE BEEN DISTRIBUTING THEM, AND SOME FOLKS STILL    *** *   FILE 914
//*    *** NEED THEM.  IF YOU WANT TO USE THESE, YOU WILL HAVE  *** *   FILE 914
//*    *** TO APPLY THEM SEPERATELY FROM THE SHARED SPOOL MODS  *** *   FILE 914
//*    *** - WE JUST HAVE THE SOURCE - THEY ARE NOT SETUP AS    *** *   FILE 914
//*    *** USERMODS.                                                *   FILE 914
//*                                                                 *   FILE 914
//*    STSCX01A -   OUR VERSION OF THE PAGE SEPARATOR EXIT.         *   FILE 914
//*                 (NOT PART OF SSM'S)                             *   FILE 914
//*                                                                 *   FILE 914
//*    STSCX05B -   PREVENT PURGING BY JOB RANGE. (NOT PART OF      *   FILE 914
//*                 SSM'S)                                          *   FILE 914
//*                                                                 *   FILE 914
//*    STSCX15A -   CAUSES FCBS TO BE RELOADED WITH EACH JOB        *   FILE 914
//*                 UNLESS STD FORMS.                               *   FILE 914
//*                                                                 *   FILE 914
//*    STSCX36A -   SAF PROCESSING FOR JOBS COMING IN FROM          *   FILE 914
//*                 RJE/NJE SOURCES.                                *   FILE 914
//*                                                                 *   FILE 914
//*      THE DOCUMENTATION MEMBERS SUFFIXED WITH A 'P' I.E.         *   FILE 914
//*    SSMINSTP ARE PDF FORMAT DOCUMENTS.  TO USE THEM YOU WILL     *   FILE 914
//*    NEED TO TRANSFER THEM TO A PC USING YOUR FAVORITE FILE       *   FILE 914
//*    TRANSFER PROGRAM USING A BINARY OPTION - IE.  NO             *   FILE 914
//*    TRANSLATION.  YOU WILL PROBABLY NEED TO MAKE SURE THEY       *   FILE 914
//*    ARE TRANSFERRED TO A NEW FILE NAME THAT ENDS IN ".PDF",      *   FILE 914
//*    OR YOU MAY NOT BE ABLE TO READ THEM.                         *   FILE 914
//*                                                                 *   FILE 914
//*      IF YOU CAN NOT READ PDF DOCS THE ORIGINAL "WORD"           *   FILE 914
//*    FORMATTED DOCS ARE INCLUDED IN THE MEMBERS SUFFIXED WITH     *   FILE 914
//*    A "D" I.E. SSMINSTD.  YOU WILL NEED TO OFFLOAD THEM TO A     *   FILE 914
//*    PC FILE WITH A SUFFIX OF .DOC TO READ THEM PROPERLY.         *   FILE 914
//*                                                                 *   FILE 914
//*                                                                 *   FILE 914
//*       THE THREE BASIC PIECES OF DOCUMENTATION ARE -             *   FILE 914
//*                                                                 *   FILE 914
//*    1. THE INSTALLATION GUIDE - GIVES BACKGROUND,                *   FILE 914
//*       INSTALLATION INSTRUCTIONS, AND OTHER INFORMATION          *   FILE 914
//*       NEEDED TO SETUP THE SHARED SPOOL MODS PACKAGE.            *   FILE 914
//*                                                                 *   FILE 914
//*    2. THE USERS GUIDE - GIVES DETAILED INFO ON JECL             *   FILE 914
//*       STATEMENTS AND IS AIMED AT THE END USERS - WHOEVER        *   FILE 914
//*       CODES AND USES JCL.                                       *   FILE 914
//*                                                                 *   FILE 914
//*    3. THE OPERATIONS GUIDE - GIVES DETAILED INFORMATIN ABOUT    *   FILE 914
//*       ALL OF THE NEW JES2 DISPLAY AND MODIFY COMMANDS           *   FILE 914
//*       AVAIALABLE WITH THE PACKAGE.                              *   FILE 914
//*                                                                 *   FILE 914
//*      - - - - - - - - - - - - - - - - - - - - - - - - - - - -    *   FILE 914
//*                                                                 *   FILE 914
//*      Once you have the package set up - please drop me a        *   FILE 914
//*      line at:                                                   *   FILE 914
//*                                                                 *   FILE 914
//*          STEPHEN.MCCOLLEY@MVSPROGRAMMER.COM                     *   FILE 914
//*                                                                 *   FILE 914
//*      so that I can add you to the mailing list.  That way, I    *   FILE 914
//*      can let you know about bugs, fixes, and new releases       *   FILE 914
//*      as I make them avaialable.                                 *   FILE 914
//*                                                                 *   FILE 914
//*      IF YOU DROP ME YOUR REAL MAILING ADDRESS, I WILL SEND      *   FILE 914
//*      YOU A REAL "SHARED SPOOL MODS" COFFEE CUP - I STILL        *   FILE 914
//*      HAVE PLENTY OF THESE.                                      *   FILE 914
//*                                                                 *   FILE 914

```
