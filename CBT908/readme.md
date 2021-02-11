```
//***FILE 908 is from James Halley and contains a package to send   *   FILE 908
//*           ISPF outputs to Windows workstations for printing     *   FILE 908
//*           and many types of further post-processing.  A short   *   FILE 908
//*           description follows below.  You should also see the   *   FILE 908
//*           pds member called $README.                            *   FILE 908
//*                                                                 *   FILE 908
//*           email:  jimhalley627@gmail.com                        *   FILE 908
//*                                                                 *   FILE 908
//*       ISPF Client Server Local Dialogs and Facilities           *   FILE 908
//*       ---- ------ ------ ----- ------- --- ----------           *   FILE 908
//*                                                                 *   FILE 908
//*     This library contains ISPF components that make it          *   FILE 908
//*     easier to move files and reports between a batch or         *   FILE 908
//*     online ISPF session and a Microsoft Windows workstation     *   FILE 908
//*     running the ISPF Workstation Agent (WSA).                   *   FILE 908
//*                                                                 *   FILE 908
//*     These tools are intended for non-productional use and       *   FILE 908
//*     may not be suitable for or function in your                 *   FILE 908
//*     environment.  Communication between a mainframe ISPF        *   FILE 908
//*     session and an ISPF Workstation Agent through an IP         *   FILE 908
//*     connection is required but can be prevented by network      *   FILE 908
//*     (e.g. firewall and communication port) settings.            *   FILE 908
//*     Contact a member of your network support team if a          *   FILE 908
//*     connection between your ISPF session and a Workstation      *   FILE 908
//*     Agent cannot be established.                                *   FILE 908
//*                                                                 *   FILE 908
//*     The ISPF Workstation Agent "Windows 2000/NT" install        *   FILE 908
//*     executable prior to z/OS 2.1 is not compatible with         *   FILE 908
//*     Microsoft Windows 7 unless z/OS APAR OA39571 has been       *   FILE 908
//*     implemented:                                                *   FILE 908
//*     http://www-01.ibm.com/support/docview.wss?uid=isg1OA39571   *   FILE 908
//*                                                                 *   FILE 908
//*     To use ISPF Client Server with Windows 7 if your z/OS       *   FILE 908
//*     version is below 2.1 and APAR OA39571 has not been          *   FILE 908
//*     applied:                                                    *   FILE 908
//*                                                                 *   FILE 908
//*       *  Upgrade z/OS to Version 2.1                            *   FILE 908
//*       *  or Apply APAR OA39571                                  *   FILE 908
//*       *  or obtain the Windows 7 compatible install             *   FILE 908
//*          executable for the Workstation Agent from IBM.         *   FILE 908
//*       *  or copy the five critical WSA components from a        *   FILE 908
//*          workstation running Windows XP or below.  (The         *   FILE 908
//*          least acceptable option.)                              *   FILE 908
//*       *  or download member ISPFINST from this library and      *   FILE 908
//*          unzip the content which is the Workstation Agent       *   FILE 908
//*          install file that came with APAR OA39571.              *   FILE 908
//*                                                                 *   FILE 908
//*     Constraints of copying the five WSA components from a       *   FILE 908
//*     WinXP to Win7:                                              *   FILE 908
//*                                                                 *   FILE 908
//*       *  Older versons of the WSA sometimes do not find or      *   FILE 908
//*          use Windows Socket Library components even when        *   FILE 908
//*          the path is manually entered in the WSA "Set           *   FILE 908
//*          Winsock Path" dialog.                                  *   FILE 908
//*       *  The older WSA had other issues that were resolved      *   FILE 908
//*          by APAR 0A39571 including abending after               *   FILE 908
//*          tranferring 1.5 GB of a large text file.               *   FILE 908
//*                                                                 *   FILE 908
//*     The WSA supplied by APAR OA39571 has been successfully      *   FILE 908
//*     tested on a z/OS 1.13 system on which APAR 0A39571 has      *   FILE 908
//*     not implemented.                                            *   FILE 908
//*                                                                 *   FILE 908
//*     This library contains a number of module types: CLIST,      *   FILE 908
//*     REXX; ISPF panel, skeleton and message; MVS procedure       *   FILE 908
//*     and JCL, Microsoft Word, zipped Microsoft Windows           *   FILE 908
//*     executable.                                                 *   FILE 908
//*                                                                 *   FILE 908
//*     The $README member describes the type and purpose of        *   FILE 908
//*     each member in this library to assist in moving             *   FILE 908
//*     members to libraries of the appropriate types.              *   FILE 908
//*                                                                 *   FILE 908
//*     The three "MVS batch" batch components must be renamed      *   FILE 908
//*     when moved to the libraries from which they will be         *   FILE 908
//*     used.  Components associated with ISPF dialogs can be       *   FILE 908
//*     used as named.                                              *   FILE 908
//*                                                                 *   FILE 908

```
