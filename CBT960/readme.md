```
//***FILE 960 is from Al Ferguson and contains many REXX execs      *   FILE 960
//*           with their accompanying techniques, to get a large    *   FILE 960
//*           variety of jobs done.                                 *   FILE 960
//*                                                                 *   FILE 960
//*           email:  Al.Ferguson@sccompanies.com                   *   FILE 960
//*                                                                 *   FILE 960
//*     Description of File Contents:                               *   FILE 960
//*                                                                 *   FILE 960
//*                  REXXes using Various APIs                      *   FILE 960
//*                                                                 *   FILE 960
//*     See $INSTALL member on how to install these and make        *   FILE 960
//*     them available.                                             *   FILE 960
//*                                                                 *   FILE 960
//*     Most of ideas (and some of the code) included here are a    *   FILE 960
//*     combination of needing to solve a problem for work,         *   FILE 960
//*     curiosity in how things work, and inspiration for others    *   FILE 960
//*     (both their ideas and their code).  Much of the code I      *   FILE 960
//*     have got inspiration from can be found on CBTTape.org.      *   FILE 960
//*                                                                 *   FILE 960
//*     Why did I implement these solution in REXX?  It             *   FILE 960
//*     interfaces with almost every sub-system on zOS, has a       *   FILE 960
//*     huge number of capabilities/APIs, and is easily             *   FILE 960
//*     extensible.  Most of my solutions use REXX & JCL to         *   FILE 960
//*     extend the capabilities of the sub-systems I already have   *   FILE 960
//*     access to, to fill in a missing piece of the automation     *   FILE 960
//*     puzzle (Programs & Batch JOBs ARE Automation).              *   FILE 960
//*                                                                 *   FILE 960
//*     Did you know that ...                                       *   FILE 960
//*       - IBM Provides a REXX STEM SORT function?                 *   FILE 960
//*         See EXEC(TSOVSORT) ...                                  *   FILE 960
//*       - IBM Provides REXX with Regex Support?                   *   FILE 960
//*         See EXEC(CHECKJOB) ...                                  *   FILE 960
//*       - You can allocate a GDG using (+1), (-1), or (-0) in     *   FILE 960
//*         a REXX?                                                 *   FILE 960
//*         See EXEC(GDGCOPY) ...                                   *   FILE 960
//*       - You can allocate a DSN without TSO support?             *   FILE 960
//*         See EXEC(GDGCOPY) EXEC(STARTUP) EXEC(UMODCHCK) ...      *   FILE 960
//*       - You can read a PDS or PDS/E Directory under MVS         *   FILE 960
//*         (IRXJCL)?                                               *   FILE 960
//*         See EXEC(GDGCOPY) ...                                   *   FILE 960
//*       - You can "efficently" get DSN Information under MVS      *   FILE 960
//*         (IRXJCL)?                                               *   FILE 960
//*         See EXEC(DSLIST) EXEC(VSAMRD) EXEC(VSAMRDEF) ...        *   FILE 960
//*       - MVS knows your Name?                                    *   FILE 960
//*         See EXEC(ACEENAME) ...                                  *   FILE 960
//*       - You can analyze the results of your JOBs & SYSOUTs?     *   FILE 960
//*         See EXEC(CHECKJOB) & EXEC(GETSYSOT) ...                 *   FILE 960
//*       - You can do Full Screen ISPF Point & Shoot in a REXX?    *   FILE 960
//*         See EXEC(BR) EXEC(DSNS) EXEC(ED) EXEC(ML) EXEC(MU)      *   FILE 960
//*         EXEC(VW) ...                                            *   FILE 960
//*       - You have access to USS Unix Man pages from ISPF?        *   FILE 960
//*         See EXEC(MAN) ...                                       *   FILE 960
//*       - You can do RFC Complient email within REXX via TCPIP?   *   FILE 960
//*         See EXEC(SENDMAIL) ...                                  *   FILE 960
//*       - You can do email just like they do on any other         *   FILE 960
//*         Unix Box?                                               *   FILE 960
//*         See EXEC(USSMAIL) ...                                   *   FILE 960
//*       - You can have ISPF (zOS 2.2+) automatically setup        *   FILE 960
//*         your session?                                           *   FILE 960
//*         See EXEC(ZSTART) ...                                    *   FILE 960
//*       - Do you need to know what day of the week June 2,        *   FILE 960
//*         1975 was?                                               *   FILE 960
//*         See EXEC(DATEX) ...                                     *   FILE 960
//*       - You can ask DB2 for Help "Drawing" a Table Select?      *   FILE 960
//*         See EXEC(DB2DRAW) ...                                   *   FILE 960
//*       - You can interface with SMS to find a DSNs last backup?  *   FILE 960
//*         See EXEC(HRECV) ...                                     *   FILE 960
//*                                                                 *   FILE 960
//*                                                                 *   FILE 960

```
