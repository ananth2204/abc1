```
//***FILE 888 is from Miklos Szigetvari and contains a package to   *   FILE 888
//*           give a very comprehensive display of z/OS system      *   FILE 888
//*           information which you can get via your Internet       *   FILE 888
//*           browser.  This package uses the z/OS system's HTTP    *   FILE 888
//*           server to put the information out on the Internet.    *   FILE 888
//*           It is really a first!  It is an excellent tool for    *   FILE 888
//*           modern-day sysprogs!                                  *   FILE 888
//*                                                                 *   FILE 888
//*           email:  miklos.szigetvari@isis-papyrus.com            *   FILE 888
//*                                                                 *   FILE 888
//*     Introduction                                                *   FILE 888
//*                                                                 *   FILE 888
//*     A very short introduction                                   *   FILE 888
//*                                                                 *   FILE 888
//*     Download from the PDS dataset the #DOCMP4 member and        *   FILE 888
//*     open as an MP4 video.                                       *   FILE 888
//*                                                                 *   FILE 888
//*     A longer introduction                                       *   FILE 888
//*                                                                 *   FILE 888
//*     For experienced and inexperienced host users, there is      *   FILE 888
//*     a demand to access different parts of the z/OS system       *   FILE 888
//*     via an interface:                                           *   FILE 888
//*                                                                 *   FILE 888
//*     - Easy to use, like a WEB browser.                          *   FILE 888
//*                                                                 *   FILE 888
//*     - Can add additional information, not or hardly             *   FILE 888
//*       available in z/OS.                                        *   FILE 888
//*                                                                 *   FILE 888
//*     - Can define simple operations (archive or compare etc.     *   FILE 888
//*       etc.)  Difficult to make on z/OS.                         *   FILE 888
//*                                                                 *   FILE 888
//*     I have tried to make a simple "in house" host explorer      *   FILE 888
//*       via the IBM z/OS HTTP Server and HTML sites.  The IBM     *   FILE 888
//*       HTTP Server (5.3) is part of the z/OS installation        *   FILE 888
//*       and contains a number of useful features (RACF            *   FILE 888
//*       authentication,REXX CGI support etc.).                    *   FILE 888
//*                                                                 *   FILE 888
//*     A collection of REXX CGI programs realize the different     *   FILE 888
//*     functions.                                                  *   FILE 888
//*                                                                 *   FILE 888
//*     I selected REXX because it is                               *   FILE 888
//*                                                                 *   FILE 888
//*     - Available everywhere                                      *   FILE 888
//*     - Contains a number of string manipulation functions        *   FILE 888
//*     - Easy to DEBUG or TRACE                                    *   FILE 888
//*                                                                 *   FILE 888
//*     The REXX CGI programs are calling the z/OS interface        *   FILE 888
//*     components.                                                 *   FILE 888
//*                                                                 *   FILE 888
//*     Some part is free available (as the SDSF REXX               *   FILE 888
//*      interface), some parts are installed from the CBT tape     *   FILE 888
//*      (as the MXI interface) and some parts are free to          *   FILE 888
//*      download from IBM:                                         *   FILE 888
//*     (as the SQL REXX interface or the MQ REXX interface)        *   FILE 888
//*     or from other source (WLM interface from YCOS software).    *   FILE 888
//*                                                                 *   FILE 888
//*     If there was no other interface,                            *   FILE 888
//*                                                                 *   FILE 888
//*     I wrote simple C/C++ programs to access these parts of      *   FILE 888
//*     the system:                                                 *   FILE 888
//*                                                                 *   FILE 888
//*     - Catalog information                                       *   FILE 888
//*     - Log streams                                               *   FILE 888
//*     - ISPF table etc.                                           *   FILE 888
//*                                                                 *   FILE 888
//*     The results are presented as dynamic HTML pages, with       *   FILE 888
//*     the Java scripts, available in the internet open source     *   FILE 888
//*     communities.                                                *   FILE 888
//*                                                                 *   FILE 888
//*     I'm using some browser plug-ins                             *   FILE 888
//*                                                                 *   FILE 888
//*     (Adobe Acrobat for PDF, ISIS AFP viewer for AFP or          *   FILE 888
//*     Notepad++) and links to the IBM "LookAt" or to the IBM      *   FILE 888
//*     Library Server.                                             *   FILE 888
//*                                                                 *   FILE 888
//*     I think the application is extendable in all directions.    *   FILE 888
//*                                                                 *   FILE 888
//*     It is connecting to, some part of the IBM software (RMF     *   FILE 888
//*     Data Portal), excellent to access from the WEB, but         *   FILE 888
//*     avoids example the CICS; as the IBM has the super CICS      *   FILE 888
//*     Explorer.                                                   *   FILE 888
//*                                                                 *   FILE 888
//*     Disclaimer !!                                               *   FILE 888
//*                                                                 *   FILE 888
//*     This is not a replacement for TSO or SDSF ISPF or any       *   FILE 888
//*     other IBM or non-IBM product.  We are using this at         *   FILE 888
//*     ISIS Papyrus Software for a while, with a small number      *   FILE 888
//*     of users.  It has never been intensively tested for         *   FILE 888
//*     performance or security.                                    *   FILE 888
//*                                                                 *   FILE 888
//*     Miklos Szigetvari                                           *   FILE 888
//*     Januar 2013                                                 *   FILE 888
//*     <miklos.szigetvari@isis-papyrus.com>                        *   FILE 888
//*                                                                 *   FILE 888

```
