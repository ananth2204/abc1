
## $CACHDOC.txt
```
Chuck Baumann  Mail Stop 139      phone: (408) 746-4784
Amdahl                            email: CEB40@AMAIL.AMDAHL.COM
1250 E Arques Ave
Sunnyvale, California  94088-3470
-----------------------------------------------------------------------
                      Cacheman (Amdahl Cache Utility)

This document contains a description of the tool Cacheman, a brief
history of the product,  a sample of the ISPF panels and output from
an actual session, and the instructions for installing on a host MVS
system.

Description:  Cacheman is a software tool that allows the user to
display the cacheing status of DASD controllers and devices connected to
cached controllers.  This dialog is much easier to use than the ISMF
panels but is NOT a replacement for ISMF.  The dialog features a user
customizable options panel, logging, and field level help.

Cacheman is an ISPF dialog that formats the output from the LISTDATA and
SETCACHE commands and displays the results in a tabular format.  The
status of devices and controllers can be easily monitored and modified
from these panels.  An options panel allows the user to easily 'tailor'
certain aspects of this dialog.  Help panels and field level help are
both available in this dialog. It will work for 3990, 3880-11,13,21,23,
and 3rd party 3990 compatible controllers (Amdahl, Hitachi, EMC, etc)

Cacheman is coded in TSO/E REXX.  There are three small assembler
routines which scan the UCB chains and return information. No modules
require APF authorization. RACF or ACF/2 authorizations will be required
to allow users to issue the LISTDATA and SETCACHE commands.

The user can select which controllers/dasd will be displayed on the
output panel by either a partial or complete volser name or by an
address range.  The output panel for controllers will display the
controller model, subsystem ID, amount of subsystem storage, amount
available, amount of NVS storage, amount NVS available, subsystem
status, CFW status, NVS status and indicators for offline memory and
pinned tracks. The user can modify the subsystem status field, the SD
Cache status field, and the NVS status field by typing over the
displayed value with a new value.  An '=' in the action field of other
controllers will replicate the same status changes for those controllers

The output panel for dasd devices will display the unit address, volser,
device model, cache status and DFW status, indicators for pinned tracks
and whether this volume is duplexed, and actual statuses for cache, NVS,
and CFW.  The actual status is a combination of device status and
controller status. The user can modify the cache and DFW status fields
by typing over the displayed value.  An '=' in the action field of other
devices will replicate the same status changes for those devices.

The options panel allows users to set flags to:
  View results of all SETCACHE commands in a popup window
  Display a confirmation window prior to executing a SETCACHE command
  Enable/disable command logging
  State which PFKEY to use for refreshing panel status.
In addition each user can identify which characters to use for the
valid actions on the controller and device panels.  If color terminals
are being used the color of certain fields may be specified on this
panel. The option settings will be saved in the users profile.


History:

Cacheman is a result of Product Certifications need for a method to
monitor and control Cache status of controllers and devices that was
more user friendly than using the ISMF panels and more productive
than using native TSO LISTDATA and SETCACHE commands.  The tool was
developed during the certification of the R49 microcode for 6100 dasd
controllers by Chuck Baumann (SPA) in his spare time. Since it was
made available to Amdahl customers it has been downloaded by over
200 different individuals worldwide.

Version 1.0 was the original prototype used by Cert.

Version 1.1 included better error handling and integrated suggestions
received from Product Certification. It was made available to the field
via AMTAG in February 1994.

Version 1.2 corrected some minor problems for displaying values received
from 3880 controllers and added the device model number as a new field
on the device panel.  It was made available via AMTAG in June 1994.

Version 1.2a corrected problems with the duplex logic and problems with
3880 device reporting. It was made available on AMTAG in July 1994.

Version 1.3  improved the error handling, changed the method used to
report pinned tracks, and moved the model lookup table from the assembler
module to the exec to allow users to add devices with new capacities.
It was made available via AMTAG in September 1994.

Version 2.0  now adds the capability to monitor cache performance in
foreground or background without the need of Cache RMF Reporter.  It
displays information in a format similar to the reports from the IBM
program product Cache RMF Reporter.
It was made available via AMTAG in November  1994.

Version 2.1 and 2.2 corrected problems with REXX interpreting certain
strings as exponential notation rather than hex strings and a few other
coding problems.  The DEVTYPE module was also changed to return certain
error information to the Cachemn1 exec.
It was made available via AMTAG in January  1995.

Version 2.3 extends the Hits option to the device level.  A SMF exit is
now supplied with Cacheman. It is IEFU84 which will write WTO messages
to the console and syslog describing the 3990 state changes as they
occur. This exit is optional and not required by Cacheman.
Cacheman now has a command which will display a grid of all controllers
and devices with their current caching status for a quick overall view.
Cacheman now logs information about calls to DEVTYPE.

Version 2.4 adds the SORT command to reorder screens using different
fields as the sort key.  It also changes the method used for
determining device models.  It will now disable logging if the log
data fills up (B37 abend) to avoid error messages coming to the users
terminal.

(The following panels are ONLY a subset of all the panels in this
 application.  They are the most commonly used panels.)

Selection Panel:

================================================================================
| -------------------------- AMDAHL CACHE UTILITY V2.4 ------------------------|
| COMMAND INPUT ===>                                           SCROLL ===> CSR |
|                    _                                                         |
|                                                                              |
|                  DEVICE SELECTION BY VOLSER OR BY UNIT ADDRESS               |
|                                                                              |
|  The output table will contain a list of caching controllers for devices     |
|  selected by naming a partial or complete VOLSER or by specifying a          |
|  range of addresses.  You cannot specify both VOLSER and Unit Address.       |
|                                                                              |
|            Volume: *_____      (* will include all volumes)                  |
|                                                                              |
|                     or                                                       |
|                                                                              |
|      Unit Address: ___   to  ___    (both values are required)               |
|                                                                              |
|                     or                                                       |
|   Select by group: _______     (select one from the groups listed below)     |
|  BIGCACH   GROUPA      SCNDSHF    THRDSH                                     |
|                                                                              |
|                                                                              |
|                                                                              |
|                                                                              |
|                                                                              |
================================================================================


Controller panel:

================================================================================
| -------------------------- AMDAHL CACHE UTILITY V2.4 --------  ROW 1 TO 6 OF |
| COMMAND INPUT ===>                                           SCROLL ===> CSR |
|                    _                                                         |
|                                                                              |
|  I =STATUS  C =COUNTS  S =DEVICES  P =PINNED  U =DESTAGE  H =HITS  M =MEMBER |
|  Enter 'OPT' in command input to update user options.                        |
|   --------------------- Storage Controller Panel ------------ Refresh = PF 16|
|   Ctlr     Unit         -Subsystem-  --NVS--  Subsys  SD          Pinned Off |
|   Model    Addr  SSID    Stg  Avail  Stg Avl  Cache  Cache    NVS Exists Mem |
| -----------------------------------------------------------------------------|
| _ 3990-03  140   00F8   128M   128M   4M N/A  ON    CFW ON    DIS     NO  NO |
| _ 3990-03  244   00D8    64M    64M   4M N/A  ON    CFW ON    DIS     NO  NO |
| _ 3990-03  340   00D0    64M    64M   4M N/A  ON    CFW DIS   DIS     NO  NO |
| _ 3990-03  740   0098   128M   128M   4M N/A  ON    CFW ON    ON      NO  NO |
| _ 3990-03  D40   0038   512M   512M   4M N/A  ON    CFW ON    DIS     NO  NO |
| _ 3990-03  E40   00A8   128M   128M   4M N/A  ON    CFW ON    DIS     NO  NO |
| ******************************* BOTTOM OF DATA ******************************|
|                                                                              |
|                                                                              |
|                                                                              |
|                                                                              |
|                                                                              |
|                                                                              |
|                                                                              |
|                                                                              |
================================================================================


Device panel:
================================================================================
|  ------------------------- AMDAHL CACHE UTILITY V2.4 -----  ROW 16 TO 30 OF 3|
|  COMMAND INPUT ===>                                          SCROLL ===> CSR |
|                     _                                                        |
|                                                                              |
|    C = COUNTS    P = PINNED   S = STATUS    D =Duplex operations    H = Hits |
|   Enter 'OPT' in command input to update user options.                       |
|    ------------------DASD Device Panel ---------------------- Refresh = PF 16|
|                 ----- Hardware Status ------                  Actual Status  |
|    Dev  Volser  Model  Cache  DFW  Duplex  Pin   Pri  Sec    Cache  NVS   CFW|
|  ----------------------------------------------------------------------------|
|  _ 259  CRP259  3390-2  ON    OFF    NO     NO                 ON    OFF  OFF|
|  _ 25A  MVP002  3390-2  ON    OFF    NO     NO                 ON    OFF  OFF|
|  _ 25B  MVP004  3390-2  ON    OFF    NO     NO                 ON    OFF  OFF|
|  _ 260  MV6060  3380-J  ON    OFF    NO     NO                 ON    OFF  OFF|
|  _ 261  MV2120  3380-J  ON    OFF    NO     NO                 ON    OFF  OFF|
|  _ 262  VMSHDD  3380-J  ON    OFF    NO     NO                 ON    OFF  OFF|
|  _ 263  MV3710  3380-J  ON    OFF    NO     NO                 ON    OFF  OFF|
|  _ 264  ES430C  3380-E  ON    OFF    NO     NO                 ON    OFF  OFF|
|  _ 265  ES430R  3380-E  ON    OFF    NO     NO                 ON    OFF  OFF|
|  _ 266  MDSVM2  3380-E  ON    OFF    NO     NO                 ON    OFF  OFF|
|  _ 267  RMS004  3380-E  ON    OFF    NO     NO                 ON    OFF  OFF|
|  _ 270  HRN270  3380-J  ON    OFF    NO     NO                 ON    OFF  OFF|
|  _ 271  HRN271  3380-J  ON    OFF    NO     NO                 ON    OFF  OFF|
|  _ 272  HRN272  3380-J  ON    OFF    NO     NO                 ON    OFF  OFF|
|  _ 273  HRN273  3380-J  ON    OFF    NO     NO                 ON    OFF  OFF|
================================================================================


Options panel:
================================================================================
|   ----------------- Amdahl Cache Utility V2.4  Setup Options ----------------|
|  COMMAND INPUT ===>                                           SCROLL ===> CSR|
|                     _                                                        |
|                                                                              |
|   ------------------------------ Global options -----------------------------|
|    NO_   View result output from each SETCACHE cmd in a popup window.        |
|    NO_   Enable confirmation for each SETCACHE cmd.                          |
|    YES   Log all commands in userid.CACHE.LOG                                |
|    16    PFKey to set to 'REF' (refreshes controller and device status)      |
|   -------------------- Line operators for Controller Panel ------------------|
|    S     Display unformatted output from LISTDATA STATUS command             |
|    C     Display unformatted output from LISTDATA COUNTS command             |
|    P     Display unformatted output from LISTDATA PINNED command             |
|    D     Display panel showing all devices connected to this controller      |
|    U     Issue SETCACHE DESTAGE for this controller                          |
|    H     Invoke Cache Performance Statistics panel                           |
|   --------------------- Line operators for Devices Panel --------------------|
|    C     Display unformatted output from LISTDATA COUNTS command             |
|    P     Display unformatted output from LISTDATA PINNED command             |
|    I     Display unformatted output from LISTDATA STATUS command             |
|    D     Display panel for DUPLEX operations on the selected device.         |
|   ------- Color attributes ( RED, WHITE, BLUE, GREEN, YELLOW, TURQ, PINK) ---|
|    YELLOW   Cache Status field color                                         |
|    YELLOW   Cache Fast Write field color                                     |
|    YELLOW   NVS field color                                                  |
================================================================================
           Amdahl Cache Utility Install Instructions

To complete the installation of the Amdahl Cache Utility please complete
the following steps:

1. Copy all execs from hlq.EXEC to a library in the SYSPROC or SYSEXEC
   concatenation of the TSO Logon proc.
   or
   Add the dataset hlq.EXEC to the SYSPROC or SYSEXEC concatenation of
   the TSO Logon proc.  Note that the dataset with the largest blksize
   should come first in the concatenation.

   The execs make use of the ISPF LIBDEF facility so the other datasets
   will be dynamically allocated.

2. You MUST edit hlq.EXEC(CACHEMN0) and change the dataset names in the
   LIBDEF statements to reflect the new dataset names.
   You MUST also edit hlq.ISPSLIB(CSHSKEL2) and change the dataset name
   in the STEPLIB DD and the SYSEXEC DD to reflect your dataset names.
-----------------------------------------------------------------------
NOTE NOTE NOTE NOTE NOTE NOTE NOTE NOTE NOTE NOTE NOTE     Enough!-----
-----------------------------------------------------------------------
If your version of ISPF is less than version 3.3 remove the following   s
two lines from hlq.ISPPLIB(CSHMAN1):

 IF (&ZTDSELS ¬= 0)
   VER(&ACT,LISTV,&VERCTL,MSG=CSHM009)

and remove the following two lines from hlq.ISPPLIB(CSHMAN3):

 IF (&ZTDSELS ¬= 0)
   VER(&LOP,LISTV,&VERDEV,MSG=CSHM000)

(the LISTV form of VER was new with version 3.3) This will not change
the function of this dialog.  If an invalid character is entered for
an action on a row it will be ignored and no message will be displayed
indicating use of an invalid operator.
***********************************************************************

3. The following authorizations must be defined to allow use of the
   IDCAMS commands LISTDATA and SETCACHE:

SAF/RACF Resources required for IDCAMS commands
                   Resource                                              Access
Command/Parameter  Class     Resource Name                        Access
------------------------------------------------------------------------
BINDDATA           FACILITY  STGADMIN.IDC.BINDDATA                READ
LISTDATA           FACILITY  STGADMIN.IDC.LISTDATA                READ
  ACCESSCODE       FACILITY  STGADMIN.IDC.LISTDATA.ACCESSCODE     READ
SETCACHE           FACILITY  STGADMIN.IDC.SETCACHE                READ
  DISCARDPINNED    FACILITY  STGADMIN.IDC.SETCACHE.DISCARDPINNED  READ
  PENDINGOFF       FACILITY  STGADMIN.IDC.SETCACHE.PENDINGOFF     READ
  REINITIALIZE     FACILITY  STGADMIN.IDC.SETCACHE.REINITIALIZE   READ
  SUBSYSTEM        FACILITY  STGADMIN.IDC.SETCACHE.SUBSYSTEM      READ
  SETSECONDARY     DASDVOL     volser of the secondary            ALTER
  REESTABLISHDUPLEX DASDVOL    volser of the alternate            ALTER
------------------------------------------------------------------------

If you have a security system enabled, you should have the security
administrator verify that these rules/profiles are enabled for each user
that will use this dialog.
******************************************************************
SAMPLE ACF/2 rules:  *********************************************
******************************************************************
00001000$KEY(STGADMIN.IDC.BINDDATA) TYPE(FAC)
00002000$USERDATA(OWNER=KEM00)
00003000%CHANGE AMDCCSTSGMV7531
00004000 UID(AMDCCSTSGMV7531) ALLOW
00005000 UID(AMDCCSTSGUS7532) ALLOW
00006000 UID(*) PREVENT
00007000$KEY(STGADMIN.IDC.LISTDATA) TYPE(FAC)
00008000$USERDATA(OWNER=TWG00)
00009000%CHANGE AMDCCSTSGMV7531
00010000 UID(AMDCCSTSGMV7531) ALLOW
00020000 UID(AMDCCS**********$CACHE) ALLOW
00030000 UID(AMD********4052*CEB40) ALLOW
00040000 UID(AMD********8644*MES90) ALLOW
00050000 UID(AMD*************DMO40) ALLOW
00090000 UID(*) PREVENT
00100000$KEY(STGADMIN.IDC.LISTDATA.ACCESSCODE) TYPE(FAC)
00110000$USERDATA(OWNER=TWG00)
00120000%CHANGE AMDCCSTSGMV7531
00130000 UID(AMDCCSTSGMV7531) ALLOW
00140000 UID(AMDCCS**********$CACHE) ALLOW
00150000 UID(AMD*************DMO40) ALLOW
00160000 UID(AMD*************RER20) ALLOW
00170000 UID(AMD*************WHG10) ALLOW
00180000 UID(AMD*************WHG11) ALLOW
00190000 UID(*) PREVENT
00200000$KEY(STGADMIN.IDC.SETCACHE) TYPE(FAC)
00210000$USERDATA(OWNER=TWG00)
00220000%CHANGE AMDCCSTSGMV7531
00230000 UID(AMDCCSTSGMV7531) ALLOW
00240000 UID(AMDCCS**********$CACHE) ALLOW
00250000 UID(AMD*************DMO40) ALLOW
00260000 UID(AMD*************RER20) ALLOW
00270000 UID(AMD*************WHG10) ALLOW
00280000 UID(AMD*************WHG11) ALLOW
00290000 UID(*) PREVENT
00300000$KEY(STGADMIN.IDC.SETCACHE.DISCARDPINNED) TYPE(FAC)
00310000$USERDATA(OWNER=KEM00)
00320000%CHANGE AMDCCSTSGMV7531
00330000 UID(AMDCCSTSGMV7531) ALLOW
00340000 UID(AMDCCSTSGUS7532) ALLOW
00350000 UID(AMD*************DMO40) ALLOW
00360000 UID(AMD*************RER20) ALLOW
00370000 UID(AMD*************WHG10) ALLOW
00380000 UID(AMD*************WHG11) ALLOW
00390000 UID(*) PREVENT
00400000$KEY(STGADMIN.IDC.SETCACHE.PENDINGOFF) TYPE(FAC)
00410000$USERDATA(OWNER=TWG00)
00420000%CHANGE AMDCCSTSGMV7531
00430000 UID(AMDCCSTSGMV7531) ALLOW
00440000 UID(AMD*************DMO40) ALLOW
00450000 UID(AMD*************RER20) ALLOW
00460000 UID(AMD*************WHG10) ALLOW
00470000 UID(AMD*************WHG11) ALLOW
00480000 UID(*) PREVENT
00490000$KEY(STGADMIN.IDC.SETCACHE.REINITIALIZE) TYPE(FAC)
00500000$USERDATA(OWNER=TWG00)
00510000%CHANGE AMDCCSTSGMV7531
00520000 UID(AMDCCSTSGMV7531) ALLOW
00530000 UID(AMD*************DMO40) ALLOW
00540000 UID(AMD*************RER20) ALLOW
00550000 UID(AMD*************WHG10) ALLOW
00560000 UID(AMD*************WHG11) ALLOW
00570000 UID(*) PREVENT
00580000$KEY(STGADMIN.IDC.SETCACHE.SUBSYSTEM) TYPE(FAC)
00590000$USERDATA(OWNER=KEM00)
00600000%CHANGE AMDCCSTSGMV7531
00610000 UID(AMDCCSTSGMV7531) ALLOW
00620000 UID(AMDCCSTSGUS7532) ALLOW
00630000 UID(AMD*************DMO40) ALLOW
00640000 UID(AMD*************RER20) ALLOW
00650000 UID(AMD*************WHG10) ALLOW
00660000 UID(AMD*************WHG11) ALLOW
00670000 UID(*) PREVENT
******************************************************************
END SAMPLE ACF/2  :  *********************************************

You must also update the member IKJTSOxx in SYS1.PARMLIB to identify
LISTDATA and SETCACHE as authorized commands (AUTHCMD section).


4. This could also be set up as a menu option on the primary menu or on
   some other sub menu. The following shows an example of how to add this
   dialog to a menu panel. For this example I used the panel found in
   ISP.V3R3M0.ISPPENU(ISP@MSTR).

%------------------------  ISPF MASTER APPLICATION MENU  -----------------------
%OPTION  ===>_ZCMD                                                             +
%                                                           +USERID   - &ZUSER
%   1 +SAMPLE1     - Sample application 1                   +TIME     - &ZTIME
%   2 +.           - (Description for option 2)             +TERMINAL - &ZTERM
% ACU +. Cache     - Amdahl Cache Utility                   +PF KEYS  - &ZKEYS
%   4 +.           - (Description for option 4)
%   5 +.           - (Description for option 5)
%   X +EXIT        - Terminate ISPF using list/log defaults
%
+Enter%END+command to terminate ISPF.
%
+5685-054 (C) COPYRIGHT IBM CORP. 1980, 1991
)INIT
  .HELP    = ISP00005     /* Help for this master menu             */
  &ZPRIM   = YES          /* This is a primary option menu         */
)PROC
  &ZSEL = TRANS( TRUNC (&ZCMD,'.')
                1,'PANEL(ISP@PRIM)' /* Sample primary option menu  */
              ACU,'CMD(%CACHEMAN)'  /* Newappl set inside exec     */
            /*******************************************************/
            /* Following shows how to code an invocation of the    */
            /* ISPF Program Development Facility, where "n" is     */
            /* the desired selection number:                       */
            /*                                                     */
            /*  n,'PANEL(ISR@PRIM) NEWAPPL(ISR)'                   */
            /*                                                     */
            /*******************************************************/
              ' ',' '
                X,'EXIT'
                *,'?' )
  &ZTRAIL = .TRAIL
)END


You are now ready to invoke the dialog.
From any command input area enter 'TSO CACHEMAN.
From option 6 panel or from native TSO Ready prompt enter 'CACHEMAN'.
If you added an option to a menu it may be selected by that identifier.

```

