```
//***FILE 688 is from Larry Altman and contains a slightly          *   FILE 688
//*           modified REXX program from Larry Prestosa, called     *   FILE 688
//*           RCNGNINT.  This program can be used to generate DBRC  *   FILE 688
//*           INIT commands in order to transfer database           *   FILE 688
//*           registration information from one recon to another    *   FILE 688
//*           or to create database registration commands which     *   FILE 688
//*           may have been lost.  It has been used with IMS V6     *   FILE 688
//*           and V7 RECONs.                                        *   FILE 688
//*                                                                 *   FILE 688
//*           A second product has been included here, called       *   FILE 688
//*           ACBLIST, which was authored by Dougie Lawson, and     *   FILE 688
//*           which was included with his permission.               *   FILE 688
//*           (Updated 2009 Apr 22 for IMS v10 and v11 by Dougie    *   FILE 688
//*           Lawson.  And IMS V12.  See members ACBLIST (newest)   *   FILE 688
//*           and ACBLISTO (older) and ACBLISTP (still older).)     *   FILE 688
//*             (Last update:  Jun 14, 2011)                        *   FILE 688
//*                                                                 *   FILE 688
//*     Larry Altman                                                *   FILE 688
//*     email:  larrytheotter@highstream.net                        *   FILE 688
//*                                                                 *   FILE 688
//*   Description of contents of this file:                         *   FILE 688
//*                                                                 *   FILE 688
//*     There are 2 sets of product included here.                  *   FILE 688
//*                                                                 *   FILE 688
//*     1. Rexx exec 'RCNGNINT' and associated members.- no         *   FILE 688
//*        changes at this time.                                    *   FILE 688
//*                                                                 *   FILE 688
//*     2. Assembler program 'ACBLIST' and associated members.      *   FILE 688
//*                                                                 *   FILE 688
//*     The 'DBRCINIT' rexx program, since rename to RCNGNINT,      *   FILE 688
//*     was obtained from an old XEPHON article dated 1996, by      *   FILE 688
//*     Larry Prestosa.  As far as I know, he is the original       *   FILE 688
//*     author of this program.  I have made some small             *   FILE 688
//*     additions to the program, which are in my usual             *   FILE 688
//*     lowercase characters.  I have made no changes to the        *   FILE 688
//*     input record processing, except for:                        *   FILE 688
//*                                                                 *   FILE 688
//*     line 52: /* PARSE VAR INRECORD 3 INRECORD.TYPE 11 */        *   FILE 688
//*     line 53:    inrecord.type=word(inrecord,1)                  *   FILE 688
//*                                                                 *   FILE 688
//*     I have made some additions to the output processing of      *   FILE 688
//*     the program as indicated at the end of the comments         *   FILE 688
//*     section in the program.                                     *   FILE 688
//*                                                                 *   FILE 688
//*     I have included the me() function as an additional          *   FILE 688
//*     member for those who wish to have it as part of the         *   FILE 688
//*     program (line 35).                                          *   FILE 688
//*                                                                 *   FILE 688
//*     By following the instructions provided in the program       *   FILE 688
//*     documentation, I created an IMS DBRC List output            *   FILE 688
//*     dataset from the commands indicated, running against V6     *   FILE 688
//*     recons.                                                     *   FILE 688
//*                                                                 *   FILE 688
//*     I then ran the Rexx program against that file.  It          *   FILE 688
//*     generated an output dataset of INIT.xx statments which      *   FILE 688
//*     I have successfully run into a set of V7 RECONS, which      *   FILE 688
//*     Recons we use in production.                                *   FILE 688
//*                                                                 *   FILE 688
//*     The members provided include:                               *   FILE 688
//*     1. $$DOC             this file                              *   FILE 688
//*     2. INITNOIC          sample output of the exec              *   FILE 688
//*     3. DBRCINIT          the rexx program                       *   FILE 688
//*     4. RCNLSTNG          sample input to the exec, produced     *   FILE 688
//*                          with list.xx                           *   FILE 688
//*     5. ME                the 'me' exec                          *   FILE 688
//*     6. REGSTRDB          sample jcl to register the db          *   FILE 688
//*                          using '.INITNOIC'                      *   FILE 688
//*     7. RUNBATCH          sample jcl to run program in batch     *   FILE 688
//*     8. INITTODO          general readme; instructions for       *   FILE 688
//*                          implementation.                        *   FILE 688
//*                                                                 *   FILE 688
//*     Note: Notify.ic statements are not generated, so image      *   FILE 688
//*           copy information will be lost. (This may or may       *   FILE 688
//*           not be dealt with in the future.)                     *   FILE 688
//*                                                                 *   FILE 688
//*     The assembler program ACBLIST is the work of Dougie         *   FILE 688
//*     Lawson of IBM who has been kind enough to allow me to       *   FILE 688
//*     place this program on the CBT tape.                         *   FILE 688
//*                                                                 *   FILE 688
//*     The members provided include:                               *   FILE 688
//*     1. ACBLIST           the assembler program                  *   FILE 688
//*     2. ACBSYSPR          sample sysprint output from the        *   FILE 688
//*                          program                                *   FILE 688
//*                          (Since this output is FB-133 and       *   FILE 688
//*                          is wider than 80 bytes, it is          *   FILE 688
//*                          presented here in TSO XMIT format.     *   FILE 688
//*                          Two members, ACBSYSP$ and ACBSYSP@,    *   FILE 688
//*                          have been supplied, either of which    *   FILE 688
//*                          will convert this member into its      *   FILE 688
//*                          original format. SBG)                  *   FILE 688
//*     3. ACB               rexx exec to get data for 1 member     *   FILE 688
//*                          w/o the JCL                            *   FILE 688
//*     4. ACBLINK           sample JCL to assemble and link        *   FILE 688
//*                          the program                            *   FILE 688
//*     5. ACBLSTRU          sample JCL to run the program          *   FILE 688
//*     6. PUBDOMAI          permission to be in the public         *   FILE 688
//*                          domain                                 *   FILE 688
//*     7. ACBLTODO          what to do for the ACBLIST utility     *   FILE 688
//*                                                                 *   FILE 688
//*     Larry Altman                                                *   FILE 688
//*     larrytheotter@highstream.net                                *   FILE 688
//*                                                                 *   FILE 688

```
