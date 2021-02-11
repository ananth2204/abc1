```
//***FILE 729 is from Rob Wunderlich and contains his MAXITRAN      *   FILE 729
//*           REXX that helps to run batch FTP between an MVS       *   FILE 729
//*           client and another FTP server.                        *   FILE 729
//*                                                                 *   FILE 729
//*           email:  RobWunderlich@ussposco.com                    *   FILE 729
//*                                                                 *   FILE 729
//*     Description:                                                *   FILE 729
//*                                                                 *   FILE 729
//*     The MAXITRAN exec is used to script batch FTP between       *   FILE 729
//*     an MVS client and another FTP server.  It provides          *   FILE 729
//*     functions such as delete of source files after GET          *   FILE 729
//*     (delete is the default!).  Read the doc "maxitran.doc"      *   FILE 729
//*     for complete documentation.  (MSWORD format member          *   FILE 729
//*     MAXITRA@).                                                  *   FILE 729
//*                                                                 *   FILE 729
//*     This software is distributed into the public domain         *   FILE 729
//*     "as-is" by Rob Wunderlich.                                  *   FILE 729
//*                                                                 *   FILE 729
//*     To execute maxitran, copy the member "PROC" to a            *   FILE 729
//*     proclib (or JCLLIB) as member "MAXITRAN".  Update the       *   FILE 729
//*     SYSPROC DD stmt to point to this PDS.                       *   FILE 729
//*                                                                 *   FILE 729
//*     Customizations required before you use this at your         *   FILE 729
//*     site:                                                       *   FILE 729
//*                                                                 *   FILE 729
//*     -- Member MAXITRAN --                                       *   FILE 729
//*     1)The shipped default is "GETDELETE YES" which means        *   FILE 729
//*     files will be deleted from the server after a               *   FILE 729
//*     sucessfull GET.  If you want to change the default for      *   FILE 729
//*     your shop, change the line                                  *   FILE 729
//*       flagGetDelete=1                                           *   FILE 729
//*     to                                                          *   FILE 729
//*       flagGetDelete=0                                           *   FILE 729
//*                                                                 *   FILE 729
//*     2)If you use the email feature, you might want to           *   FILE 729
//*     update subroutine "sendmail" to use "HELO" and "FROM"       *   FILE 729
//*     values that are meaningful for your site.                   *   FILE 729
//*                                                                 *   FILE 729
//*     The email routine expects that you have an MVS              *   FILE 729
//*     SMTP server set up named "SMTP" that services output        *   FILE 729
//*     class B.                                                    *   FILE 729
//*                                                                 *   FILE 729

```
