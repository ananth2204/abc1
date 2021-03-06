# CBTTAPE Archive

This github archive is an extraction of the XMIT files availble on CBT tape. It was produced using the xmit python library availble here: https://github.com/mainframed/xmilib

Folders contain the extracted zip files, the original XMIT file unloaded to a folder named after the PDS contained in the XMIT and any nested XMITs contained in the CBT xmit file.

Since the python library has mimetype detection all plaintext files were converted to text and binary files were given specific extentions.

Each folder also contains a `.json` file which contains the contents of the XMI file as well as arguments and parsed attributes (i.e. ispf stats, INRM02/3 records, XMIT messages, etc).

The files in their folders retained their last modified dates if the XMIT file had them.

Below is the table of contents included with CBT Tape. This archive was last updated on 02/10/2021.

## CBTTOC499

```
//*+File 001:  Detailed documentation of the CBT MVS Utilities Tape *#  DOC FILE
//*+File 002:  CBT973 Compression-Decompression Program for Files   *   DOC FILE
//*+File 003:  JCL member to load each tape file to disk            *#  DOC FILE
//*+File 004:  Put ./ ADD cards into this file to make a PDS        *   DOC FILE
//*+File 005:  VMREXX exec to load CBT tape to VM - fixed a bit     *   DOC FILE
//*+File 006:  Collection of Utilities to manipulate File 001 doc   *#  DOC FILE
//*+File 007:  SYSUPLOG (keep as EBCDIC only) - sequential data     *#  DOC FILE
//*+File 008:  File containing jobs used to create the CBT Tape     *#  DOC FILE
//*+File 009:  RACF 1.7 Exits                                       *   DOC FILE
//*+File 010:  TSO command called ISPFPRIM to invoke ISPF from TSO  *   DOC FILE
//*+File 011:  MVS DEBE, MSG2USER, System Info into CLIST variables *   DOC FILE
//*+File 012:  John Hancock Mutual ISPF Background Jobs driver      *   DOC FILE
//*+File 013:  SHARE RACF mods tape - SETPW2 fixed - WHOIS fixed    *   DOC FILE
//*+File 014:  Sam Golob's SMP/E Introduction tutorial, etc.        *   DOC FILE
//*+File 015:  Warner Brothers collection of Utilities and Exits    *   DOC FILE
//*+File 016:  Scott & White Hospital User Exits                    *   DOC FILE
//*+File 017:  LISTDD program from Firemen's Fund                   *   DOC FILE
//*+File 018:  TSUPDATE program from Conrail                        *   DOC FILE
//*+File 019:  Utilities from John Hooper                           *   DOC FILE
//*+File 020:  A collection of System REXX execs                    *   DOC FILE
//*+File 021:  BELL & HOWELL operator communication utilities       *   DOC FILE
//*+File 022:  A collection of utilities from Mark Hedges           *   DOC FILE
//*+File 023:  Mods to LOGON to TSO under a secondary JES2          *   DOC FILE
//*+File 024:  XFERDUMP from MCI - originally from Howard Dean      *   DOC FILE
//*+File 025:  TSO Console Pgm and other pgms from TU Services      *   DOC FILE
//*+File 026:  Program to take a survey at TSO LOGOFF time          *   DOC FILE
//*+File 027:  Date Check utility from DAYCO Products               *   DOC FILE
//*+File 028:  CLISTs to generate JCL to backup a list of datasets  *   DOC FILE
//*+File 029:  Cook Book instructions to Enlarge the VTOC of a pack *   DOC FILE
//*+File 030:  Mods to change console pfkeys MVS370 thru XA 2.1.7   *   DOC FILE
//*+File 031:  IGGPRE00 exit with RACF interface                    *   DOC FILE
//*+File 032:  JCLSCAN, COPYPACK, DOWNDATE programs                 *   DOC FILE
//*+File 033:  SHARE JES2 Song Book                                 *   DOC FILE
//*+File 034:  RACFUSER - program to print PASSWORD info by userid  *   DOC FILE
//*+File 035:  LOAD MODULE file - Quick install of useful programs  *#  DOC FILE
//*+File 036:  FIXPDS. ISPF-based utility. Restore deleted members  *   DOC FILE
//*+File 037:  COPYCAT - pgm to copy and reorganize CVOLs           *   DOC FILE
//*+File 038:  KLINGON - TSO based reverse STAR TREK game           *   DOC FILE
//*+File 039:  CITIBANK - SMF 14-15 pgm, and IPOUPDTE mod & doc     *   DOC FILE
//*+File 040:  Clean a PDS, string scan-repl, super file copy, etc  *   DOC FILE
//*+File 041:  JES2 Exits to drive XEROX printers                   *   DOC FILE
//*+File 042:  Load File 001 information to an INFO/MVS database    *   DOC FILE
//*+File 043:  Header information for File 042                      *   DOC FILE
//*+File 044:  ASMTOZAP - code your system zaps in assembler lang   *   DOC FILE
//*+File 045:  PDS Compare program adapted from Yale compare pgm    *   DOC FILE
//*+File 046:  PACKRAT program to scratch datasets from a DASD pack *   DOC FILE
//*+File 047:  NOCELL-LISTICAT etc. Jim Lane's large collection.    *   DOC FILE
//*+File 048:  LISTVOL, LISTSPC, LOCINDEX: doc and help for them    *   DOC FILE
//*+File 049:  STATS program to report structure of datasets        *   DOC FILE
//*+File 050:  Internet URLs for Free Downloads                     *   DOC FILE
//*+File 051:  Internet URLs for some Relevant Vendor Sites         *   DOC FILE
//*+File 052:  SHOWMVS for MVS 3.8 - from Jim Morrison              *   DOC FILE
//*+File 053:  Deluxe Check Printers ISPF system - source code      *   DOC FILE
//*+File 054:  Deluxe Check Printers ISPF system - ISPF panels      *   DOC FILE
//*+File 055:  Deluxe Check Printers ISPF system - ISPF messages    *   DOC FILE
//*+File 056:  Deluxe Check Printers ISPF system - ISPF skeletons   *   DOC FILE
//*+File 057:  Deluxe Check Printers ISPF system - ISPF clists      *   DOC FILE
//*+File 058:  TSO command to display the LINKLIST                  *   DOC FILE
//*+File 059:  IPL DATE display under ISPF                          *   DOC FILE
//*+File 060:  Software Status Report ISPF. Source and ISPF panels  *   DOC FILE
//*+File 061:  Software Status Report ISPF. Load Modules            *   DOC FILE
//*+File 062:  Software Status Report ISPF. Indxtbl init record     *   DOC FILE
//*+File 063:  Software Status Report ISPF. Prodtbl init record     *   DOC FILE
//*+File 064:  Software Status Report ISPF. History init record     *   DOC FILE
//*+File 065:  Mod to put uncataloged dataset into LINKLIST - old   *   DOC FILE
//*+File 066:  Alan Field utility collection                        *   DOC FILE
//*+File 067:  IEFDB401 and IEFUJV exits from Coca Cola Corp.       *   DOC FILE
//*+File 068:  TSTVS - Console Editor and Dataset Utility-Rob Prins *   DOC FILE
//*+File 069:  Coding Examples from Carmine Cannatello's ASM book   *   DOC FILE
//*+File 070:  Computer Sciences Corp - was Gen Dynamics Sysmods    *   DOC FILE
//*+File 071:  Documentation for the contents of other free tapes   *   DOC FILE
//*+File 072:  PANEXEC ISPF interface - ISPPLIB                     *   DOC FILE
//*+File 073:  PANEXEC ISPF interface - ISPLLIB                     *   DOC FILE
//*+File 074:  NASPA MACLIB - ISPF macros from NaSPA VIP Tape       *   DOC FILE
//*+File 075:  PANEXEC ISPF interface - ISPALIB                     *   DOC FILE
//*+File 076:  PANEXEC ISPF interface - PROCS                       *   DOC FILE
//*+File 077:  MVS 3.8 Utilities for Hercules from Brian Westerman  *   DOC FILE
//*+File 078:  ISPF EDIT macros from John Kalinich - SHARE cd-rom   *   DOC FILE
//*+File 079:  SCRIPT/VS DCF ISPF Interface                         *   DOC FILE
//*+File 080:  RACF Data Reformatter to allow postprocessing        *   DOC FILE
//*+File 081:  MVS DEBE                                             *   DOC FILE
//*+File 082:  Reference Manuals: IEHMAP, MAPLPA, PTXREF, SUPERZAP  *   DOC FILE
//*+File 083:  IEHMAP Source and Object, with Installation JCL      *   DOC FILE
//*+File 084:  MAPLPA Object                                        *   DOC FILE
//*+File 085:  PTXREF Object                                        *   DOC FILE
//*+File 086:  SUPERZAP Object                                      *   DOC FILE
//*+File 087:  ISPF SYSLOG Archival Utility from Mark Diehl         *   DOC FILE
//*+File 088:  Brian Westerman Utilities                            *   DOC FILE
//*+File 089:  University of Manitoba DYNALLOC Interface            *   DOC FILE
//*+File 090:  DELINKI - in PL/I and assembler - delink load mods   *   DOC FILE
//*+File 091:  PROCs for PL1/F, FORTRAN G & H, RPG/F and ALGOL      *   DOC FILE
//*+File 092:  PL1/F Compiler - moved to CBT Overflow Tape File 092 *   DOC FILE
//*+File 093:  PDSLOAD, OFFLOAD, UPDTE, UNUPDTE: Sequentialize PDS  *#  DOC FILE
//*+File 094:  DAF from Mike Cleary - Dataset Audit Facility        *   DOC FILE
//*+File 095:  ISPF EDIT MACRO collection from Paul Davis - 1       *   DOC FILE
//*+File 096:  University of Missouri Hospital Utilities & Exits    *   DOC FILE
//*+File 097:  Disk Management System from Peoples National Bank    *   DOC FILE
//*+File 098:  ISPF interface for XMIT/RECEIVE - source             *   DOC FILE
//*+File 099:  ISPF interface for XMIT/RECEIVE - data file          *   DOC FILE
//*+File 100:  Deluxe Check Printers ISPF/PDF customizations        *   DOC FILE
//*+File 101:  Deluxe Check Printers ISPF Clists                    *   DOC FILE
//*+File 102:  TAPESCAN program - Now 64K capable                   *   DOC FILE
//*+File 103:  ISPF DIALOGS from Bill Horton of Tennessee Eastman   *   DOC FILE
//*+File 104:  JES2 Remote Printers (JRP package) - OS/390 level    *   DOC FILE
//*+File 105:  ISPF 3.8 OUTLIST replacement and enhancement         *   DOC FILE
//*+File 106:  Utility to list RACF access of Users to Entities     *   DOC FILE
//*+File 107:  Clemson University Structured Macro Library          *   DOC FILE
//*+File 108:  Clemson University Structured Macro SAMPLIB          *   DOC FILE
//*+File 109:  IEFACTRT exit code from First Chicago                *   DOC FILE
//*+File 110:  IEFACTRT sample output from File 109 code            *   DOC FILE
//*+File 111:  REVLON utility collection from Jim Purdy             *   DOC FILE
//*+File 112:  VTOC TSO command processor                           *   DOC FILE
//*+File 113:  SMPSCAN documentation                                *   DOC FILE
//*+File 114:  SMPSCAN jobstream samples                            *   DOC FILE
//*+File 115:  SMPSCAN source code                                  *   DOC FILE
//*+File 116:  Disk Seek Analysis program                           *   DOC FILE
//*+File 117:  WTO Exits from Jim Cook of Coca Cola                 *   DOC FILE
//*+File 118:  SMPPTFIN preprocessing - sort by FMIDs & their PTFs  *   DOC FILE
//*+File 119:  Howard Dean Utility collection - 1st File            *   DOC FILE
//*+File 120:  Sam Golob's "MVS Tools & Tricks" and other articles  *#  DOC FILE
//*+File 121:  Wide illustrations from Sam Golob's articles         *   DOC FILE
//*+File 122:  RMSG Subsystem and JES2 exits from Allergan          *   DOC FILE
//*+File 123:  TSO Echo Programs for "TSO Command Restriction"      *   DOC FILE
//*+File 124:  State of Wisconsin ISPF/PDF applications             *   DOC FILE
//*+File 125:  State of Connecticut RMF analysis system - in SAS    *   DOC FILE
//*+File 126:  Password Modification - ESA                          *   DOC FILE
//*+File 127:  CHRYSLER utilities collection                        *   DOC FILE
//*+File 128:  LDS utilities - ISPF/VTAM cmds, CHIMP, SYSLOG scan   *   DOC FILE
//*+File 129:  Shared DASD Checkpoint mod - XA and OS/390           *   DOC FILE
//*+File 130:  Southwestern Public Service - Utilities colleciton   *   DOC FILE
//*+File 131:  SAR Security user exit - DMS/OS auto-restore exit    *   DOC FILE
//*+File 132:  First Nationwide Bank utilities - from George Ramas  *   DOC FILE
//*+File 133:  Alan Field Utility collection                        *   DOC FILE
//*+File 134:  Greg Price Utility collection - REVIEW, etc.         *#  DOC FILE
//*+File 135:  Greg Price Load Module library                       *#  DOC FILE
//*+File 136:  Howard Dean Utility collection - 2nd File            *   DOC FILE
//*+File 137:  Mod to list VSAM files in ISPF 3.4 dataset list      *   DOC FILE
//*+File 138:  Program called SYSTEM to report system info          *   DOC FILE
//*+File 139:  Dennis Longnecker Utilities + WHOHAS                 *   DOC FILE
//*+File 140:  Data Archival/Recovery System (DARS) DASD Managemnt  *   DOC FILE
//*+File 141:  SYS1.BRODCAST package from Tim Vanderwall            *   DOC FILE
//*+File 142:  Invoke other VTAM applications from within TSO       *   DOC FILE
//*+File 143:  Online IDCAMS application, CLISTs etc.               *   DOC FILE
//*+File 144:  VPS User Exit 14                                     *   DOC FILE
//*+File 145:  KERMIT for TSO - source                              *   DOC FILE
//*+File 146:  KERMIT for TSO - load library                        *   DOC FILE
//*+File 147:  ARCHIVER  All your non-VSAM datasets to 1 VSAM file  *   DOC FILE
//*+File 148:  Panvalet ISPF interface                              *   DOC FILE
//*+File 149:  UCLA utilities collection                            *   DOC FILE
//*+File 150:  ISPF Interactive Data Transmission Facility (XMIT)   *   DOC FILE
//*+File 151:  Load LISTCAT info into INFO/MVS database             *   DOC FILE
//*+File 152:  Harold Zbiegien Utilities - PSF emphasis, & others   *   DOC FILE
//*+File 153:  Harold Zbiegien - 3800 Character set samples         *   DOC FILE
//*+File 154:  Program to show SMP ELEMENTS from APPLY/ACCEPT run   *   DOC FILE
//*+File 155:  Dave North's REXX execs - go VB-255 to FB-80 etc.    *   DOC FILE
//*+File 156:  IEBASAP - source code                                *   DOC FILE
//*+File 157:  IEBASAP - sample reports                             *   DOC FILE
//*+File 158:  ISPF & REXX                                          *   DOC FILE
//*+File 159:  UCBFIND                                              *   DOC FILE
//*+File 160:  TSO CPS from Chuck Hoffman, etc.                     *   DOC FILE
//*+File 161:  Jim Marshall - ISPF interfaces to utilities          *   DOC FILE
//*+File 162:  XREFASM                                              *   DOC FILE
//*+File 163:  DUDA UTILITIES                                       *   DOC FILE
//*+File 164:  RESCUE SYSTEM                                        *   DOC FILE
//*+File 165:  RACF 1.7 SYSTEM                                      *   DOC FILE
//*+File 166:  Vinh Vu Utilities collection                         *#  DOC FILE
//*+File 167:  CATELLUS UTIL                                        *   DOC FILE
//*+File 168:  Bill Godfrey Utilities collection                    *#  DOC FILE
//*+File 169:  Kevin Williams Utilities collection                  *   DOC FILE
//*+File 170:  DUMPCSA program from Frank O'Quinn, USERS            *   DOC FILE
//*+File 171:  DISASM, TAPEMAP, SMFSPLIT, TPX, FX, SUTL, DLIUTILS   *   DOC FILE
//*+File 172:  David Cartwright's collection of Utilities           *   DOC FILE
//*+File 173:  Ted Bestani's collection - SMPETOOL etc etc          *   DOC FILE
//*+File 174:  TAPECOPY program from Aron Eisenpress                *   DOC FILE
//*+File 175:  PHILIPS Utilities from Clark Morris                  *   DOC FILE
//*+File 176:  ALGOL Compiler - moved to CBT Overflow Tape File 089 *   DOC FILE
//*+File 177:  Add OPCODES to the assembler as MACROS (MNEMAC lib)  *   DOC FILE
//*+File 178:  An IPCS interface for IDMS                           *   DOC FILE
//*+File 179:  Leonard Woren's MACLIB                               *   DOC FILE
//*+File 180:  Leonard Woren's TSO Commands                         *   DOC FILE
//*+File 181:  Leonard Woren's MVS Programs                         *   DOC FILE
//*+File 182:  PDS Command Package - Version 8.6.18.2 - PDSE Support*#  DOC FILE
//*+File 183:  Gilbert Saint-flour's collection of Utilities, etc.  *   DOC FILE
//*+File 184:  Tom Bryant's way of setting up IPCS                  *   DOC FILE
//*+File 185:  IKJTABLS Source Code and Auth Table handling tools   *#  DOC FILE
//*+File 186:  EMPTY                                                *   DOC FILE
//*+File 187:  CLIST Conversion Program:  FB-80 <---> VB-255        *   DOC FILE
//*+File 188:  IBM Source Tapes - a system to keep track of them    *   DOC FILE
//*+File 189:  IBM Source Tapes - sample report output - File 188   *   DOC FILE
//*+File 190:  VSMDUMP from Bob Styma - who used parts of CSA       *   DOC FILE
//*+File 191:  Started Task accnting information system, Walt Sapp  *   DOC FILE
//*+File 192:  Generalized Recovery Routine, ESTAEX, FRR, ARR etc.  *   DOC FILE
//*+File 193:  TCOPY - tape copying program - now 64K capable       *   DOC FILE
//*+File 194:  CUT-PASTE edit macros from Jim Marshall              *   DOC FILE
//*+File 195:  Eli Duttman's "simple but useful" CLISTs             *   DOC FILE
//*+File 196:  JES2 Exit Loader - an older and more imperfect one   *   DOC FILE
//*+File 197:  IMS 3.1 Mods from Rockwell - large collection        *   DOC FILE
//*+File 198:  JES2 Exit Dynamic Reloader Commands from Bob Break   *   DOC FILE
//*+File 199:  BLKSPTRK, CMDPGM, more programs from Dave Cole       *   DOC FILE
//*+File 200:  Collection of Utilities from TWA                     *   DOC FILE
//*+File 201:  IKJCT44B CLIST user exit to get system information   *   DOC FILE
//*+File 202:  Sample output from IEFU83 exit reporting I/O counts  *   DOC FILE
//*+File 203:  Produce STK Silo Eject cards from TMSGRW report      *   DOC FILE
//*+File 204:  MVS CROSS SYSTEM from Ken Tomiak & Joel Perlman      *   DOC FILE
//*+File 205:  MVS XSYS Doumentation in SCRIPT format               *   DOC FILE
//*+File 206:  DCOLLECT REXX execs from Linnea Nichols              *   DOC FILE
//*+File 207:  FSE a free version of old Full Screen Edit for TSO   *   DOC FILE
//*+File 208:  LSPC Command - Displays attributes of devices        *   DOC FILE
//*+File 209:  Hex Calculator written in REXX, by Art Tansky        *   DOC FILE
//*+File 210:  CICS Version of Cross System - moved CBT Overflow 310*   DOC FILE
//*+File 211:  CICS XSYS Documentation - moved, CBT Overflow 311    *   DOC FILE
//*+File 212:  DB2 CROSS SYSTEM - moved, CBT Overflow 312           *   DOC FILE
//*+File 213:  DB2 XSYS Documentation - moved, CBT Overflow 313     *   DOC FILE
//*+File 214:  MVS Control Blocks formatted for COBOL 2             *   DOC FILE
//*+File 215:  Two CLISTs to help you use SMP/E better              *   DOC FILE
//*+File 216:  Date Conversion and Manipulation Routine             *   DOC FILE
//*+File 217:  Disassembler - From Load modules to ASM code         *   DOC FILE
//*+File 218:  MPL and ASM Monitor under RMFMON, from Jim Cook      *   DOC FILE
//*+File 219:  REXX execs from Tony Forte                           *   DOC FILE
//*+File 220:  EDP Auditor Tool collection updated from Lee Conyers *   DOC FILE
//*+File 221:  EDP Auditor REXX tools updated from Lee Conyers      *   DOC FILE
//*+File 222:  EMPTY                                                *   DOC FILE
//*+File 223:  FREE Tape Management System - reports all mounts     *   DOC FILE
//*+File 224:  FREE Tape Management System - sample outputs         *   DOC FILE
//*+File 225:  OFFLOAD program - Dave Cole's original version       *   DOC FILE
//*+File 226:  COMPRSEQ - Dave Cole's compare program - orig vers   *   DOC FILE
//*+File 227:  TSO authorization code from CBT Company              *   DOC FILE
//*+File 228:  DFHSM Dataset Recovery - ISPF dialog                 *   DOC FILE
//*+File 229:  COPYMODS and other utilities for Tape Copying        *   DOC FILE
//*+File 230:  ISPF facilities demo from SHARE 66 presentation      *   DOC FILE
//*+File 231:  Source code for ISPF demo from File 230              *   DOC FILE
//*+File 232:  Convert MVS IOGEN deck into approx HCPRIO for VM     *   DOC FILE
//*+File 233:  GBHABEND Program - produces any ABEND code (S or U)  *   DOC FILE
//*+File 234:  New Disassembler by Dick Thornton-author of File 217 *#  DOC FILE
//*+File 235:  LPA Loader program - MODREP                          *   DOC FILE
//*+File 236:  ZAP to shorten LISTC LEV( ) display                  *   DOC FILE
//*+File 237:  Load Library CSECT Cross Reference report program    *   DOC FILE
//*+File 238:  ISPF Interactive Disassembler - Load Modules         *   DOC FILE
//*+File 239:  ISPF Interactive Disassembler - ISPF Panels          *   DOC FILE
//*+File 240:  ISPF Interactive Disassembler - ISPF Messages        *   DOC FILE
//*+File 241:  ISPF Interactive Disassembler - JCL                  *   DOC FILE
//*+File 242:  ISPF Interactive Disassembler - Formatted CBLKS      *   DOC FILE
//*+File 243:  ISPF Interactive Disassembler - Source Code          *   DOC FILE
//*+File 244:  UK GUIDE Tape Supplement - 1993A                     *   DOC FILE
//*+File 245:  UK GUIDE Tape - Norwich Union Insurance Supplement   *   DOC FILE
//*+File 246:  Issue Console Commands from Batch                    *   DOC FILE
//*+File 247:  Broadcast Manager Utilities to manage SYS1.BRODCAST  *#  DOC FILE
//*+File 248:  Jim Boysen Utility collection                        *   DOC FILE
//*+File 249:  Programs from Eileen Barkow - WMOD updated for z/OS  *   DOC FILE
//*+File 250:  DISPLAY GRS LONG RNAMES - Console Command            *   DOC FILE
//*+File 251:  ISPF EDIT MACRO collection from Paul Davis - 2       *   DOC FILE
//*+File 252:  JEFF KAPLAN Source Code                              *   DOC FILE
//*+File 253:  JEFF KAPLAN REXX execs                               *   DOC FILE
//*+File 254:  JEFF KAPLAN CNTL                                     *   DOC FILE
//*+File 255:  JEFF KAPLAN ISPPLIB                                  *   DOC FILE
//*+File 256:  JEFF KAPLAN ISPTLIB                                  *   DOC FILE
//*+File 257:  ZAPS to Linkage Editor to take BLKSIZE=32720         *   DOC FILE
//*+File 258:  WIN3270 - 3270 Device Tools - SAS/C source code      *   DOC FILE
//*+File 259:  WIN3270 - 3270 Device Tools - Load Modules           *   DOC FILE
//*+File 260:  Quick Disk Mapping program - Updated for 3390-9 etc. *   DOC FILE
//*+File 261:  Moved CMD1 Subsystem to File 296 of Overflow Tape    *   DOC FILE
//*+File 262:  PTFXREF Program                                      *   DOC FILE
//*+File 263:  MACROS from the UK G.U.I.D.E. Tape                   *   DOC FILE
//*+File 264:  LOOK program, DUDASD and JLOG. LOOKN for 64-bit addr *   DOC FILE
//*+File 265:  BF Goodrich LOGON exit                               *   DOC FILE
//*+File 266:  SS0104 TAPE MAP program - measures footages          *   DOC FILE
//*+File 267:  HETUTL Utility-read a tape-make AWS or HET file      *   DOC FILE
//*+File 268:  REXX function package to access VSAM files           *   DOC FILE
//*+File 269:  PL/I source code for ADVENTURE game                  *   DOC FILE
//*+File 270:  Washington State Utility Collection                  *   DOC FILE
//*+File 271:  Dynamic Proclib modification from Amdahl             *   DOC FILE
//*+File 272:  Mod to put Variable info into VTAM Logo              *   DOC FILE
//*+File 273:  TSO LOGON to a secondary JES2                        *   DOC FILE
//*+File 274:  Dynamic Proclib modification for ESA Release 4       *   DOC FILE
//*+File 275:  Mark Hedges programs - APFLIST, PACKOFF, etc.        *   DOC FILE
//*+File 276:  REXX to calculate CHECKSUM in ZAP statements         *   DOC FILE
//*+File 277:  Program to substitute values in JCL                  *   DOC FILE
//*+File 278:  ISPF package to keep track of SLSS subscription      *   DOC FILE
//*+File 279:  Documentation for File 278                           *   DOC FILE
//*+File 280:  Waterloo Script Documentation                        *   DOC FILE
//*+File 281:  Waterloo Script Load Modules                         *   DOC FILE
//*+File 282:  Waterloo Script Macro Library                        *   DOC FILE
//*+File 283:  Waterloo Script Memo to Users                        *   DOC FILE
//*+File 284:  Waterloo Script Source Code                          *   DOC FILE
//*+File 285:  Waterloo Script Hyphenation File                     *   DOC FILE
//*+File 286:  Waterloo Script Object Modules                       *   DOC FILE
//*+File 287:  Waterloo Script TSO Prompter                         *   DOC FILE
//*+File 288:  TSO Command Processor to invoke Waterloo Script      *   DOC FILE
//*+File 289:  PTF XREF REPORTS - Know BEFORE you RECEIVE...!!      *   DOC FILE
//*+File 290:  GPSAM - General Purpose Access Method                *   DOC FILE
//*+File 291:  CPU Instruction Speed monitor                        *   DOC FILE
//*+File 292:  Utility to convert CBT Doc File to HTML              *   DOC FILE
//*+File 293:  CKIEBGEN versions (copy program) - Warren Whitford   *   DOC FILE
//*+File 294:  VSAM Analysis TSO command called VSAMANAL            *   DOC FILE
//*+File 295:  A Heartfelt Essay about programming, by Dave Cole    *   DOC FILE
//*+File 296:  TSO Utilities. Use with PDS86 package or standalone. *   DOC FILE
//*+File 297:  GRS ISPF Interface from Mike Cleary                  *   DOC FILE
//*+File 298:  GTE Panvalet-PDS member backup system                *   DOC FILE
//*+File 299:  TAPEMAP program - Reads tape files in many formats   *   DOC FILE
//*+File 300:  Jim Marshall's enormous collection of TSO programs   *#  DOC FILE
//*+File 301:  A version of CDSCB which checks auth thru RACF       *   DOC FILE
//*+File 302:  Program from Mike Cleary--Show LPA and Linklist info *   DOC FILE
//*+File 303:  SIMTERM OS/390 from Alex Brodsky - VTAM pgms in TSO  *   DOC FILE
//*+File 304:  LSTVOL program source from Bruce Hogman              *   DOC FILE
//*+File 305:  LSTVOL assembly and linkedit printout                *   DOC FILE
//*+File 306:  The original version of TSSO from Bill Godfrey       *   DOC FILE
//*+File 307:  IEV90 program which invokes HLASM (ASMA90)           *   DOC FILE
//*+File 308:  Console display of system info from Alan Field       *   DOC FILE
//*+File 309:  ALGOL Compiler Source Code - a few modules incomplete*   DOC FILE
//*+File 310:  ALGOL Library Source Code                            *   DOC FILE
//*+File 311:  Dave Alcock's large Utilities collection             *   DOC FILE
//*+File 312:  Lionel Dyck Collection of Utilities.  A thru R       *#  DOC FILE
//*+File 313:  Lionel Dyck Collection of Utilities.  S thru TS      *#  DOC FILE
//*+File 314:  Lionel Dyck Collection of Utilities. TX thru Z       *#  DOC FILE
//*+File 315:  Dave Lees Utilities                                  *   DOC FILE
//*+File 316:  Jim Marshall's large collection of batch programs    *   DOC FILE
//*+File 317:  BOOKMANAGER management REXX exec from Tim Henness    *   DOC FILE
//*+File 318:  REXX exec to print from a tape in POFFLOAD Format    *   DOC FILE
//*+File 319:  SMF type 14 and 15 Report Program                    *   DOC FILE
//*+File 320:  DF/DSS Driver exits from John Sullivan               *   DOC FILE
//*+File 321:  COBOL Analyzer from Roland Schiradin & post processor*#  DOC FILE
//*+File 322:  TSO SLEEP programs (like the VM ones)                *   DOC FILE
//*+File 323:  REXX Function Package from Gerard Nicol              *   DOC FILE
//*+File 324:  Gerard Nicol package to access StorageTek API - HSC  *   DOC FILE
//*+File 325:  TSO Command Processor Programs from Wells Fargo      *   DOC FILE
//*+File 326:  Free FORTRAN G & H  - moved to CBT Overflow File 090 *   DOC FILE
//*+File 327:  Free RPG/F Compiler - moved to CBT Overflow File 091 *   DOC FILE
//*+File 328:  IGGPRE00, IGGPOST0 code from Aron Eisenpress         *   DOC FILE
//*+File 329:  Southern California Edison JES2 Exit 6               *   DOC FILE
//*+File 330:  ISPF dialog for SMF88, CICS CSD and COBANAL display  *   DOC FILE
//*+File 331:  COBOL subrtnes to set an area in W-S to an address   *   DOC FILE
//*+File 332:  Automatic Job Scheduler in MVS JES2 environment      *   DOC FILE
//*+File 333:  MVS Version of GZIP Compression - Load Module        *   DOC FILE
//*+File 334:  MVS Version of GZIP Compression - SOURCE .H          *   DOC FILE
//*+File 335:  MVS Version of GZIP Compression - SOURCE .C          *   DOC FILE
//*+File 336:  Utilities collection from Rice University            *   DOC FILE
//*+File 337:  Search entire system for PDS member name-Atalay Gul  *   DOC FILE
//*+File 338:  P390 Utilities from Gilbert Saint-flour              *   DOC FILE
//*+File 339:  JES2 Exit 5 - commands to better control job status  *   DOC FILE
//*+File 340:  DCM - Report statistics from 7980-3 controllers      *   DOC FILE
//*+File 341:  Code to load PLPA programs into CSA-structrd macros  *   DOC FILE
//*+File 342:  ISPF interface to Model 204 database-John Kalinich   *   DOC FILE
//*+File 343:  A VTOCLIST program - Peter Havercan & John Kalinich  *   DOC FILE
//*+File 344:  REXX execs and other tools from Joerg Berning        *   DOC FILE
//*+File 345:  Generalized MPF Exit - from Murray Nicholas          *   DOC FILE
//*+File 346:  JES2 Exits from Bob Break                            *   DOC FILE
//*+File 347:  MODLIST program-list original COBOL compile options  *   DOC FILE
//*+File 348:  Programs to list a PDS directory in order            *   DOC FILE
//*+File 349:  REXX update ISPF in-storage & stored command tables  *   DOC FILE
//*+File 350:  JES2 exits to convert JOB affnty JCL to WLM SCHENV=  *   DOC FILE
//*+File 351:  Programs to list the LE Level currently installed    *   DOC FILE
//*+File 352:  INTEL large collection - moved to Overflow File 301  *   DOC FILE
//*+File 353:  Collection of programs from Brian Cook - ETPS etc.   *   DOC FILE
//*+File 354:  Randy Hall's collection of utilities                 *   DOC FILE
//*+File 355:  KONCAT program from Kaiser Permanente                *   DOC FILE
//*+File 356:  NETSOL-VTAM multi-session mgr - updated for OS/390   *   DOC FILE
//*+File 357:  Carl Hafner's large collection of Utilities-PDSMATCH *   DOC FILE
//*+File 358:  SYSOUT archive package from Eric Bielefeld           *   DOC FILE
//*+File 359:  Utilities from Howard Dean and Bill Smith            *   DOC FILE
//*+File 360:  State of Wisconsin utilities - COMMAND, VOLS updated *   DOC FILE
//*+File 361:  Frank Johnston Utilities - CXYPSCAN, ZZRELINK        *   DOC FILE
//*+File 362:  Frank Johnston Utilities - Load Library              *   DOC FILE
//*+File 363:  ISPF Name Change Exit                                *   DOC FILE
//*+File 364:  Control Card Subsystem - CCSS                        *   DOC FILE
//*+File 365:  System to send files error-free using TSO XMIT       *   DOC FILE
//*+File 366:  World Clock and PDSADD prgms from Marvin Shaw        *   DOC FILE
//*+File 367:  ASCB and TSO User REXX commands from John Kalinich   *#  DOC FILE
//*+File 368:  Utility collection from James Williams               *   DOC FILE
//*+File 369:  Planning Research Corp collection of programs        *   DOC FILE
//*+File 370:  ZAPs-I/O counts in IEF285I msgs-see IEFU83,File 134  *   DOC FILE
//*+File 371:  Load Modules-programs on File 270-Washington State   *   DOC FILE
//*+File 372:  DYNALLOC Program from Ken MacKenzie                  *   DOC FILE
//*+File 373:  GTE TSO command - SAL - show dataset allocations     *   DOC FILE
//*+File 374:  SAS Programs to format IBM-produced SMF records      *   DOC FILE
//*+File 375:  SAS Programs to format Vendor SMF records            *   DOC FILE
//*+File 376:  ZDF Display Facility & utilities form David Marsden  *   DOC FILE
//*+File 377:  Exits and mods to run TCAS under SUB=MSTR: Ed Jaffe  *   DOC FILE
//*+File 378:  SORTTRAK to report on DFSORT SMF records: S.Kowalski *   DOC FILE
//*+File 379:  PROCLIB Cross Reference reports                      *   DOC FILE
//*+File 380:  REXX execs and other stuff from David McRitchie      *   DOC FILE
//*+File 381:  First Computer Services - programs and JES2 exits    *   DOC FILE
//*+File 382:  Paul Gillis utilities collection                     *   DOC FILE
//*+File 383:  INTEL CLISTS for Techinfo system on File 352         *   DOC FILE
//*+File 384:  Moved CDS programs to File 297 of Overflow Tape      *   DOC FILE
//*+File 385:  LPA Compare program from Jerry Lawson                *   DOC FILE
//*+File 386:  Salvador Carrasco EXECs and other programs           *   DOC FILE
//*+File 387:  Stony Brook PASCAL Distribution                      *   DOC FILE
//*+File 388:  David Cole's Job Scheduler package                   *   DOC FILE
//*+File 389:  QUEUE program for JES2 5.1, 5.2                      *   DOC FILE
//*+File 390:  Schudel QUEUE for ESA 5.2 thru OS390, early z/OS     *   DOC FILE
//*+File 391:  TRACE390 Instruction Trace Program from Robert Ngan  *   DOC FILE
//*+File 392:  QUEUE from Leonard Woren - JES2 4.2 and below        *   DOC FILE
//*+File 393:  RACFGRPS exec from Robert Lamerand & Ken MacKenzie   *   DOC FILE
//*+File 394:  Jan Jakubek collection of Utilites, and KSDSPACE Pgm *   DOC FILE
//*+File 395:  CATIND exec to do bulk cataloging for a new system   *   DOC FILE
//*+File 396:  FINDSTR exec to invoke ISRSUPC automatically in 3.4  *   DOC FILE
//*+File 397:  PACK and UNPK execs to do numeric conversions        *   DOC FILE
//*+File 398:  Generate system macro invocations more simply        *   DOC FILE
//*+File 399:  TSSO modifications, applications, and clists         *   DOC FILE
//*+File 400:  DYNAMASK program - for pre-dynamic UCB systems       *   DOC FILE
//*+File 401:  SPITBOL 360 Compiler and Library                     *   DOC FILE
//*+File 402:  SMF Display Consolidation from Multiple MVS systems  *   DOC FILE
//*+File 403:  Message Display Facility (UMSG) from Ugur Cilesiz    *   DOC FILE
//*+File 404:  TSSO for OS/390 and z/OS                             *#  DOC FILE
//*+File 405:  Defense Logistics Agency Exits and Utilities         *   DOC FILE
//*+File 406:  CQX (purge all jobs with same name), & FIND TSO cmds *   DOC FILE
//*+File 407:  DYNAMIC BLDL - by David Cole - For pre-ESA           *   DOC FILE
//*+File 408:  David Cole's Macros - needed for his other pgms      *   DOC FILE
//*+File 409:  Rob Scott's MXI monitor package - FB-80 members      *   DOC FILE
//*+File 410:  Rob Scott's MXI monitor package - load modules       *   DOC FILE
//*+File 411:  Rob Scott's utilities - source code and FB-80        *   DOC FILE
//*+File 412:  Rob Scott's utilities - load modules                 *   DOC FILE
//*+File 413:  Ashley Street's FADH Utility collection              *   DOC FILE
//*+File 414:  Convert printouts from machine control to ANSI       *   DOC FILE
//*+File 415:  RPF TSO-based ISPF-like editor, etc. Vers 1.8.1      *#  DOC FILE
//*+File 416:  Deluxe Check Printing - useful programs              *   DOC FILE
//*+File 417:  RACFADM - ISPF Dialog to make RACF admin easier      *#  DOC FILE
//*+File 418:  Combined Insurance collection of programs            *   DOC FILE
//*+File 419:  Dignus C language source and compiled assembler src  *   DOC FILE
//*+File 420:  Dignus Load Library - Compiled C to OS/390 utilities *   DOC FILE
//*+File 421:  XACORZAP program by Robert Budge (INCORZAP author)   *   DOC FILE
//*+File 422:  Don Marquardt collection of utilities                *   DOC FILE
//*+File 423:  Jeff Broido collection - TSO commands and utilities  *#  DOC FILE
//*+File 424:  VETAPE - 3420 to 3480 conversion program             *   DOC FILE
//*+File 425:  IEFUSI Exit from Mike Loos                           *   DOC FILE
//*+File 426:  Started Task Accounting, and Jobnames processor      *   DOC FILE
//*+File 427:  IHASTOW macro source                                 *   DOC FILE
//*+File 428:  Programs to extract and display control block info   *   DOC FILE
//*+File 429:  Allergan Utilities - from Paul Banks                 *   DOC FILE
//*+File 430:  McEvoy Utilities collection                          *   DOC FILE
//*+File 431:  Steve Bacher's utilities, packages, and offerings    *   DOC FILE
//*+File 432:  Thierry Falissard's selected programs and stuff      *   DOC FILE
//*+File 433:  Frank Clarke's collection of REXX execs, etc.        *   DOC FILE
//*+File 434:  Mark Zelden collection of Utilities and REXX execs   *#  DOC FILE
//*+File 435:  Frank Clarke's stuff FB-80-ized by Dave North (F155) *   DOC FILE
//*+File 436:  COMPCODE - sends NOTIFY & email for job completion   *   DOC FILE
//*+File 437:  Jan Jaeger utilities collection, including ZZSA      *   DOC FILE
//*+File 438:  Dan Snyder collection of structured macros & others  *   DOC FILE
//*+File 439:  PDSX Utility to scan all pds'es--from Volker Mielke  *   DOC FILE
//*+File 440:  Load Library for PDSX                                *   DOC FILE
//*+File 441:  2 Pgms for RACF from Brian Vogt - RESUME & RA#NAMES  *   DOC FILE
//*+File 442:  REVIVE Utility from Tetsuya Kimura (Kimu)            *   DOC FILE
//*+File 443:  Other Utilities from Tetsuya Kimura (Kimu)           *   DOC FILE
//*+File 444:  Ron Tatum pgms - create and read big blocks on tape  *   DOC FILE
//*+File 445:  Object Deck Disassembler from Chris Kendon           *   DOC FILE
//*+File 446:  COBOL Program which uses UNIX system services        *   DOC FILE
//*+File 447:  ENQMON from Rick Fochtman - GRS displays like MIM's  *   DOC FILE
//*+File 448:  Package to Insert Date into Global system variables  *   DOC FILE
//*+File 449:  AMDAHL Bookmanager Package                           *   DOC FILE
//*+File 450:  REXX exec to globally search for character strings   *   DOC FILE
//*+File 451:  Gary Scarcella REXX execs - CUTCLEAR, SUBCAN         *   DOC FILE
//*+File 452:  Dan Dalby's MVS-JES2 Utilities + STEPLIB, etc.       *   DOC FILE
//*+File 453:  Paul Moinil collection of Utilities: Index           *   DOC FILE
//*+File 454:  Paul Moinil collection of Utilities: Basic Material  *   DOC FILE
//*+File 455:  Paul Moinil collection of Utilities: Complementary   *   DOC FILE
//*+File 456:  Paul Moinil collection of Utilities: Additional      *   DOC FILE
//*+File 457:  Paul Moinil collection of Utilities: Demo/Games      *   DOC FILE
//*+File 458:  Paul Moinil collection of Utilities: CBT Extracted   *   DOC FILE
//*+File 459:  Paul Moinil collection of Utilities: Supplementary   *   DOC FILE
//*+File 460:  ISPF GUIDE Tape - ISPCLIB file                       *   DOC FILE
//*+File 461:  ISPF GUIDE Tape - Doc file                           *   DOC FILE
//*+File 462:  ISPF GUIDE Tape - Edit Macros                        *   DOC FILE
//*+File 463:  ISPF GUIDE Tape - Help file                          *   DOC FILE
//*+File 464:  ISPF GUIDE Tape - ISPFMACS                           *   DOC FILE
//*+File 465:  ISPF GUIDE Tape - JCL file                           *   DOC FILE
//*+File 466:  ISPF GUIDE Tape - ISPMLIB file                       *   DOC FILE
//*+File 467:  ISPF GUIDE Tape - ISPPLIB file                       *   DOC FILE
//*+File 468:  ISPF GUIDE Tape - ISPSLIB file                       *   DOC FILE
//*+File 469:  ISPF GUIDE Tape - Source file                        *   DOC FILE
//*+File 470:  ISPF GUIDE Tape - SVC99MAC file                      *   DOC FILE
//*+File 471:  ISPF GUIDE Tape - MACRO file                         *   DOC FILE
//*+File 472:  MURPHY - TSO command to display one-liners randomly  *   DOC FILE
//*+File 473:  CHKASVT program to find non-reusable ASIDs.          *   DOC FILE
//*+File 474:  LIBCLEAN - compare contents of pds's. Rob Wunderlich *   DOC FILE
//*+File 475:  Doc for the Large Block Interface (LBI) for tape     *   DOC FILE
//*+File 476:  LISP for MVS - moved back to CBT from Overflow Tape  *   DOC FILE
//*+File 477:  AWSUTIL Utility to Create AWS-format "tapes" on DASD *   DOC FILE
//*+File 478:  RAWSTAPE from Jan Jaeger                             *   DOC FILE
//*+File 479:  Broadcast Notices EDIT, BKMGR search, YAHTZEE        *   DOC FILE
//*+File 480:  Baldomero Castilla Utilities - Source Code           *   DOC FILE
//*+File 481:  Baldomero Castilla Utilities - Load Modules          *   DOC FILE
//*+File 482:  GDGCOPY Utility                                      *   DOC FILE
//*+File 483:  Thomas Ramseier collection of Utilities              *   DOC FILE
//*+File 484:  Cache Manager ISPF utility                           *   DOC FILE
//*+File 485:  VTAM application from Binyamin Dissen                *   DOC FILE
//*+File 486:  SETCLOCK program                                     *   DOC FILE
//*+File 487:  REXX to trap and display output from TSO Commands    *   DOC FILE
//*+File 488:  Jim Iannone Utilities for Production Control         *#  DOC FILE
//*+File 489:  Jim Iannone Utilities for Shared Medical Systems pkg *   DOC FILE
//*+File 490:  INSTASM - Assembler Macros for Reentrant code        *   DOC FILE
//*+File 491:  XMITMAIL - Lite XMITIP written in COBOL + BATCHART   *   DOC FILE
//*+File 492:  SHOWMVS 7.10, SHOWzOS 7.22, 7.23, 7.24 SHOWMVS 6.30  *#  DOC FILE
//*+File 493:  Utilities from Jim Connelley - VC, CRC32, C2F        *   DOC FILE
//*+File 494:  IKJEESX9 LISTBC exit - partial use of SYS1.BRODCAST  *   DOC FILE
//*+File 495:  Dynamic ISPF installs of products - from Tom Conley  *   DOC FILE
//*+File 496:  REXX exec to do LISTA (display allocations)          *   DOC FILE
//*+File 497:  CSVLLIX1 LLA Fetch exit example from A.Colombo       *   DOC FILE
//*+File 498:  Match Merge program from Craig Schneiderwent         *   DOC FILE
//*+File 499:  Utilities and RACF Panels from Ed Ross - prelim vers *   DOC FILE
//*+File 500:  Object decks that go with File 499                   *   DOC FILE
//*+File 501:  SNTP (Simple Network Time Protocol) Server - K.Clapp *   DOC FILE
//*+File 502:  ZAP to AMASPZAP program to eliminate AMA117D message *   DOC FILE
//*+File 503:  MBRLIST exec that runs under raw TSO                 *   DOC FILE
//*+File 504:  Software Inventory System                            *   DOC FILE
//*+File 505:  ASSIST Assembler - moved to Overflow Tape File 085   *   DOC FILE
//*+File 506:  REXX execs for handling SMP/E output                 *   DOC FILE
//*+File 507:  TPL V6.0 for MVS. Table Producing Language (pub dom) *   DOC FILE
//*+File 508:  EXCMD - Command Processor to execute CLISTs & REXX   *   DOC FILE
//*+File 509:  Application to web-enable the SHOWMVS command        *   DOC FILE
//*+File 510:  IEBLIST and SPACE dataset listers - Ricardo Paranhos *   DOC FILE
//*+File 511:  VSAM Space Analysis program from Geoffrey McIntyre   *   DOC FILE
//*+File 512:  ISPF CUT-PASTE - from Luc van Rompaey                *   DOC FILE
//*+File 513:  Tools to use OPERLOG in a sysplex, like SYSLOG       *   DOC FILE
//*+File 514:  ICHRTX00 special-purpose SAF exit - Larry Williams   *   DOC FILE
//*+File 515:  Alex Brodsky REXX functions (assembler) & ISPF stuff *   DOC FILE
//*+File 516:  CA-1 (TMS) program. Inquire VOLSER against CTSQSTS.  *   DOC FILE
//*+File 517:  XPL Compiler Generator System                        *   DOC FILE
//*+File 518:  Sam Knutson's Utilities - AUXBOOST, PUTPARM others   *   DOC FILE
//*+File 519:  Compare TMS (CA-1) volume data to IBM VTS vol status *   DOC FILE
//*+File 520:  REXX Functions from Robin Ryerse                     *   DOC FILE
//*+File 521:  Some EREP jobstreams from Tom Bryant                 *   DOC FILE
//*+File 522:  Write User SMF records from Application Programs     *   DOC FILE
//*+File 523:  General SMF Record Selection Program from Paul Dion  *   DOC FILE
//*+File 524:  EXCP Tape Functions in a Subroutine, from Ron Tatum  *   DOC FILE
//*+File 525:  Zap to CFMON free IBM utility to work past OS/390 2.6*   DOC FILE
//*+File 526:  Top Secret Security Administration package           *   DOC FILE
//*+File 527:  Matthew Stitt collection of programs & new LISTICAT  *   DOC FILE
//*+File 528:  J.McKown REXX--Look at LISTCAT and create IDCAMS srce*   DOC FILE
//*+File 529:  Programs to report CICS SMF records, more - M.Stitt  *   DOC FILE
//*+File 530:  PL/I program to format PL/I programs - Roy Gardiner  *   DOC FILE
//*+File 531:  Compound EXEC to detect DSNames, and other EXECs     *   DOC FILE
//*+File 532:  Extensive collection of Roscoe RPFs - Charles Hottel *   DOC FILE
//*+File 533:  AWS Tape,FKT<->Real Tape Conversion Utilities on MVS *   DOC FILE
//*+File 534:  SPACE command from Paul Dion                         *   DOC FILE
//*+File 535:  Powerful Concat, Alloc, Deconcat CMD from D.Sudibyo  *   DOC FILE
//*+File 536:  CA-Xcom and CA-Dispatch Report Distribution Extension*   DOC FILE
//*+File 537:  Entry and Exit Assembler macros                      *   DOC FILE
//*+File 538:  IPL Text for ZZSA (Standalone Utils) & ZZSA minidisk *   DOC FILE
//*+File 539:  DSNUSAGE - a mini-app in SAS and REXX from H. White  *   DOC FILE
//*+File 540:  PARM Checker Routine - for setting program options   *   DOC FILE
//*+File 541:  CCKD DASD compression routines to be run on MVS      *   DOC FILE
//*+File 542:  Alastair Gray-replacement for MCNVTCAT, other tools  *   DOC FILE
//*+File 543:  REXXs and Assembler Program to display System Info   *   DOC FILE
//*+File 544:  Material and Code for setting up Stanford PL360      *   DOC FILE
//*+File 545:  Stanford University PL360 EBCDIC distribution        *   DOC FILE
//*+File 546:  Documentation for Stanford PL360                     *   DOC FILE
//*+File 547:  Volker Bandke's Hercules Supplementary Utilities     *   DOC FILE
//*+File 548:  REXX Functions from Alfred Nikolyn                   *   DOC FILE
//*+File 549:  ISPF Dialog to display Unit Names - from Mark Baron  *   DOC FILE
//*+File 550:  Dan Snyder's Structured Macro Toolkit Set            *   DOC FILE
//*+File 551:  Exits to control users of the CONSOLE TSO command    *   DOC FILE
//*+File 552:  COBOL 2 and COBOL/MVS Analysis Program               *   DOC FILE
//*+File 553:  SUBMITC Edit Macro to submit jobs, with "smarts"     *   DOC FILE
//*+File 554:  "MVS Power Programming" ESA Coding Examples          *   DOC FILE
//*+File 555:  Solomon Santos Utility and Subroutine collection     *   DOC FILE
//*+File 556:  HTTP Socket Requestor - Get a text file from the web *   DOC FILE
//*+File 557:  Soundex Code Generator package from Jim Moore        *   DOC FILE
//*+File 558:  Dick Thornton's Large Collection of Assembler Code   *   DOC FILE
//*+File 559:  Dick Thornton's Large Collection of C-Language Code  *   DOC FILE
//*+File 560:  Dick Thornton's Large JCL Collection                 *   DOC FILE
//*+File 561:  Dick Thornton's CLIST Collection                     *   DOC FILE
//*+File 562:  Dick Thornton's EXECs, with PANELS and MESSAGES      *   DOC FILE
//*+File 563:  Dick Thornton's Large Collection of COBOL Code       *   DOC FILE
//*+File 564:  Dick Thornton's Documentation PDS'es                 *   DOC FILE
//*+File 565:  Dick Thornton's Classes - C, COBOL, Dump Reading     *   DOC FILE
//*+File 566:  Sam Bass Utilities collection-copy 256K block tapes  *   DOC FILE
//*+File 567:  Clark Jennings CSVLLIX2 exit and Module Fetch Stats  *   DOC FILE
//*+File 568:  TSO Games circa 1980 - contributed by Dick Thornton  *   DOC FILE
//*+File 569:  Rules and Notes for File 568 TSO Games               *   DOC FILE
//*+File 570:  MVS Tips and 'How-To's - Please contribute your own! *   DOC FILE
//*+File 571:  XMIT370 and RECV370 from Jim Morrison                *   DOC FILE
//*+File 572:  MVS zipping programs from Jeff Kaplan                *   DOC FILE
//*+File 573:  IEFUJV exit for System Symbolic substitution in JCL  *   DOC FILE
//*+File 574:  Some MVS 3.8-related items from Wolfgang Schaefer    *   DOC FILE
//*+File 575:  Read and Combine JES2 Spool Offload Files Directly   *   DOC FILE
//*+File 576:  Easy Handy Dataset Copying tool from Mick Sheehy     *   DOC FILE
//*+File 577:  Interesting REXX execs from Pergentino Arias         *   DOC FILE
//*+File 578:  General ISPF Table Handling Facility - Roy Gardiner  *   DOC FILE
//*+File 579:  BREAK and CONTINUE addon macros for HLASM Toolkit    *   DOC FILE
//*+File 580:  New CUT and PASTE macros from Michael R. Smith       *   DOC FILE
//*+File 581:  Complete Disaster Recovery System from Tom Hutchins  *   DOC FILE
//*+File 582:  TAPEMAP for MVS 3.8 (from File 299) and PDSLOAD      *   DOC FILE
//*+File 583:  PROFSET and EPROF packages from Jim Moore            *   DOC FILE
//*+File 584:  AUTOINIT (DASD Initialization in Batch)-Ugur Cilesiz *   DOC FILE
//*+File 585:  AWSSL - Dataset to SL AWS Tape Utility - Reed Petty  *   DOC FILE
//*+File 586:  Generalized ISPF Application Starter - Robin Murray  *   DOC FILE
//*+File 587:  Older VTOC command-improved features-MVS38 can run it*   DOC FILE
//*+File 588:  Automated System Shutdown from Sergey Makogonov      *   DOC FILE
//*+File 589:  HSCTOOL and Utilities - Philippe Leite - HERCMD      *   DOC FILE
//*+File 590:  Exercises from Knuth books in Assembler by C. Hottel *   DOC FILE
//*+File 591:  VM REXXFORM - REXX exec reformatter                  *   DOC FILE
//*+File 592:  DISPLAY function in Assembler programs - R.L. Rice   *   DOC FILE
//*+File 593:  ASMG                                                 *   DOC FILE
//*+File 594:  Dataset Display Facility (DDF) from Roy Gardiner     *   DOC FILE
//*+File 595:  LABEL macro to trace program execution - R.L. Rice   *   DOC FILE
//*+File 596:  SWP EDIT macro from David Chambers                   *   DOC FILE
//*+File 597:  MPF exit to issue START commands based on message id *   DOC FILE
//*+File 598:  Utilities from Richard Rice                          *   DOC FILE
//*+File 599:  REXX execs to summarize the ISPF environment         *   DOC FILE
//*+File 600:  SMF Exit and Programs to process TCP/IP SMF records  *   DOC FILE
//*+FILE 601:  MVS 3.8 version of QUEUE from Greg Price             *   DOC FILE
//*+FILE 602:  REXX execs from Mike Newell                          *   DOC FILE
//*+FILE 603:  QWIKSCAN pds scanning utility from Sebastian Welton  *   DOC FILE
//*+FILE 604:  Bell SNOBOL4 load module, disassembled SRC & OBJECT  *   DOC FILE
//*+FILE 605:  ACF2 to RACF password capture conversion aid         *   DOC FILE
//*+FILE 606:  AWSSL V19J+ - supports creation of HET and AWS tapes *   DOC FILE
//*+FILE 607:  A free IND$FILE version from Mike Rayborn - V1.0.6   *   DOC FILE
//*+FILE 608:  Free Space Lister TSO command from Bob Glover        *   DOC FILE
//*+FILE 609:  RESCUE systems, RACF tool, etc. from John Miller     *   DOC FILE
//*+FILE 610:  CHANGE71 and WTOR programs from somitcw              *   DOC FILE
//*+FILE 611:  REXX to submit job based on RC from previous job     *   DOC FILE
//*+FILE 612:  DUDASD, DSPACE, LOCATE (modules) SYSINCRD - A.Cheng  *#  DOC FILE
//*+FILE 613:  JCL to create and renew a RESCUE system from prod    *   DOC FILE
//*+FILE 614:  SHOWMVS and SHOWzOS Load Libraries FB-80 XMIT format *#  DOC FILE
//*+FILE 615:  ISPF and DYNALLOC macro libraries - Lionel Dyck      *   DOC FILE
//*+FILE 616:  Programs etc. from Nigel Thomas                      *   DOC FILE
//*+FILE 617:  REXX exec to produce SMF 30 Report from P. Berrios   *   DOC FILE
//*+FILE 618:  Cryptographic Interface from Pergentino Arias        *   DOC FILE
//*+FILE 619:  Dynamic Proclib modification for MVS 3.8J            *   DOC FILE
//*+FILE 620:  COBOL precompiler to extend COPY statements          *   DOC FILE
//*+FILE 621:  NPF Exits-print MVS datasets to PCL network printers *   DOC FILE
//*+FILE 622:  MATRIX package - easy interface to data spaces       *   DOC FILE
//*+FILE 623:  Automated System Shutdown and Automated IPL - H Zhou *   DOC FILE
//*+FILE 624:  FIND REXX to get all instances of a DSN. And TSOUCB. *#  DOC FILE
//*+FILE 625:  REXX to recatalog all datasets listed in a LISTCAT   *   DOC FILE
//*+FILE 626:  EN (display enqueues), JI (JES2 inits), CSA execs    *   DOC FILE
//*+FILE 627:  AUTOMAN Console Operations Package                   *   DOC FILE
//*+FILE 628:  Convert TCP/IP packet trace into TCPDUMP format      *   DOC FILE
//*+FILE 629:  An SNTP Server from Andrew Armstrong                 *   DOC FILE
//*+FILE 630:  DFDSS Move/Copy datasets in the foreground           *   DOC FILE
//*+FILE 631:  REXX to search a pds for strings                     *   DOC FILE
//*+FILE 632:  BASE64 conversion on MVS for emails - Gary Cherlet   *   DOC FILE
//*+FILE 633:  Updated DSPACE TSO command and ISPF dialog using it  *   DOC FILE
//*+FILE 634:  List all or some UCBs defined to your MVS system     *   DOC FILE
//*+FILE 635:  REXX to generate mass file renames                   *   DOC FILE
//*+FILE 636:  Execute TSO commands against datasets in LISTC LEV( )*   DOC FILE
//*+FILE 637:  Program to compare load modules - Nolan Young        *   DOC FILE
//*+FILE 638:  Send Email With Attachments from Hunter Zhou         *   DOC FILE
//*+FILE 639:  Set System Clock program from Hunter Zhou            *   DOC FILE
//*+FILE 640:  VPS Dynamic Separator Page Printer exit              *   DOC FILE
//*+FILE 641:  For MVS 3.8, Display maxcc in Job Notify Message     *   DOC FILE
//*+FILE 642:  OPERLOG scan program and SMP/E API interface - R.Hobt*   DOC FILE
//*+FILE 643:  Paul A. Scott macros and programs including CALENDAR *   DOC FILE
//*+FILE 644:  FUSION - change management package from J. Caughman  *   DOC FILE
//*+FILE 645:  Update to SHOWMVS to show if it's running authorized *   DOC FILE
//*+FILE 646:  CLIST to REXX conversion tool                        *   DOC FILE
//*+FILE 647:  An XML parser written in REXX from Andrew Armstrong  *   DOC FILE
//*+FILE 648:  GPSAM - General Purpose Access Method - H. Gilbert   *   DOC FILE
//*+FILE 649:  PDS2PDS utility from Mike Newell                     *   DOC FILE
//*+FILE 650:  A CSA Reporting and Tracking Tool from Mike Reeves   *   DOC FILE
//*+FILE 651:  Batch program to reset BWO flags from Chip Grantham  *   DOC FILE
//*+FILE 652:  A system-specific FIND utility from Richard Rice     *   DOC FILE
//*+FILE 653:  Dynamic Allocation utilities from Jim Harrison       *   DOC FILE
//*+FILE 654:  TSO FSI - Full Screen Interface from Tommy Sprinkle  *   DOC FILE
//*+FILE 655:  Catalog Cleanup Tool from David Kopischke            *   DOC FILE
//*+FILE 656:  Large collection of REXX utlities from Kannan Ak     *   DOC FILE
//*+FILE 657:  z/OS 1.4 RESCUE system build, from Kevin Mitts       *   DOC FILE
//*+FILE 658:  CRC check Assembler program and REXX that calls it   *   DOC FILE
//*+FILE 659:  Create P/390 DASD recipe - from Glenn Siegel         *   DOC FILE
//*+FILE 660:  Edit macro to check REXX execs for compile errors    *   DOC FILE
//*+FILE 661:  HOTRDR package to submit jobs, from Peter McFarland  *   DOC FILE
//*+FILE 662:  Automated system to convert CA-1 to FLEX-ES Faketape *   DOC FILE
//*+FILE 663:  Public Domain C Runtime Library                      *   DOC FILE
//*+FILE 664:  Date Conversion Routines and programs - Jay Moseley  *   DOC FILE
//*+FILE 665:  Field fixing routines from Jay Moseley               *   DOC FILE
//*+FILE 666:  Random number generator and COMB sort implementation *   DOC FILE
//*+FILE 667:  An RPG Tutorial from Jay Moseley - see File 327 also *   DOC FILE
//*+FILE 668:  OFFLOAD JES2 spool to datasets, from Hunter Zhou     *   DOC FILE
//*+FILE 669:  REXX save & retrieve variables, read/write VSAM-more *#  DOC FILE
//*+FILE 670:  REXX math function package                           *#  DOC FILE
//*+FILE 671:  ZOOM edit macro to "cursor retrieve" datasets        *   DOC FILE
//*+FILE 672:  NETINIT - issue system cmds after VTAM is up, etc.   *   DOC FILE
//*+FILE 673:  CCFDELET utility to delete datasets using JCL        *   DOC FILE
//*+FILE 674:  REXX-based TSO/ISPF toolkit from Robin Murray        *   DOC FILE
//*+FILE 675:  REXX execs pertaining to DB2 by Isaac Yassin         *   DOC FILE
//*+FILE 676:  VPS exits and other exits from Jim Marshall          *   DOC FILE
//*+FILE 677:  Parallel Sysplex Manager ISPF Application, M.Willemse*   DOC FILE
//*+FILE 678:  Write DFDSS dump to AWS-format file instead of a tape*   DOC FILE
//*+FILE 679:  Edit macro to construct a flowchart from JCL w/VISIO *   DOC FILE
//*+FILE 680:  Edit Macro, ISPF, REXX, PDSMAN courses - Bruce Koss  *   DOC FILE
//*+FILE 681:  Updated PL/I Execution Analyzer (PLEA) from Bob Styma*   DOC FILE
//*+FILE 682:  ESO command processor to display Esoterics           *   DOC FILE
//*+FILE 683:  BPXSTOP URL from IBM with their website infromation  *   DOC FILE
//*+FILE 684:  Rick Fochtman's PDSUPDTE program and misc. exits etc.*   DOC FILE
//*+FILE 685:  TXT2XML - Text to XML and back, from Pierre Delaunoy *   DOC FILE
//*+FILE 686:  SMFDUMP program                                      *   DOC FILE
//*+FILE 687:  Compare VVDS'es to referenced Catalogs               *   DOC FILE
//*+FILE 688:  IMS - Generate DBRC INIT commands automat. + ACBLIST *   DOC FILE
//*+FILE 689:  Peter Sawyer's famous paper on how to use SVC 26     *   DOC FILE
//*+FILE 690:  Cross Memory storage browser from Martin Kline       *   DOC FILE
//*+FILE 691:  READSEQ program to pick records, and BRODCAST stuff  *   DOC FILE
//*+FILE 692:  UATAPE tape mapping and copying utility-D. Merrifield*   DOC FILE
//*+FILE 693:  PDSCLEAN program: expand dir & empty PDS, empty PDSE *   DOC FILE
//*+FILE 694:  MACTREE macro from Mark Yuhas to do a binary search  *   DOC FILE
//*+FILE 695:  Useful REXX execs from J.D. Acevedo                  *   DOC FILE
//*+FILE 696:  System to imitate z/OS tape robot on FLEX-ES         *   DOC FILE
//*+FILE 697:  Reports for CICS/TS using Linux, Perl, and PostgreSQL*   DOC FILE
//*+FILE 698:  RACF reporting using Linux, Perl, and PostgreSQL     *   DOC FILE
//*+FILE 699:  ISPF/assembler SUBMIT edit macro, returns JOB id     *   DOC FILE
//*+FILE 700:  Useful ISPF REXX execs from Jim Haire                *   DOC FILE
//*+FILE 701:  DB2 Admin helpers from Marino Drazeta                *   DOC FILE
//*+FILE 702:  JES2 Mellon Mod equivalents at z/OS 1.6 level, etc.  *   DOC FILE
//*+FILE 703:  Program to convert Fujitsu FAL stats to ISPF stats   *   DOC FILE
//*+FILE 704:  DRDASD program to report status of your disk packs   *   DOC FILE
//*+FILE 705:  Performance tuning z/OS on Flex-ES using TSSO, etc.  *   DOC FILE
//*+FILE 706:  Create line charts from your data using SVG          *   DOC FILE
//*+FILE 707:  Customize ISPF 3.4 dataset lists according to users  *   DOC FILE
//*+FILE 708:  A very general MPF exit system with great capability *   DOC FILE
//*+FILE 709:  MPFCMD program from Bob Shannon                      *   DOC FILE
//*+FILE 710:  TSO commands to display DASD volume and dataset recds*   DOC FILE
//*+FILE 711:  Free LIBRARIAN program package                       *   DOC FILE
//*+FILE 712:  Send a file or send mail from CICS using TCP/IP      *   DOC FILE
//*+FILE 713:  The EMPTYPDS batch program to "empty" a pds          *   DOC FILE
//*+FILE 714:  FLEXCLI program to issue FLEXES commands on MVS      *   DOC FILE
//*+FILE 715:  Tape Erase Program                                   *   DOC FILE
//*+FILE 716:  QUERYENQ ISPF implementation from Jim Moore          *   DOC FILE
//*+FILE 717:  JumpList program package from Joseph Caughman        *   DOC FILE
//*+FILE 718:  TSO or JES/MSTR Logon, Garry Green-Futurity Software *   DOC FILE
//*+FILE 719:  Offline DASD Dump/Restore Program from Greg Smith    *   DOC FILE
//*+FILE 720:  Collection of Utilities from Bill Sweeney            *   DOC FILE
//*+FILE 721:  ChangeWiz - Program Change History - Shirley Huhtanen*   DOC FILE
//*+FILE 722:  FileWiz - File Compare Program from Shirley Huhtanen *   DOC FILE
//*+FILE 723:  Available Storage Displays, from Jim Moore           *   DOC FILE
//*+FILE 724:  HLASM Toolkit Improvements from Ed Jaffe             *   DOC FILE
//*+FILE 725:  CICS Auxiliary Trace Analyzer from Andrew Armstrong  *   DOC FILE
//*+FILE 726:  Generate VSAM DEFINE statements from VSAM file       *   DOC FILE
//*+FILE 727:  COPYVBS program using EXCP to read full 3390 tracks  *   DOC FILE
//*+FILE 728:  ICHPWX01 - RACF Password Quality Exit - Dave Jousma  *   DOC FILE
//*+FILE 729:  MAXITRAN REXX to script batch FTP from an MVS client *   DOC FILE
//*+FILE 730:  Program to run COBOL programs in batch under z/OS.e  *   DOC FILE
//*+FILE 731:  IKJTSOxx Parmlib info-Display/Chg XMIT parms-UCBDASD *#  DOC FILE
//*+FILE 732:  A familiar version of the WHOHAS command             *   DOC FILE
//*+FILE 733:  ALGOL 68C Cambridge University distribution - 1976   *   DOC FILE
//*+FILE 734:  Original PDS command, circa 1975. Still works.       *   DOC FILE
//*+FILE 735:  Edit macros from Tom Barthold                        *   DOC FILE
//*+FILE 736:  Perl Script from Mark Naughton to display IODF detail*   DOC FILE
//*+FILE 737:  Package to clear all DASD to X'00' after D/R Test    *   DOC FILE
//*+FILE 738:  Package to reallocate and reorg VSAM clusters        *   DOC FILE
//*+FILE 739:  Heavy Duty ISPF Commands Tool - by Ron Brown         *   DOC FILE
//*+FILE 740:  REXX Package to Execute SQL statements - Alan Wynne  *   DOC FILE
//*+FILE 741:  BASE64 encoding and decoding program in Assembler    *   DOC FILE
//*+FILE 742:  PDS member versioning tool from Bob Birdsall         *   DOC FILE
//*+FILE 743:  MODLIST program from Terry Miller                    *   DOC FILE
//*+FILE 744:  RACF "Rules" Enforcer - RRE 3.40                     *   DOC FILE
//*+FILE 745:  FM "File Formatter" program package                  *   DOC FILE
//*+FILE 746:  MVS and C Versions of Richard Tsujimoto's Parser     *   DOC FILE
//*+FILE 747:  System Logger Reader - from Mark Naughton            *   DOC FILE
//*+FILE 748:  BASE64 to text decoding; EMAIL Change Approval System*   DOC FILE
//*+FILE 749:  Gilbert Saint-flour Utilities adapted for MVS 3.8    *   DOC FILE
//*+FILE 750:  ISPF Productivity REXX EXECs by Ted MacNeil          *   DOC FILE
//*+FILE 751:  Tape Programs and Code from somitcw                  *   DOC FILE
//*+FILE 752:  ISPF Profile Dumping Utility from Robin Ryerse       *   DOC FILE
//*+FILE 753:  Robin Ryerse's REXX Function Package                 *   DOC FILE
//*+FILE 754:  ISPF Profile Searching Tool from Henrik Salminen     *   DOC FILE
//*+FILE 755:  Improved version of JRP which runs on MVS 3.8        *   DOC FILE
//*+FILE 756:  Powerful JCL preprocessor from Daniel Gaeta          *   DOC FILE
//*+FILE 757:  LOGGRASM Utility to track Assembler code execution   *   DOC FILE
//*+FILE 758:  LOADWORD package from Craig Schneiderwent            *   DOC FILE
//*+FILE 759:  CICS MQ api crossing exit to trace MQ api calls      *   DOC FILE
//*+FILE 760:  Ken Tomiak's z/OS and PC sysprog helper's package    *   DOC FILE
//*+FILE 761:  FINDALL package of REXX execs from Mark Baron        *   DOC FILE
//*+FILE 762:  DDNAME info to nullify OEM products, and JCL info    *   DOC FILE
//*+FILE 763:  Convert FB-80 Hex to 2 lines printable and back, more*   DOC FILE
//*+FILE 764:  Alex Kara Utility REXXes, etc.                       *   DOC FILE
//*+FILE 765:  Forms Based Authentication for HTTP Server under z/OS*   DOC FILE
//*+FILE 766:  Shared Spool Mods-"Mellon"-for JES2 z/OS 1.7 and 1.8 *   DOC FILE
//*+FILE 767:  REXX Frontends for TERSE and UNTERSE - D. Gaeta      *   DOC FILE
//*+FILE 768:  VM/CMS version of VTT2DISK, VTT2TAPE... from File 533*   DOC FILE
//*+FILE 769:  R. Prins' edit macros to convert code/text into HTML *   DOC FILE
//*+FILE 770:  Event Management System for Automation - Deru Sudibyo*   DOC FILE
//*+FILE 771:  ICSF (Cryptographic Services Facility) Monitor       *   DOC FILE
//*+FILE 772:  Stephen Bacher collected public work                 *   DOC FILE
//*+FILE 773:  Disassemble a Chunk of Storage - Arthur Fichtl       *   DOC FILE
//*+FILE 774:  Upgraded 80-byte compress program like CBT973-RL Rice*   DOC FILE
//*+FILE 775:  App under CICS COBOL to respond to HTTP requests     *   DOC FILE
//*+FILE 776:  RECV390 for the PC, zip file from Edgar Hofmann      *   DOC FILE
//*+FILE 777:  REXX exec to measure disk occupancy - Philippe Cochy *   DOC FILE
//*+FILE 778:  Programs to access GIMAPI (SMP/E API) using REXX     *   DOC FILE
//*+FILE 779:  COBOL pgm to access SDSF and do Symbolic JCL Substit.*   DOC FILE
//*+FILE 780:  Fullscreen interface using REXX without ISPF- D.Gaeta*   DOC FILE
//*+FILE 781:  Modification of IBM Sample RACSEQ program - J. McKown*   DOC FILE
//*+FILE 782:  Powerful Windows program to look at AWS-format tapes *   DOC FILE
//*+FILE 783:  PL/I Scientific Subroutine Package for 360 (OS)      *   DOC FILE
//*+FILE 784:  J.McKown implementations of a "Dataset List" web page*   DOC FILE
//*+FILE 785:  Substitute system symbols into JCL - K-H Doppelfeld  *   DOC FILE
//*+FILE 786:  Separate CBTF1.zip file into separate HTML datasets  *   DOC FILE
//*+FILE 787:  Send data to remote hosts in multi-Sysplex environmnt*   DOC FILE
//*+FILE 788:  MA1K Application for MQ series by C.Schneiderwent    *   DOC FILE
//*+FILE 789:  Batch job to automate and email IBM's SCRT report    *   DOC FILE
//*+FILE 790:  SRS (Sysout Retrieval Services) pkg from Dave Danner *   DOC FILE
//*+FILE 791:  STORAGE OBTAIN/RELEASE REXX Function - Anthony Rudd  *   DOC FILE
//*+FILE 792:  DISKMAP for z/OS EAV support-earlier z/OS too.       *   DOC FILE
//*+FILE 793:  R.L.Rice updates for SDF 3.4 - alpha                 *   DOC FILE
//*+FILE 794:  RXMEM REXX function - beta version - from D.F.Gaeta  *   DOC FILE
//*+FILE 795:  HTTP Server in Assembler--ALPHA--needs expert to fix.*   DOC FILE
//*+FILE 796:  Lindy Mayfield Utilities                             *   DOC FILE
//*+FILE 797:  LWATMGR, LLWA, TSUB. Fix your TSO session auth tables*#  DOC FILE
//*+FILE 798:  Job Scheduler written in COBOL from Kevin Dengsong   *   DOC FILE
//*+FILE 799:  SMF Type 30 post processor written in COBOL          *   DOC FILE
//*+FILE 800:  RECEIVE/UNXMIT tool written in REXX for the PC       *   DOC FILE
//*+FILE 801:  Create Browseable Bar Charts in Silverlight format   *   DOC FILE
//*+FILE 802:  DELINK program in C from Jason Winter                *   DOC FILE
//*+FILE 803:  ISPF Macro collection                                *   DOC FILE
//*+FILE 804:  TAPEMAP reworked with JUMP instructions              *   DOC FILE
//*+FILE 805:  Establish SNMP sub-agent, and an EMC monitoring STC..*   DOC FILE
//*+FILE 806:  SMF 110 CICS Performance Monitor Analysis Tools      *   DOC FILE
//*+FILE 807:  HFSELECT and SUPRDUMP from M.Karlin and others       *   DOC FILE
//*+FILE 808:  PC un-XMIT in object REXX. ZIP file from File 800.   *   DOC FILE
//*+FILE 809:  Fixed DITTO from Richard L. Rice                     *   DOC FILE
//*+FILE 810:  Fixed ONSCREEN rework of FM (File 745) from R.L. Rice*   DOC FILE
//*+FILE 811:  Fixed LIBRARIAN from Richard L. Rice (was File 711)  *   DOC FILE
//*+FILE 812:  Fixed DISASM from Richard L. Rice (was on File 171)  *   DOC FILE
//*+FILE 813:  Fixed SUTL from Richard L. Rice (was on File 171)    *   DOC FILE
//*+FILE 814:  Old XEPHON MVS articles in zipped text - from E.Vogt *   DOC FILE
//*+FILE 815:  SRCHE multiple dataset search facility - Bob Glover  *   DOC FILE
//*+FILE 816:  Instant change of Default Notices number in ACCT/SYNC*   DOC FILE
//*+FILE 817:  FIXCATLG program - Recatalog datasets on DASD volumes*   DOC FILE
//*+FILE 818:  Assembler stub to call AMODE64 module from COBOL pgm *   DOC FILE
//*+FILE 819:  RACF Exit Dynamic UPDATE/DELETE/REMOVE Facility "ICH"*   DOC FILE
//*+FILE 820:  64/20 Assembly Language Development Platform-R.Harper*   DOC FILE
//*+FILE 821:  CC - ISPF Edit Macro to plug values into a Skeleton  *   DOC FILE
//*+FILE 822:  Softcap CPU Utilization and Measuring Tool for LPARs *   DOC FILE
//*+FILE 823:  Expand ISPF command shell panel to retain 20 commands*   DOC FILE
//*+FILE 824:  ISPF-based VTOC zapper that interfaces with RACF     *   DOC FILE
//*+FILE 825:  SSL Handshake diagnosis program                      *   DOC FILE
//*+FILE 826:  TSO command to make a job cancelable or non-swap etc.*#  DOC FILE
//*+FILE 827:  RACF Profiling Utility from John C. Miller           *   DOC FILE
//*+FILE 828:  Updated DELAY program from somitcw                   *   DOC FILE
//*+FILE 829:  TIDYASM program to neaten Assembler source code      *   DOC FILE
//*+FILE 830:  XEPHON MVS articles from 07/1987 thru 12/1996 EBCDIC *   DOC FILE
//*+FILE 831:  Dynamic Concatenation TSO command                    *   DOC FILE
//*+FILE 832:  Package to Print MVS files on TCPIP printers         *   DOC FILE
//*+FILE 833:  Label Aid Facility to look at COBOL programs in ISPF *   DOC FILE
//*+FILE 834:  Dataset Migration Allocation Aid facility+Misc REXX's*   DOC FILE
//*+FILE 835:  Programs and REXX to display the PPT under ISPF & TSO*   DOC FILE
//*+FILE 836:  Xephon MVS Update programs gotten to work on z/OS    *#  DOC FILE
//*+FILE 837:  Exits. Inform TSO user about pending files to RECEIVE*   DOC FILE
//*+FILE 838:  Dynamic Allocation macro that generates SVC99 params *   DOC FILE
//*+FILE 839:  Long Parameters in EXEC - JCL symbolic substitution  *   DOC FILE
//*+FILE 840:  ICSF KGUP exit to make updates dependent on RACF     *   DOC FILE
//*+FILE 841:  Run CA-Optimized COBOL pgms with CA-Optimizer removed*   DOC FILE
//*+FILE 842:  Create multiple XMIT-format datasets on MVS by prefix*   DOC FILE
//*+FILE 843:  Panel recovery of HSM datasets from ISPF 3.4 or 6    *   DOC FILE
//*+FILE 844:  ENQWATCH - Long running task - announce ENQ conflicts*   DOC FILE
//*+FILE 845:  HOSTCMD, SYSCMD, RUNAUTH from G. Bliznets            *   DOC FILE
//*+FILE 846:  TRK0SAVE, TRK0UPD, EOFDISK from somitcw. + TRK0INIT. *#  DOC FILE
//*+FILE 847:  Development of COPYMODS program thru 86 versions     *#  DOC FILE
//*+FILE 848:  LIBSPOOL                                             *   DOC FILE
//*+FILE 849:  Display TSO Users - DT cmd, Display Active - DA cmd  *   DOC FILE
//*+FILE 850:  RAKF Security System for MVS 3.8                     *   DOC FILE
//*+FILE 851:  RMMCOPY - generate JCL to copy tapes with 256K blocks*   DOC FILE
//*+FILE 852:  GCCMVS - GCC C-Compiler and Library - 3.2.3 MVS 9.0  *   DOC FILE
//*+FILE 853:  GCCMVS - GCC C-Compiler and Library - 3.4.6 MVS 1.0  *   DOC FILE
//*+FILE 854:  Free Instructional Papers from "The Trainer's Friend"*   DOC FILE
//*+FILE 855:  Excel spreadsheet to figure DASD sizes               *   DOC FILE
//*+FILE 856:  Shared Spool Mods (Mellon Mods) for z/OS 1.9 - 1.13  *   DOC FILE
//*+FILE 857:  Interactive EREP Report from Marco Serafini          *   DOC FILE
//*+FILE 858:  Clemson University Structured Macro Library          *   DOC FILE
//*+FILE 859:  Clemson University Service Processor Source Modules  *   DOC FILE
//*+FILE 860:  Gerhard Postpischil miscellaneous source code        *   DOC FILE
//*+FILE 861:  Gerhard Postpischil macro library                    *   DOC FILE
//*+FILE 862:  Gerhard Postpischil more code                        *   DOC FILE
//*+FILE 863:  IKJEFF10 TSO SUBMIT exit - J. Callihan               *   DOC FILE
//*+FILE 864:  John McKown UNIX Shell Commands for z/OS             *   DOC FILE
//*+FILE 865:  Free zip/unzip (MINIZIP and MINIUNZ) for MVS         *   DOC FILE
//*+FILE 866:  BSPUFI - C SQL-DB2-TSO Processor/Executor/Monitor    *   DOC FILE
//*+FILE 867:  RDW2VB (add BDWs) and RECU2AWS programs from somitcw *   DOC FILE
//*+FILE 868:  DISKCOMP trk-by-trk compare of 2 offline DASD packs  *   DOC FILE
//*+FILE 869:  Getmain/Freemain Trace with IPCS support             *   DOC FILE
//*+FILE 870:  HTTP REXX scripts from Rick Turnbull                 *   DOC FILE
//*+FILE 871:  Un-XMIT for Android - from Roland Scholz             *   DOC FILE
//*+FILE 872:  z/OS port of Julian Seward's bzip2 library - R.Scholz*   DOC FILE
//*+FILE 873:  Macros for ULUT-based UCB scans. 64-bit ULUT, Type 3.*   DOC FILE
//*+FILE 874:  HELP members for some programs in the CBT collection *   DOC FILE
//*+FILE 875:  ALGOL 68C from Chris Cheney, et al                   *   DOC FILE
//*+FILE 876:  ALGOL F v2.1 source and executables from T.Armstrong *   DOC FILE
//*+FILE 877:  MAKE tool for z/OS. Includes V/B/E macros.           *   DOC FILE
//*+FILE 878:  TSO BURN command newly rewritten by Joe Reichman     *   DOC FILE
//*+FILE 879:  TSOFIND from Tom Hall. Also fixed for z/OS.          *   DOC FILE
//*+FILE 880:  Extension of ADRDSSU to manage dumps in a network    *   DOC FILE
//*+FILE 881:  Modification to Excel format Julian Calendar from CBT*   DOC FILE
//*+FILE 882:  Console Automation Tools                             *#  DOC FILE
//*+FILE 883:  Manage DFHSM migration in a small environment        *   DOC FILE
//*+FILE 884:  Abe Kornelis macro library and other tools           *#  DOC FILE
//*+FILE 885:  Disassembler with Jump Instructions-from Albert Cheng*#  DOC FILE
//*+FILE 886:  Init large quantities of DASD volumes - Ed Petka     *   DOC FILE
//*+FILE 887:  Scott Vetter collection of mods and pgms for MVS 3.8J*   DOC FILE
//*+FILE 888:  MVSEXP - Browse z/OS system info with a web browser  *   DOC FILE
//*+FILE 889:  Hercules 3.12 - 64 bit for Windows - ready to use    *   DOC FILE
//*+FILE 890:  SIMULA 360/370 Compiler, Library, and PDF Format Doc *   DOC FILE
//*+FILE 891:  REXX to flowchart, graph structure of COBOL programs *   DOC FILE
//*+FILE 892:  TERSE pgms - DOS, OS/2, AIX, Windows, Linux, Mac OS-X*   DOC FILE
//*+FILE 893:  SMFLOG - SMF Type 4, 20, 35 - Logons, Logoffs, Inits *   DOC FILE
//*+FILE 894:  Collection of helpful REXX execs for OE from R.Zenuk *   DOC FILE
//*+FILE 895:  STEMEDIT update and related mods to File 183-R.Nowak *   DOC FILE
//*+FILE 896:  Misc. TSO Tools - from SHARE 1993 - still useful     *   DOC FILE
//*+FILE 897:  Port of SQLITE 3.8 to z/OS - File 923 is newer...    *   DOC FILE
//*+FILE 898:  Alex Kara collected works                            *   DOC FILE
//*+FILE 899:  TSO command DACEE, and callable version              *#  DOC FILE
//*+FILE 900:  MD5 and SHAx calculation programs for MVS and z/OS   *#  DOC FILE
//*+FILE 901:  ASSIST assembler presented by Jay Moseley            *   DOC FILE
//*+FILE 902:  Callable Date Conversion routines from Jay Moseley   *   DOC FILE
//*+FILE 903:  Field formatting routines from Jay Moseley           *   DOC FILE
//*+FILE 904:  IBM Connect:Direct add-ons and exits from A. Cieri   *   DOC FILE
//*+FILE 905:  Common Storage info about selected PARMLIB members   *   DOC FILE
//*+FILE 906:  STLSPACE (nice LSPACE command) from Steve McColley   *   DOC FILE
//*+FILE 907:  XiFrame XMI Explorer for the PC, from Nick Barnes    *   DOC FILE
//*+FILE 908:  ISPF Client Server Local Dialogs and Facilities      *   DOC FILE
//*+FILE 909:  GSMAIL - package to email CA-Dispatch reports        *   DOC FILE
//*+FILE 910:  NoSQLz DBMS from Thierry Falissard                   *   DOC FILE
//*+FILE 911:  Problems from "The REXX Language on TSO" - Gargiulo  *   DOC FILE
//*+FILE 912:  Don Higgins macro collections and programs           *   DOC FILE
//*+FILE 913:  Send z/OS SMS free space data to an iPhone           *   DOC FILE
//*+FILE 914:  Shared Spool Mods (Mellon Mods) for z/OS 2.1         *   DOC FILE
//*+FILE 915:  Generic Tracker Facility - ISPF dialog, EAV planning *   DOC FILE
//*+FILE 916:  Xmit Manager - installable on Win-64-bit - RAR format*   DOC FILE
//*+FILE 917:  SELECTIT - Extremely powerful file manipulaton & copy*   DOC FILE
//*+FILE 918:  Port of BASH 4.2 to z/OS - executables only          *   DOC FILE
//*+FILE 919:  Port of BASH 4.2 to z/OS - with source & executables *   DOC FILE
//*+FILE 920:  Generate DEFINE statements from existing VSAM file   *   DOC FILE
//*+FILE 921:  ISPFDSN utility. Allocate ISPF datasets in native TSO*   DOC FILE
//*+FILE 922:  DSPACE TSO command tailored for EAV volumes          *   DOC FILE
//*+FILE 923:  SQLITE 3.8.7 for z/OS, ported by John McKown         *   DOC FILE
//*+FILE 924:  LDSI list information about datasets (from ISPF 3.4) *   DOC FILE
//*+FILE 925:  ENL - enlarge non-VSAM and VSAM datasets             *   DOC FILE
//*+FILE 926:  AMORT - payment schedule pgm from Phil Polchinski    *#  DOC FILE
//*+FILE 927:  PRMEVSAM program from Steve Wentworth                *   DOC FILE
//*+FILE 928:  Adaptation of regex.h header file to COBOL copybooks *   DOC FILE
//*+FILE 929:  REALNAME REXX function for GDG's etc.                *   DOC FILE
//*+FILE 930:  Support material for Phil Polchinski Calendar File   *   DOC FILE
//*+FILE 931:  Code from "TSO CLIST to TSO REXX Conversion Handbook"*   DOC FILE
//*+FILE 932:  Calendar File (EBCDIC) - LRECL=35                    *   DOC FILE
//*+FILE 933:  Calendar File (ASCII text with Doc - zipped)         *   DOC FILE
//*+FILE 934:  DFSORT job to produce maximum Calendar File          *   DOC FILE
//*+FILE 935:  SQLITE 3.8.11 for z/OS, ported by John McKown        *   DOC FILE
//*+FILE 936:  Port of NAWK (New AWK) to z/OS from John McKown      *   DOC FILE
//*+FILE 937:  EMPTY                                                *   DOC FILE
//*+FILE 938:  SSINFO program                                       *   DOC FILE
//*+FILE 939:  PCRE2-Perl-Compatible Regular Expressions 10.34A z/OS*#  DOC FILE
//*+FILE 940:  Program to list libraries controlled by LLA          *   DOC FILE
//*+FILE 941:  G. Bliznets utilities - AMBLIST, DDL, ISP<->CSV      *   DOC FILE
//*+FILE 942:  Display VSAM info from ISPF 3.4. Create DEFINE's     *#  DOC FILE
//*+FILE 943:  Xephon CICS Update articles - Sep 87 thru Jan 93     *   DOC FILE
//*+FILE 944:  Xephon SNA Update articles - Mar 91 thru Dec 92      *   DOC FILE
//*+FILE 945:  Xephon VSAM Update articles - Apr 91 thru Jan 93     *   DOC FILE
//*+FILE 946:  Xephon VM Update articles - Sep 87 thru Jan 93 (SDS) *   DOC FILE
//*+FILE 947:  Xephon VSE Update articles - Mar 91 thru Dec 92 (SDS)*   DOC FILE
//*+FILE 948:  CICS and DB2 SMF execs - PDS2SEQ                     *   DOC FILE
//*+FILE 949:  PDSUR - IEHMOVE substitute - easier to use           *   DOC FILE
//*+FILE 950:  Norbert Haas REXX Utilities - AUTOMAT etc.           *#  DOC FILE
//*+FILE 951:  GDGP Utility for GDG's from Nick Light               *   DOC FILE
//*+FILE 952:  Valuable OS/360 Documents in PDF format              *   DOC FILE
//*+FILE 953:  John Gateley macro library and utilities             *   DOC FILE
//*+FILE 954:  Make addrspce CANCELABLE, FORCIBLE, NON-*** and more *   DOC FILE
//*+FILE 955:  z/OS Remote Syslog Facility - John C. Miller         *   DOC FILE
//*+FILE 956:  DSREF reports to show dataset accesses by userid etc *   DOC FILE
//*+FILE 957:  IEBUPDTX program, macros, etc. from Seymour Metz     *   DOC FILE
//*+FILE 958:  Manipulate and Display the TSO Relogon Buffer        *   DOC FILE
//*+FILE 959:  Release unused DASD space without opening datasets   *#  DOC FILE
//*+FILE 960:  REXX execs to use & demonstrate many useful z/OS APIs*   DOC FILE
//*+FILE 961:  Additional ISPF Edit and View commands, Yves Colliard*   DOC FILE
//*+FILE 962:  ISPF Interface for Mounting and Unmounting UNIX files*   DOC FILE
//*+FILE 963:  Dynamic ISPF file allocation pkg from Al Ferguson    *   DOC FILE
//*+FILE 964:  Display VSAM dataset details ISPF 3.4 or PDS LISTC/F *#  DOC FILE
//*+FILE 965:  SQLITE 3.21.0 for z/OS, ported by John McKown        *   DOC FILE
//*+FILE 966:  HLASM - TSO prompter to run High-Level Assembler     *   DOC FILE
//*+FILE 967:  CBT Usermods Collection for ISPF (CUCI)              *   DOC FILE
//*+FILE 968:  Show PARMLIB concatenation in ISRDDN format          *   DOC FILE
//*+FILE 969:  PDSEGEN multi-utility for PDSE v2 member generations *#  DOC FILE
//*+FILE 970:  Ken Tomiak's version of RCNVTCAT (batch job)         *   DOC FILE
//*+FILE 971:  Program EMPTYTST: is a dataset or pds member empty?  *   DOC FILE
//*+FILE 972:  GENIE edit macro - like IBM's MODEL but extensible   *   DOC FILE
//*+FILE 973:  WATFIV (Fortran) compiler and library                *   DOC FILE
//*+FILE 974:  Rewrite of TSSO/AOF using enhanced console support   *   DOC FILE
//*+FILE 975:  Count & Statistics of Reserved Words in a COBOL pgm  *   DOC FILE
//*+FILE 976:  USYNC command: ADD/DEL userid entry in Broadcast DS  *   DOC FILE
//*+FILE 977:  URL Table for MOSHIX YouTube Mainframe Videos        *#  DOC FILE
//*+FILE 978:  Beta version of GENIE edit macro - from K. Tomiak    *   DOC FILE
//*+FILE 979:  ZZSA Tutorial Package - complete setup to learn ZZSA *   DOC FILE
//*+FILE 980:  ZAP for TASID 5.21 to fix Initiator Display (4)      *   DOC FILE
//*+FILE 981:  REXX Utilities from Larry Zuckett                    *   DOC FILE
//*+FILE 982:  JOL from Clement Clarke                              *   DOC FILE
//*+FILE 983:  Mainframe Software Installation Customizer (MSIC)    *   DOC FILE
//*+FILE 984:  Ken Tomiak REXX execs                                *   DOC FILE
//*+FILE 985:  REXX execs from Marius Lewin                         *#  DOC FILE
//*+FILE 986:  A TSO PUTLINE programming interface - W. Jensen      *   DOC FILE
//*+FILE 987:  Programs from NaSPA VIP tape, fixed to run on z/OS   *   DOC FILE
//*+FILE 988:  OS/360 Storage Zap - original program from S. Metz   *   DOC FILE
//*+FILE 989:  FINDMEM package. Give member name, find the datasets *   DOC FILE
//*+FILE 990:  ISPF Developer Tips and Tricks - doc and code - V1.7 *#  DOC FILE
//*+FILE 991:  From John Hamlet - SVCUPDTE                          *   DOC FILE
//*+FILE 992:  Example code to put "security" in TSO commands       *#  DOC FILE
//*+FILE 993:  COBOL program to read many types of SMF records      *   DOC FILE
//*+FILE 994:  TSO commands - Display entire load modules in hex    *#  DOC FILE
//*+FILE 995:  WYLBUR and accessory tools for MVS 3.8 and MVS/SP    *   DOC FILE
//*+FILE 996:  Slaten pkgs-Loadlib Scanner, Rexx Toolkit, String pkg*#  DOC FILE
//*+FILE 997:  ISPF Git Interface - ZIGI                            *#  DOC FILE
//*+FILE 998:  RACFROD reporting system for RACF                    *#  DOC FILE
//*+FILE 999   EMPTY                                                *   DOC FILE
//*+FILE1000   EMPTY                                                *   DOC FILE
```
