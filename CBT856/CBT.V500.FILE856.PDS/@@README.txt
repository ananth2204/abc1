

                   SSSS H   H  AAA  RRRR  EEEEE DDDD
                  S     H   H A   A R   R E     D   D
                   SSS  HHHHH AAAAA RRRR  EEEE  D   D
                      S H   H A   A R  R  E     D   D
                  SSSS  H   H A   A R   R EEEEE DDDD

                      SSSS PPPP   OOO   OOO  L
                     S     P   P O   O O   O L
                      SSS  PPPP  O   O O   O L
                         S P     O   O O   O L
                     SSSS  P      OOO   OOO  LLLLL

                        M   M  OOO  DDDD   SSSS
                        MM MM O   O D   D S
                        M M M O   O D   D  SSS
                        M   M O   O D   D     S
                        M   M  OOO  DDDD  SSSS

                       for jes2 1.10, 1.11 and 1.12
                               and 1.13

  DISCLAIMER -

***********************************************************************
*                                                                     *
*     THE MODS ON THIS TAPE HAVE BEEN USED SUCCESSFULLY AND TO THE    *
*  BEST OF OUR KNOWLEDGE THEY ARE OPERATIONAL, HOWEVER NO WARRANTY IS *
*  MADE TO THE ACCURACY OF THE MODS AND NO RESPONSIBILITY IS ASSUMED  *
*  FOR ANY MODIFICATION DIRECTLY OR INDIRECTLY CAUSED BY THE USE OF   *
*  THE MODIFICATIONS.  IT IS THE USERS RESPONSIBILITY TO EVALUATE THE *
*  USEFULLNESS OF THE MATERIAL.                                       *
*                                                                     *
*     WE DO NOT GUARANTEE TO KEEP ANY MATERIAL PROVIDED UP TO DATE,   *
*  NOR DO WE GUARANTEE TO PROVIDE ANY CORRECTIONS OR EXTENSIONS MADE  *
*  IN THE FUTURE.                                                     *
*                                                                     *
***********************************************************************


  This is the installation PDS for the Shared Spool Mods for JES2
 1.10, 1.11, 1.12 and JES2 1.13.  The shared spool mods were formerly
 known as the Mellon shared spool mods.

   All who use the shared spool mods, owe a debt of gratitude to Mellon
 Bank for the original implementaion of the shared spool mods, but
 because it has been maintained outside of Mellon for over 15 years,
 and has been rewritten twice since then, we will refer to the mods
 as the SHARED SPOOL MODS from now on.  Once again -
                      THANK YOU MELLON BANK !



  In this PDS you should find the following members.


                ( ADMINISTRATIVE MEMBERS )
@@README -   That is this member, you are reading it.

DISCLAIM -   Our standard disclaimer - we guarentee / warrent nothing!



            ( DOCUMENTATION - PDF AND DOC FORMAT MANUALS )
SSMINSTP -   Shared Spool Mods installation manual - PDF format
             (simply download to your PC as ssminst.pdf - binary xfer)

SSMINSTW -   Shared Spool Mods installation manual - Word Document
             (simply download to your PC as ssminst.doc - binary xfer)

SSMUSERP -   Shared Spool Mods Users Guide - PDF format
             (simply download to your PC as ssmuser.pdf - binary xfer)

SSMUSERW -   Shared Spool Mods Users Buide - Word Document
             (simply download to your PC as ssmuser.doc - binary xfer)

SSMOPSGP -   Shared Spool Mods Operations Guide - PDF format
             (simply download to your PC as ssmopsg.pdf - binary xfer)

SSMOPSGW -   Shared Spool Mods Operations Guide - Word Document
             (simply download to your PC as ssmopsg.doc - binary xfer)


               ( SMP INSTALLATION MEMBERS )
LSES500  -   The SMP/e usermod needed to install the entire package.

LSES500J -   Sample JCL to run the RECEIVE / APPLY Check / APPLY
    (You must apply lses500 or use the non-smp install method).



             ( NON-SMP INSTALLATION MEMBERS )
