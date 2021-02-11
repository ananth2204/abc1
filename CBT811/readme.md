```
//***FILE 811 is a very useful LIBRARIAN program package, and       *   FILE 811
//*           which is completely new at this time (Mar/06). The    *   FILE 811
//*           package was written by Richard L. Rice.  This is a    *   FILE 811
//*           fixed version of the LIBRARIAN program that was on    *   FILE 811
//*           File 711.                                             *   FILE 811
//*                                                                 *   FILE 811
//*   >>> --------------------------------------------------------  *   FILE 811
//*   >>> This LIBRARIAN is a free package, unrelated to any other  *   FILE 811
//*   >>> package having the same or a similar name......           *   FILE 811
//*   >>> --------------------------------------------------------  *   FILE 811
//*                                                                 *   FILE 811
//*           email:  Richard.L.Rice@conocophillips.com             *   FILE 811
//*                                                                 *   FILE 811
//*   Some documentation for this utility follows:                  *   FILE 811
//*                                                                 *   FILE 811
//*     The LIBRARIAN is a VTAM LU 6.2 client-server type           *   FILE 811
//*     application, and it can also be accessed using TCP/IP.      *   FILE 811
//*                                                                 *   FILE 811
//*     My idea for using an LU 6.2 interface was to allow          *   FILE 811
//*     users to access a library without having to log-in to       *   FILE 811
//*     the system where the library actually lives.  You could     *   FILE 811
//*     have a system at a central location serving remote          *   FILE 811
//*     offices.  If you have multiple LPARs, users can access      *   FILE 811
//*     libraries on any of the LPARs while logged in to only       *   FILE 811
//*     one of the LPARs.                                           *   FILE 811
//*                                                                 *   FILE 811
//*     Since you have PDSs (libraries) on MVS already, what do     *   FILE 811
//*     I need a librarian for?  The LIBRARIAN prevents             *   FILE 811
//*     multiple users from updating a member at the same time.     *   FILE 811
//*     When a user wants to update a member of a library, they     *   FILE 811
//*     "CHECK OUT" the member.  The LIBRARIAN updates the          *   FILE 811
//*     status to reflect the status is "CHECKED OUT" and           *   FILE 811
//*     records the time, date, and user id of who CHECKED OUT      *   FILE 811
//*     the member.  While the member is in CHECKED OUT state,      *   FILE 811
//*     others will not be allowed to CHECK OUT the same            *   FILE 811
//*     member.  Only the user that CHECKED out the member may      *   FILE 811
//*     CHECK IN that member.  When the member is CHECKED IN,       *   FILE 811
//*     the LIBRARIAN will change the status to CHECKED IN and      *   FILE 811
//*     record the time, date, and user id of the user that         *   FILE 811
//*     performed the CHECK IN.  A member may be VIEWed at any      *   FILE 811
//*     time.  VIEWing a member does not change the STATUS or       *   FILE 811
//*     the CHECK IN or CHECK OUT time stamps.                      *   FILE 811
//*                                                                 *   FILE 811
//*     Access to members is controlled via a user exit             *   FILE 811
//*     (LIBUX02).  You may over-ride standard access controls.     *   FILE 811
//*     For example, it may be that a user that has a member        *   FILE 811
//*     CHECKED OUT is on vacation or no long working for your      *   FILE 811
//*     company.  You may want to allow a manager to CHECK IN       *   FILE 811
//*     the member.                                                 *   FILE 811
//*                                                                 *   FILE 811
//*     The server or back-end can be run as a JOB or started       *   FILE 811
//*     task (STC).  Users may interface with the LIBRARIAN         *   FILE 811
//*     either though batch or an SPF dialog.                       *   FILE 811
//*                                                                 *   FILE 811
//*     The LIBRARIAN can manage multiple libraries.  This          *   FILE 811
//*     allows one LIBRARIAN to manage SOURCE, MACRO, JCL, etc      *   FILE 811
//*     libraries.                                                  *   FILE 811
//*                                                                 *   FILE 811
//*     Libraries are KSDS VSAM clusters.                           *   FILE 811
//*                                                                 *   FILE 811
//*     Members in the library may be stored in a compressed        *   FILE 811
//*     form.  User exit LIBUX01 allows you to use the              *   FILE 811
//*     LIBRARIAN supplied compression, use a compression           *   FILE 811
//*     method of your own, or turn compression off.  The           *   FILE 811
//*     librarian compression mechanism averages about a 4-to-1     *   FILE 811
//*     compression ratio.                                          *   FILE 811
//*                                                                 *   FILE 811
//*     This version of the LIBRARIAN allows you to add up to 5     *   FILE 811
//*     lines of comments about a member for documentation.         *   FILE 811
//*     These comments are not considered a part of the member      *   FILE 811
//*     itself.                                                     *   FILE 811
//*                                                                 *   FILE 811
//*     The LIBRARIAN allows for up to 32,767 versions of a         *   FILE 811
//*     given member.                                               *   FILE 811
//*                                                                 *   FILE 811
//*     The VSAM key used in the KSDSs allow approximately 2        *   FILE 811
//*     billion (a 4 byte binary field) blocks of source data.      *   FILE 811
//*     Each block is up to 8K in size.  If data compression is     *   FILE 811
//*     used, the blocks contain compressed data.  The amount       *   FILE 811
//*     of data that can be stored in a library is usually          *   FILE 811
//*     limited only by the amount of disk space available.         *   FILE 811
//*                                                                 *   FILE 811
//*     Several supporting utilities are also supplied.             *   FILE 811
//*       .  LIBINIT     Initializes a new library.                 *   FILE 811
//*       .  UTIL0001    Loads members to a library "offline"       *   FILE 811
//*       .  UTIL0002    Unloads a library to a sequential file     *   FILE 811
//*       .  UTIL0003    Converts a source file to compressed form  *   FILE 811
//*       .  UTIL0004    Detail library status report.              *   FILE 811
//*       .  UTIL0005    Unloads members to a sequential file in    *   FILE 811
//*                      LIBRARIAN "export" format                  *   FILE 811
//*       .  UTIL0006    Imports members from a sequential file     *   FILE 811
//*                      in LIBRARIAN "export" format               *   FILE 811
//*                                                                 *   FILE 811

```
