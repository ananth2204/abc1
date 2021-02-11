```
//***FILE 714 is from Bob Styma and contains a set of programs      *   FILE 714
//*           to enable an MVS system that is running under         *   FILE 714
//*           FLEX-ES to issue flexes commands to the Linux         *   FILE 714
//*           system it is running on.                              *   FILE 714
//*                                                                 *   FILE 714
//*        If you have any questions, feel free to contact me:      *   FILE 714
//*                                                                 *   FILE 714
//*        Robert Styma    stymar@lucent.com,   styma@swlink.net    *   FILE 714
//*                                                                 *   FILE 714
//*     Normal disclaimer, this program is provided free of         *   FILE 714
//*     charge and no warranty is made as to its fitness for        *   FILE 714
//*     any particular purpose.  The author assumes no              *   FILE 714
//*     liability resulting from the use or misuse of these         *   FILE 714
//*     programs.                                                   *   FILE 714
//*                                                                 *   FILE 714
//*     This distribution contains 3 parts.                         *   FILE 714
//*                                                                 *   FILE 714
//*     1.  $$NOTE1 - general description of the package            *   FILE 714
//*                                                                 *   FILE 714
//*     2.  The MVS side of the program -                           *   FILE 714
//*                                                                 *   FILE 714
//*          Note:  This consists of members:                       *   FILE 714
//*           $COMPILE $SAMPOUT $SAMPRUN ASMSRC COS001A             *   FILE 714
//*           COS001B  DSSDUMP  LINKDATE PLISRC                     *   FILE 714
//*                                                                 *   FILE 714
//*     3.  TAR     - (download this to the Linux side of the       *   FILE 714
//*                    FLEX-ES system and un-tar it there.)         *   FILE 714
//*                                                                 *   FILE 714
//*        flexescli_inetd.tar  - The unix (linux) side of the      *   FILE 714
//*                     program designed to run under xinetd.       *   FILE 714
//*                     The comments at the beginning of            *   FILE 714
//*                     flexescli_inetd.c describe how to set       *   FILE 714
//*                     the program up for use with xinetd.         *   FILE 714
//*                                                                 *   FILE 714
//*     General program description:                                *   FILE 714
//*                                                                 *   FILE 714
//*        Note:  The flexescli_inetd program, by way of xinetd     *   FILE 714
//*        is listening on a port.  The MVS side of the program     *   FILE 714
//*        will contact the flexescli_inetd program using the       *   FILE 714
//*        IP address of the UNIX side of the system and the        *   FILE 714
//*        port.  The MVS side has the port 19999 coded into it     *   FILE 714
//*        as a default although it can be overridden with the      *   FILE 714
//*        port= parameter to the main parm string.                 *   FILE 714
//*                                                                 *   FILE 714
//*        The port on the Unix side is specified in                *   FILE 714
//*        /etc/services.  The update to /etc/services is shown     *   FILE 714
//*        in flexescli_inetd.c using the port 19999.  You may      *   FILE 714
//*        wish to use a different port.  If you use a              *   FILE 714
//*        different port, update the MVS program (member           *   FILE 714
//*        PLISRC) to reflect the new port.  You will probably      *   FILE 714
//*        update it to change the default IP address to the        *   FILE 714
//*        correct value on your system.                            *   FILE 714
//*                                                                 *   FILE 714

```