ALOCLIBS -  NON-SMP STEP 1 - ALLOCATE NEW LIBRARIES.

COPYLIBS -  NON-SMP STEP 3 - POPULATE NEW LIBRARIES.


             ( COMMON JES2 PARMS NEEDED FOR PACKAGE )
JES2PARM -   SAMPLE JES2 PARMS NEEDED TO IMPLEMENT THE PACKAGE.



*** THEN WE HAVE THE FOLLOWING FOUR MEMBERS - THEY ARE NOT REALLY PART OF
*** THE SHARED SPOOL MODS - BUT WE HAVE BEEN DISTRIBUTING THEM, AND SOME
*** FOLKS STILL NEED THEM.  IF YOU WANT TO USE THESE, YOU WILL HAVE TO
*** APPLY THEM SEPERATELY FROM THE SHARED SPOOL MODS - WE JUST HAVE THE
*** SOURCE - THEY ARE NOT SETUP AS USERMODS.


STSCX01A -   OUR VERSION OF THE PAGE SEPERATOR EXIT. (NOT PART OF SSM'S)

STSCX05B -   PREVENT PURGING BY JOB RANGE. (NOT PART OF SSM'S)

STSCX15A -   CAUSES FCBS TO BE RELOAD WITH EACH JOB UNLESS STD FORMS.

STSCX36A -   SAF PROCESSING FOR JOBS COMING IN FROM RJE/NJE SOURCES.


  THE DOCUMENTATION MEMBERS SUFFIXED WITH A 'P' I.E. SSMINSTP ARE PDF
FORMAT DOCUMENTS.  TO USE THEM YOU WILL NEED TO TRANSFER THEM TO A PC
USING YOUR FAVORITE FILE TRANSFER PROGRAM USING A BINARY OPTION - IE.
NO TRANSLATION.  YOU WILL PROBABLY NEED TO MAKE SURE THEY ARE
TRANSFERRED TO A NEW FILE NAME THAT ENDS IN ".PDF", OR YOU MAY NOT BE
ABLE TO READ THEM.

  IF YOU CAN NOT READ PDF DOCS THE ORIGINAL "WORD" FORMATTED DOCS
ARE INCLUDED IN THE MEMBERS SUFFIXED WITH A "W" I.E. SSMINSTW.  YOU
WILL PROBABLY NEED TO OFFLOAD THEM TO A PC FILE WITH A SUFFIX OF DOC
TO READ THEM PROPERLY.


  THE THREE BASIC PIECES OF DOCUMENTATION ARE -

1 THE INSTALLATION GUIDE - GIVES BACKGROUND, INSTALLATION INSTRUCTIONS,
  AND OTHER INFORMATION NEEDED TO SETUP THE SHARED SPOOL MODS PACKAGE.

2 THE USERS GUIDE - GIVES DETAILED INFO ON JECL STATEMENTS AND IS AIMED
  AT THE END USERS - WHOEVER CODES AND USES JCL.

3 THE OPERATIONS GUIDE - GIVES DETAILED INFORMATIN ABOUT ALL OF THE
  NEW JES2 DISPLAY AND MODIFY COMMANDS AVAIALABLE WITH THE PACKAGE.



  ONCE YOU HAVE THE PACKAGE SETUP - PLEASE DROP ME A LINE AT
   SGMCCOLLEY@ALLTEL.NET  OR STEPHEN.MCCOLLEY@MVSPROGRAMMER.COM SO THAT
  I CAN ADD YOU TO THE MAILING LIST.  THAT WAY I CAN LET YOU KNOW ABOUT
  BUGS, FIXES, AND NEW RELEASES AS I MAKE THE AVAIALABLE.

  IF YOU DROP ME YOUR REAL MAILING ADDRESS, I WILL SEND YOU A REAL
  "SHARED SPOOL MODS" COFFEE CUP - I STILL HAVE PLENTY OF THESE.

** END OF DOC **
