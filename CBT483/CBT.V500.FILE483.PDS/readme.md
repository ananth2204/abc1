
## $$$$$DOC.txt
```
***********************************************************************
MEMBER   DATE      WHO WHAT
-------- --------- --- ------------------------------------------------
$$$$$DOC N/A       RAM THIS MEMBER
-------- --------- --- ------------------------------------------------
$QSMS    07.SEP.00 RAM SHORT DESCRIPTION OF QSMS
QSMS     07.SEP.00 RAM REXX-FUNCTION THAT OBTAINS THE SMS-STATUS OF ALL
                       DEFINED VOLUMES. RUNS AS TSO-COMMAND OR REXX
PRINTREG 07.SEP.00 RAM ASM-MACRO USED IN QSMS
IGDBCD   ??.???.?? GSF SMS-CONFIG MAPPING MACRO BY GILBERT SAINT-FLOUR
                       USED IN QSMS
QSMSREXX 07.SEP.00 RAM SAMPLE REXX THAT INVOKES QSMS.
-------- --------- --- ------------------------------------------------
$QVTOC   07.SEP.00 RAM SHORT DESCRIPTION OF QVTOC
QVTOC    07.SEP.00 RAM A CMD-PROCESSOR THAT SCANS ALL ONLINE DASDS AND
                       BUILDS A LIST OF ALL LOADMODULES.
                       $$NOTE$$: NEEDS READ ACCESS TO ALL LOADLIBS|
ADDMSG   07.SEP.00 RAM ASM-MACRO USED IN QVTOC
AIACCTAB 07.SEP.00 RAM FILTER-PGM USED WITH QVTOC
-------- --------- --- ------------------------------------------------
$QLPAR   07.SEP.00 RAM SHORT DESCRIPTION OF QLPAR
QLPAR    07.SEP.00 RAM A TSO CP SHOWING LPAR-INFORMATION FOR ALL CUR-
                       RENTLY DEFINED PARTITIONS.
ADDMSG   07.SEP.00 RAM ASM-MACRO USED IN QLPAR
PRINTREG 07.SEP.00 RAM ASM-MACRO USED IN QLPAR
-------- --------- --- ------------------------------------------------
$QCMD    07.SEP.00 RAM SHORT DESCRIPTION OF QCMD
QCMD     07.SEP.00 RAM A TSO COMMANDPROCESSOR THAT ISSUES MVS-COMMANDS
                       AND TRAPS THE RESPONSE. THE OUTPUT CAN BE WRITTEN
                       INTO A STEM OF REXX-VARIABLES.
QCMC     07.SEP.00 RAM SAMPLE REXX THAT USES THE QCMD-FUNCTION
QCMSCRL  07.SEP.00 RAM SCROLL-ROUTINE FOR THE QCMC-FUNCTION
QCMP010  07.SEP.00 RAM PANEL FOR THE QCMC-FUNCTION
QCMDREPL 07.SEP.00 RAM SAMPLE JOB TO RUN QCMD IN BATCH
-------- --------- --- ------------------------------------------------
QTOD     07.SEP.00 RAM A TSO COMMANDPROCESSOR SHOWING DATE/TIME IN A
                       MORE CONVENIENT WAY THAN THE "TIME" COMMAND.
TODPRINT 07.SEP.00 RAM A ASM-MACRO THAT "PRINTS" A TOD-STAMP.
-------- --------- --- ------------------------------------------------
Q522     07.SEP.00 RAM A TSO COMMANDPROCESSOR PREVENTING YOU FROM BE-
                       ING LOGGED OFF AFTER JWT EXCEEDED. AUTHORIZED
-------- --------- --- ------------------------------------------------
OMTREE   07.SEP.00 RAM REXX DISPLAYING ALL CURRENTLY MOUNTED HFSES AND
                       THEIR HIERARCHICAL RELATIONSHIP
OMTREE1  07.SEP.00 RAM PANEL DISPLAYED IN OMTREE
OMTREEH  07.SEP.00 RAM HELP PANEL FOR THE OMTREE-FUNCTION
-------- --------- --- ------------------------------------------------
$INSLINE 07.SEP.00 RAM SHORT DESCRIPTION OF INSLINE
INSLINE  07.SEP.00 RAM EDIT-MACRO THAT INSERTS LINES INTO DATASETS
-------- --------- --- ------------------------------------------------
CATCVTM  07.SEP.00 RAM EDIT-MACRO FOR POSTPROCESSING MCNVTCAT-OUTPUT
-------- --------- --- ------------------------------------------------
WORM     07.SEP.00 RAM REXX GAME
WORMP    07.SEP.00 RAM PLAYGROUND FOR WORM
WORMH    07.SEP.00 RAM HELP PANEL FOR THE WORM-GAME
-------- --------- --- ------------------------------------------------
MM       07.SEP.00 RAM MASTERMIND GAME, WRITTEN IN REXX
MMP      07.SEP.00 RAM PLAYGROUND FOR MASTERMIND
MMPH     07.SEP.00 RAM HELP PANEL FOR THE MASTERMIND GAME
-------- --------- --- ------------------------------------------------
QUICKIE  07.SEP.00 RAM XMITTED LOADLIB WITH THE ASM-PGMS.
-------- --------- --- ------------------------------------------------
$$NOTE$$ THE MM, WORM AND OMTREE-FUNCTIONS SHOULD BE USED WITH A
         GRAPHIC-TERMINAL OR AN EMULATOR SUPPORTING BOTH APL AND GRAPH.
-------- --------- --- ------------------------------------------------
***********************************************************************
* For further information, please contact me under following address: *
*                                                                     *
*                           Thomas Ramseier                           *
*        FOITT - Swiss Federal Office of Information Technology,      *
*                    Systems and Telecommunication                    *
*                          Monbijoustrasse 74                         *
*                            CH-3003 Berne                            *
*                            -switzerland-                            *
* phone: ++41 (0)31 323'01'00         facsimile: ++41 (0)31 325'93'75 *
*          e-mail (preferred): thomas.ramseier@bit.admin.ch           *
*                                                             cheers. *
***********************************************************************
```

