```
//***FILE 805 is from Michael Schmutzok and contains the source     *   FILE 805
//*       code and JCL needed to establish an SNMP sub-agent, an    *   FILE 805
//*       EMC (Extended MCS) monitoring started task and an         *   FILE 805
//*       externally called storage snap program.  Member MACROS    *   FILE 805
//*       in this file contains the user written macros needed to   *   FILE 805
//*       compile the programs.                                     *   FILE 805
//*                                                                 *   FILE 805
//*       See member $$$INTRO for an explanation of SNMP and an     *   FILE 805
//*       introduction to what this package does.  It basically     *   FILE 805
//*       finds "alerts" in the system operation, so the sysprog    *   FILE 805
//*       or an operator can keep track of them.                    *   FILE 805
//*                                                                 *   FILE 805
//*           email:  schmum@shands.ufl.edu                         *   FILE 805
//*                                                                 *   FILE 805
//*       Many thanks go out to those of you on the MVS and         *   FILE 805
//*       Assembler ListServs who answered the many questions I     *   FILE 805
//*       had while I was creating this beastie.                    *   FILE 805
//*                                                                 *   FILE 805
//*     OVERVIEW                                                    *   FILE 805
//*     --------                                                    *   FILE 805
//*       This dataset contains several programs which may be of    *   FILE 805
//*       general interest to other installations.  They are, of    *   FILE 805
//*       course, available on an as-is condition with the usual    *   FILE 805
//*       disclaimer.                                               *   FILE 805
//*                                                                 *   FILE 805
//*       I am under no illusions about the level of my assembler   *   FILE 805
//*       coding skills.  I'm not an expert by any means.           *   FILE 805
//*       However, having said that, these programs were used in    *   FILE 805
//*       z/OS 1.7 and our current z/OS 1.9 environment.  They      *   FILE 805
//*       should work on any IBM supported system.  Some may not    *   FILE 805
//*       work on earlier systems.                                  *   FILE 805
//*                                                                 *   FILE 805
//*       This dataset contains the source code and JCL needed      *   FILE 805
//*       to establish an SNMP sub-agent, an EMC (Extended MCS)     *   FILE 805
//*       monitoring started task and an externally called          *   FILE 805
//*       storage snap program. Its sister dataset contains the     *   FILE 805
//*       user written macros needed to compile the programs.       *   FILE 805
//*       The IBM macros can be found in SYS1.MACLIB,               *   FILE 805
//*       TCPIP.SEZAMAC and SYS1.AMODGEN. A list of the macros      *   FILE 805
//*       and control block DSECTS used can be found in member      *   FILE 805
//*       $$CTLBLK.                                                 *   FILE 805
//*                                                                 *   FILE 805
//*       For some of the metrics I gather, I couldn't figure       *   FILE 805
//*       out how to get the information through control block      *   FILE 805
//*       chaining (I DID mention I wasn't an expert in this).      *   FILE 805
//*       To compensate for this, I use/call system REXX execs      *   FILE 805
//*       from which I issue JES2 commands, HSM commands, etc.      *   FILE 805
//*       and process the output from these commands. Not the       *   FILE 805
//*       most efficient way to do it, but it works.                *   FILE 805
//*                                                                 *   FILE 805
//*       2/10/09 - As of this writing, I have discovered a bug     *   FILE 805
//*       with system REXX in that AXRCMD does not handle           *   FILE 805
//*       certain types of multi-line command output (e.g.          *   FILE 805
//*       $DSPOOL, F HSM,QUERY CDS, etc.). A PMR has been opened    *   FILE 805
//*       with IBM.                                                 *   FILE 805
//*                                                                 *   FILE 805
//*     NIMAGENT                                                    *   FILE 805
//*     --------                                                    *   FILE 805
//*       This SNMP sub-agent attaches several subtasks which       *   FILE 805
//*       query/check various system metrics and updates            *   FILE 805
//*       established MIB values. These values may then be          *   FILE 805
//*       queried by an external monitor (such as NimBUS in our     *   FILE 805
//*       case) and alerting done. All of the SNMP interfacing      *   FILE 805
//*       is done via the Distributed Program Interface (DPI).      *   FILE 805
//*       See RFC 1228 for more information.                        *   FILE 805
//*                                                                 *   FILE 805
//*       Future enhancements:                                      *   FILE 805
//*       - Eliminate the system REXX execs by going directly to    *   FILE 805
//*         the control blocks                                      *   FILE 805
//*       - Finish the RENT process. Currently the sub-tasks are    *   FILE 805
//*         re-entrant but the overall load module is not.          *   FILE 805
//*       - Add a MODIFY command to dynamically change the timer    *   FILE 805
//*         interval for any of the sub-tasks (currently            *   FILE 805
//*         hardcoded).                                             *   FILE 805
//*                                                                 *   FILE 805
//*     NIMBEMCS                                                    *   FILE 805
//*     --------                                                    *   FILE 805
//*       The EMC monitoring program can be used to monitor         *   FILE 805
//*       console messages and issue SNMP traps to an external      *   FILE 805
//*       monitoring system for alerting purposes. The sample       *   FILE 805
//*       included here was based on a sample IBM program found     *   FILE 805
//*       in SYS1.SAMPLIB(IEAEXMCS).                                *   FILE 805
//*                                                                 *   FILE 805
//*       Note: The EMC monitoring program issues SNMP traps.       *   FILE 805
//*       Ours is coded to use the 'awtrap' program which I         *   FILE 805
//*       found within the base Unicenter code from Computer        *   FILE 805
//*       Associates (CAI) and is found in the HFS/ZFS file:        *   FILE 805
//*          /cai/agent/ro/awtrap                                   *   FILE 805
//*                                                                 *   FILE 805
//*       If you do not have access to this command, you will       *   FILE 805
//*       need to code or find own trap command or issue one via    *   FILE 805
//*       DPI.                                                      *   FILE 805
//*                                                                 *   FILE 805
//*     PCCSSNAP                                                    *   FILE 805
//*     --------                                                    *   FILE 805
//*       PCCSSNAP is a re-entrant program that can be linked to    *   FILE 805
//*       from a program and used to snap storage areas for         *   FILE 805
//*       debugging purposes. The addresses of the storage area     *   FILE 805
//*       to be snapped are passed via a parmlist. The snap         *   FILE 805
//*       output is directed to a JES2 sysout dataset, which a      *   FILE 805
//*       DD (SNAPDD) is dynamically allocated for.                 *   FILE 805
//*                                                                 *   FILE 805
//*     Dataset Contents:                                           *   FILE 805
//*                                                                 *   FILE 805
//*       Member      Description                                   *   FILE 805
//*       ------------------------------------------------------    *   FILE 805
//*       $$DISCL   - Disclaimer                                    *   FILE 805
//*       #README   - This member description list                  *   FILE 805
//*       ASM       - Assemble/link entire sub-agent                *   FILE 805
//*       ASM1      - Assemble/link a single subtask                *   FILE 805
//*       Author    - Contact information                           *   FILE 805
//*       LINK1     - Linkedit sub-agent                            *   FILE 805
//*       NIMAGENT  - Started task JCL for NIMAGNT program          *   FILE 805
//*       NIMAGNT   - Main sub-agent                                *   FILE 805
//*       NIMBEMCS  - Console monitoring program                    *   FILE 805
//*       NIMBCONS  - Started task JCL for NIMBEMCS program         *   FILE 805
//*       NIMDASD   - Subtask: DASD checks                          *   FILE 805
//*       NIMESTA   - Sub-agent/sub-task ESTAI routine              *   FILE 805
//*       NIMEXST   - Subtask: Started task existence checking      *   FILE 805
//*       NIMHSM    - Subtask: HSM checking                         *   FILE 805
//*       NIMJES2   - Subtask: JES2 checking                        *   FILE 805
//*       NIMMIB    - Subagent MIB                                  *   FILE 805
//*       NIMSYS    - Subtask: System information                   *   FILE 805
//*       NMIBDESC  - Sample MIBDESC for TCPIP                      *   FILE 805
//*       NMIBSDAT  - Sample MIBDATA for TCPIP                      *   FILE 805
//*       PCCSSNAP  - Callable program to snap data areas for       *   FILE 805
//*                   debugging                                     *   FILE 805
//*       QUERYJES  - System REXX exec to query JES2 metrics        *   FILE 805
//*                   (used in NIMJES2)                             *   FILE 805
//*                                                                 *   FILE 805
//*       The following were used to develop the code to be         *   FILE 805
//*       included within a sub-task                                *   FILE 805
//*                                                                 *   FILE 805
//*       SYSREXX   - JCL to execute a program that calls a         *   FILE 805
//*                   system REXX exec                              *   FILE 805
//*       SYSREXXJ  - Program to call system REXX exec (code        *   FILE 805
//*                   used in NIMJES2)                              *   FILE 805
//*                                                                 *   FILE 805

```
