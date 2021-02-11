```
//***FILE 483 is from Thomas Ramseier and contains a nice           *   FILE 483
//*           collection of system utilities.  A description of     *   FILE 483
//*           the programs follows below.                           *   FILE 483
//*                                                                 *   FILE 483
//*      $$$$$DOC  THIS MEMBER                                      *   FILE 483
//*                                                                 *   FILE 483
//*      $QSMS     SHORT DESCRIPTION OF QSMS                        *   FILE 483
//*      QSMS      REXX FUNCTION THAT OBTAINS THE SMS STATUS        *   FILE 483
//*                OF ALL DEFINED VOLUMES. RUNS AS TSO COMMAND      *   FILE 483
//*                OR REXX                                          *   FILE 483
//*                (FIXED NOT TO GO INTO AN INFINITE LOOP)          *   FILE 483
//*                (SG-12/18)                                       *   FILE 483
//*      PRINTREG  ASM MACRO USED IN QSMS                           *   FILE 483
//*      IGDBCD    SMS CONFIG MAPPING MACRO BY GILBERT SAINT        *   FILE 483
//*                FLOUR USED IN QSMS                               *   FILE 483
//*                                                                 *   FILE 483
//*      QSMSREXX  SAMPLE REXX THAT INVOKES QSMS.                   *   FILE 483
//*                                                                 *   FILE 483
//*      $QVTOC    SHORT DESCRIPTION OF QVTOC                       *   FILE 483
//*      QVTOC     A CMD PROCESSOR THAT SCANS ALL ONLINE DASDS      *   FILE 483
//*                AND BUILDS A LIST OF ALL LOAD MODULES.           *   FILE 483
//*                $$NOTE$$: NEEDS READ ACCESS TO ALL LOADLIBS      *   FILE 483
//*                                                                 *   FILE 483
//*      ADDMSG    ASM MACRO USED IN QVTOC                          *   FILE 483
//*      AIACCTAB  FILTER PGM USED WITH QVTOC                       *   FILE 483
//*                                                                 *   FILE 483
//*      $QLPAR    SHORT DESCRIPTION OF QLPAR                       *   FILE 483
//*      QLPAR     A TSO CP SHOWING LPAR INFORMATION FOR ALL        *   FILE 483
//*                CURRENTLY DEFINED PARTITIONS.                    *   FILE 483
//*                                                                 *   FILE 483
//*      ADDMSG    ASM MACRO USED IN QLPAR                          *   FILE 483
//*      PRINTREG  ASM MACRO USED IN QLPAR                          *   FILE 483
//*                                                                 *   FILE 483
//*      $QCMD     SHORT DESCRIPTION OF QCMD                        *   FILE 483
//*      QCMD      A TSO COMMANDPROCESSOR THAT ISSUES MVS           *   FILE 483
//*                COMMANDS AND TRAPS THE RESPONSE. THE             *   FILE 483
//*                OUTPUT CAN BE WRITTEN INTO A STEM OF             *   FILE 483
//*                REXX VARIABLES.                                  *   FILE 483
//*                                                                 *   FILE 483
//*      QCMC      SAMPLE REXX THAT USES THE QCMD FUNCTION          *   FILE 483
//*      QCMSCRL   SCROLL ROUTINE FOR THE QCMC FUNCTION             *   FILE 483
//*      QCMP010   PANEL FOR THE QCMC FUNCTION                      *   FILE 483
//*      QCMDREPL  SAMPLE JOB TO RUN QCMD IN BATCH                  *   FILE 483
//*                                                                 *   FILE 483
//*      QTOD      A TSO COMMAND PROCESSOR SHOWING DATE/TIME        *   FILE 483
//*                IN A MORE CONVENIENT WAY THAN THE "TIME"         *   FILE 483
//*                COMMAND.                                         *   FILE 483
//*                                                                 *   FILE 483
//*      DTOD      AN ADAPTATION OF QTOD WHICH ALLOWS YOU TO        *   FILE 483
//*                INTERPRET A TIME ENTERED IN DISPLAY STCK         *   FILE 483
//*                FORMAT:   DTOD D565353F6689C002                  *   FILE 483
//*                                                                 *   FILE 483
//*      TODPRINT  A ASM MACRO THAT "PRINTS" A TOD STAMP.           *   FILE 483
//*                                                                 *   FILE 483
//*      Q522      A TSO COMMANDPROCESSOR PREVENTING YOU            *   FILE 483
//*                FROM BEING LOGGED OFF AFTER JWT                  *   FILE 483
//*                EXCEEDED.  AUTHORIZED.                           *   FILE 483
//*                                                                 *   FILE 483
//*      OMTREE    REXX DISPLAYING ALL CURRENTLY MOUNTED            *   FILE 483
//*                HFSES AND THEIR HIERARCHICAL RELATIONSHIP        *   FILE 483
//*      OMTREE1   PANEL DISPLAYED IN OMTREE                        *   FILE 483
//*      OMTREEH   HELP PANEL FOR THE OMTREE FUNCTION               *   FILE 483
//*                                                                 *   FILE 483
//*      $INSLINE  SHORT DESCRIPTION OF INSLINE                     *   FILE 483
//*      INSLINE   EDIT MACRO THAT INSERTS LINES INTO               *   FILE 483
//*                DATASETS                                         *   FILE 483
//*                (fixed by Peter Glanzmann)                       *   FILE 483
//*                                                                 *   FILE 483
//*      CATCVTM   EDIT MACRO FOR POSTPROCESSING MCNVTCAT           *   FILE 483
//*                OUTPUT                                           *   FILE 483
//*                                                                 *   FILE 483
//*      WORM      REXX GAME                                        *   FILE 483
//*      WORMP     PLAYGROUND FOR WORM                              *   FILE 483
//*      WORMH     HELP PANEL FOR THE WORM GAME                     *   FILE 483
//*                                                                 *   FILE 483
//*      MM        MASTERMIND GAME, WRITTEN IN REXX                 *   FILE 483
//*      MMP       PLAYGROUND FOR MASTERMIND                        *   FILE 483
//*      MMPH      HELP PANEL FOR THE MASTERMIND GAME               *   FILE 483
//*                                                                 *   FILE 483
//*      QUICKIE   XMITTED LOADLIB WITH THE ASM PGMS.               *   FILE 483
//*                                                                 *   FILE 483
//*      $$NOTE$$  THE MM, WORM AND OMTREE FUNCTIONS SHOULD         *   FILE 483
//*                BE USED WITH A GRAPHIC TERMINAL OR AN            *   FILE 483
//*                EMULATOR SUPPORTING BOTH APL AND GRAPH.          *   FILE 483
//*                                                                 *   FILE 483
//*        For further information, please contact me under         *   FILE 483
//*        following address:                                       *   FILE 483
//*                                                                 *   FILE 483
//*                         Thomas Ramseier                         *   FILE 483
//*      FOITT   Swiss Federal Office of Information Technology,    *   FILE 483
//*                  Systems and Telecommunication                  *   FILE 483
//*                        Monbijoustrasse 74                       *   FILE 483
//*                          CH 3003 Berne                          *   FILE 483
//*                           Switzerland                           *   FILE 483
//*                                                                 *   FILE 483
//*        phone:     ++41 (0)31 323-01-00                          *   FILE 483
//*        facsimile: ++41 (0)31 325-93-75                          *   FILE 483
//*                                                                 *   FILE 483
//*        e-mail (preferred): thomas.ramseier@bit.admin.ch         *   FILE 483
//*                                                                 *   FILE 483
//*                       cheers.                                   *   FILE 483
//*                                                                 *   FILE 483

```
