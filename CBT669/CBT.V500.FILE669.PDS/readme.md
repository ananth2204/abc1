
## @FILE669.txt
```
//***FILE 669  REXX Global Variables, VSAM bulk access, OpComm etc  *   FILE 669
//*                                                                 *   FILE 669
//*            Contact email: willy@harders-jensen.com              *   FILE 669
//*            Web:           http://harders-jensen.com/wjtech      *   FILE 669
//*                                                                 *   FILE 669
//*            Programs in package:                                 *   FILE 669
//*                                                                 *   FILE 669
//*             ISPDPX01 - ISPF panel exit, supply panel lines in   *   FILE 669
//*                        REXX stem(s)                             *   FILE 669
//*                        Build: 003 2019-12-04                    *   FILE 669
//*             REXXGBLV - REXX function to implement global        *   FILE 669
//*                        variables.                               *   FILE 669
//*                        Build: 064 2020-07-22                    *   FILE 669
//*             REXXSTOR - REXX function to save and retrieve a     *   FILE 669
//*                        string in command storage.               *   FILE 669
//*                        Build: 005 2019-12-04                    *   FILE 669
//*             RXPATTRN - REXX function to test a string against   *   FILE 669
//*                        a pattern.                               *   FILE 669
//*                        Build: 003 2020-07-21                    *   FILE 669
//*             RXRDPRML - REXX function to copy a parmlib          *   FILE 669
//*                        member to a stem.                        *   FILE 669
//*                        Build: 005 2019-12-04                    *   FILE 669
//*             RXOPCOMM - REXX function allowing a REXX program    *   FILE 669
//*                        to support operator MODIFY and STOP      *   FILE 669
//*                        commands.                                *   FILE 669
//*                        Build: 006 2019-12-04                    *   FILE 669
//*             RXVSAMBA - REXX function to read and update a       *   FILE 669
//*                        VSAM KSDS and RRDS database through      *   FILE 669
//*                        stem or stack.                           *   FILE 669
//*                        Build: 026 2020-07-22                    *   FILE 669
//*             RXWAIT   - REXX function to wait whole or           *   FILE 669
//*                        fractions of seconds.                    *   FILE 669
//*                        May also be used as a TSO command and    *   FILE 669
//*                        a batch pgm                              *   FILE 669
//*                        Build: 002 2019-12-04                    *   FILE 669
//*                                                                 *   FILE 669
//*            This update is mostly because a fix to a bug in the  *   FILE 669
//*            STRPATRN macro, which is used in several of the      *   FILE 669
//*            programs.                                            *   FILE 669
//*                                                                 *   FILE 669
//*            Install a program                                    *   FILE 669
//*                                                                 *   FILE 669
//*             RECEIVE the transport dataset, this will generate   *   FILE 669
//*             a pds with all neccessary members.                  *   FILE 669
//*             Edit and excute the $$$$EDIT member to update       *   FILE 669
//*             library names throughout the CBT library.           *   FILE 669
//*             Review and run the program member. This will        *   FILE 669
//*             install and verify the program.                     *   FILE 669
//*             You may edit and execute member Z669UPDT to update  *   FILE 669
//*             library names etc in the install lib.               *   FILE 669
//*                                                                 *   FILE 669
//*            ISPDPX01 description                                 *   FILE 669
//*                                                                 *   FILE 669
//*             This  ISPF panel  exit is  used to  insert records  *   FILE 669
//*             into  an ISPF  panel.  It can  replace the  entire  *   FILE 669
//*             panel, or one  or more sections with  data in REXX  *   FILE 669
//*             stem variable(s).                                   *   FILE 669
//*             Build: 003                                          *   FILE 669
//*             See member ISX1DOC for full  documentation.         *   FILE 669
//*             Members ISX1* are part of the ISPDPX01 package.     *   FILE 669
//*                                                                 *   FILE 669
//*            REXXGBLV description                                 *   FILE 669
//*                                                                 *   FILE 669
//*             Provides   a  variable   store  external   to  the  *   FILE 669
//*             currently running REXX program. REXX variables can  *   FILE 669
//*             be  copied to  the  external  store and  retrieved  *   FILE 669
//*             again at  some later time  by the same  or another  *   FILE 669
//*             REXX  process. The  saved  variables  can even  be  *   FILE 669
//*             written to and retrieved from  a disk file, so can  *   FILE 669
//*             be  used across  logons and  even be  shared among  *   FILE 669
//*             users.                                              *   FILE 669
//*             Plus numerous REXX variable handling functions.     *   FILE 669
//*             Build: 062                                          *   FILE 669
//*             See member RXGVDOC for full  documentation.         *   FILE 669
//*             See member RXGVRDME for a member list.              *   FILE 669
//*             Members RXGV* are part of the REXXGBLV package.     *   FILE 669
//*                                                                 *   FILE 669
//*            REXXSTOR description                                 *   FILE 669
//*                                                                 *   FILE 669
//*             Allow a REXX program to  store a string of data in  *   FILE 669
//*             common storage and retrieve  it later, either from  *   FILE 669
//*             the  same program  or from  another REXX  program.  *   FILE 669
//*             Build: 005                                          *   FILE 669
//*             See member RXSTDOC for full  documentation.         *   FILE 669
//*             Members RXST* are part of the REXXSTOR package.     *   FILE 669
//*                                                                 *   FILE 669
//*            RXPATTRN description                                 *   FILE 669
//*                                                                 *   FILE 669
//*             Test a string by a mask, return 0 if match.         *   FILE 669
//*             See member RXPNDOC for full  documentation.         *   FILE 669
//*             Build: 002                                          *   FILE 669
//*             Members RXPN* are part of the RXPATTRN package.     *   FILE 669
//*                                                                 *   FILE 669
//*            RXRDPRML description                                 *   FILE 669
//*                                                                 *   FILE 669
//*             Read parmlib member, return data in stem.           *   FILE 669
//*             Some comments may be ignored.                       *   FILE 669
//*             Build: 005                                          *   FILE 669
//*             See member RXRPDOC for full  documentation.         *   FILE 669
//*             Members RXRP* are part of the RXRDPRML package.     *   FILE 669
//*                                                                 *   FILE 669
//*            RXOPCOMM description                                 *   FILE 669
//*                                                                 *   FILE 669
//*             Allow MODIFY and STOP operator command for REXX     *   FILE 669
//*             programs (F jobname,some text, or P jobname).       *   FILE 669
//*             Build: 006                                          *   FILE 669
//*             See member RXOPDOC for full  documentation.         *   FILE 669
//*             Members RXOP* are part of the RXOPCOMM package.     *   FILE 669
//*                                                                 *   FILE 669
//*            RXVSAMBA description                                 *   FILE 669
//*                                                                 *   FILE 669
//*             The program  can add, replace, retrieve  or delete  *   FILE 669
//*             records from a VSAM database. Acess is normally by  *   FILE 669
//*             key/keyprefix,  but  some functions  allow  access  *   FILE 669
//*             based on text anywhere in the record.               *   FILE 669
//*             Data is either read from  a REXX stem or stored in  *   FILE 669
//*             a REXX stem.                                        *   FILE 669
//*             Build: 025                                          *   FILE 669
//*             See member RXVBDOC for full  documentation.         *   FILE 669
//*             Members RXVB* are part of the RXVSAMBA package.     *   FILE 669
//*                                                                 *   FILE 669
//*            RXWAIT description                                   *   FILE 669
//*                                                                 *   FILE 669
//*              cc=RXWAIT(time-spec)                 REXX function *   FILE 669
//*               or                                                *   FILE 669
//*              RXWAIT timespec                      TSO cmd       *   FILE 669
//*               or                                                *   FILE 669
//*              // EXEC PGM=RXWAIT,PARM=timespec     batch step    *   FILE 669
//*                time-spec:                                       *   FILE 669
//*                  n          seconds                             *   FILE 669
//*                  .nn        fractions of seconds                *   FILE 669
//*                  =hhmmssth                                      *   FILE 669
//*             Members RXWT* are part of the RXWAIT package.       *   FILE 669
//*             Build: 002                                          *   FILE 669
//*                                                                 *   FILE 669
//*            Changes in this package:                             *   FILE 669
//*                                                                 *   FILE 669
//*             REXXGBLV  Fix DATA(ccc) issue                       *   FILE 669
//*                                                                 *   FILE 669
//*             RXPATTRN  Change ASAXWC call to own StrPatrn        *   FILE 669
//*                                                                 *   FILE 669
//*             RXVSAMBA  Fix MASK(ccc) issue                       *   FILE 669
//*                                                                 *   FILE 669
//*             RXWAIT    Add '.' and '=' parm formats              *   FILE 669
//*                       Add CDEUCTZ2 macro to keep lmod in        *   FILE 669
//*                       storage.                                  *   FILE 669
//*                                                                 *   FILE 669
//*             See the xxxxHIST members for details.               *   FILE 669
//*                                                                 *   FILE 669
//*            Other members of possible interest                   *   FILE 669
//*                                                                 *   FILE 669
//*              ISPXMACS  ASM copy book containing my macros for   *   FILE 669
//*                        interfacing with ISPF.                   *   FILE 669
//*              REXXMACS  ASM copy book containing my macros for   *   FILE 669
//*                        interfacing with REXX.                   *   FILE 669
//*              WSAMMACS  ASM copy book containing my structured   *   FILE 669
//*                        assembler macro set. WSAM is similar,    *   FILE 669
//*                        but not identical, to IBM's Structured   *   FILE 669
//*                        Programming Macros.                      *   FILE 669
//*                                                                 *   FILE 669
//*            Some notes                                           *   FILE 669
//*              Common macros devloped by me are combined in       *   FILE 669
//*              member DVLMACS. This member is included by the     *   FILE 669
//*              various products.                                  *   FILE 669
//*              Use member Z669UPDT to update JCL - if you have    *   FILE 669
//*              STARTOOL or PDS86 installed.                       *   FILE 669
//*                                                                 *   FILE 669
```

