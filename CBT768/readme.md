```
//***FILE 768 is from Rick Bourgeois, and contains an adaptation    *   FILE 768
//*           of the "real tape to AWS tape" and vice-versa         *   FILE 768
//*           facilities, from File 533, to run under CMS.  The     *   FILE 768
//*           following is a description of this package.  The      *   FILE 768
//*           package also includes Sam Golob's utilities to        *   FILE 768
//*           convert real tape to FLEX-ES (R) Faketape, and        *   FILE 768
//*           vice-versa.                                           *   FILE 768
//*                                                                 *   FILE 768
//*           email:  rick@vsoftsys.com                             *   FILE 768
//*                                                                 *   FILE 768
//*     VTT2 AWSTAPE and FAKETAPE                                   *   FILE 768
//*     Real tape conversion utilities                              *   FILE 768
//*                                                                 *   FILE 768
//*     This package updates Sam Golob's REAL tape to AWSTAPE       *   FILE 768
//*     or FAKETAPE and AWSTAPE or FAKETAPE to REAL tape MVS        *   FILE 768
//*     package to run under CMS or MVS.                            *   FILE 768
//*                                                                 *   FILE 768
//*     Updated by Rick Bourgeois - rick@vsoftsys.com This file     *   FILE 768
//*     is included in the VTT2EXEC FILES file as VTT2CMS DOC.      *   FILE 768
//*                                                                 *   FILE 768
//*     For additional information on Sam's package see             *   FILE 768
//*     CBT Tape File 533.                                          *   FILE 768
//*                                                                 *   FILE 768
//*     The changes to Sam's code that allow his programs to        *   FILE 768
//*     run under CMS or MVS were done using conditional assembly   *   FILE 768
//*     code.  A VTTEQUAT copy file was created and contains a      *   FILE 768
//*     &RUNSYS variable that is used to identify the target        *   FILE 768
//*     system.  The &RUNSYS variable can be coded as 'O/S' or      *   FILE 768
//*     'CMS' and the copy file must be in the maclib used for      *   FILE 768
//*     the assemblies.  It specifies 'CMS' in this                 *   FILE 768
//*     distribution so must be changed for MVS assemblies.         *   FILE 768
//*     The VTTEQUAT copy file also contains the register           *   FILE 768
//*     equates, version variable and default chunk size used       *   FILE 768
//*     when creating AWSTAPE or FAKETAPE disk files.               *   FILE 768
//*                                                                 *   FILE 768
//*     There are 8 members in this file.                           *   FILE 768
//*                                                                 *   FILE 768
//*     1. IEBUPDAP EXEC  - Create an append file                   *   FILE 768
//*     2. IEBUPDEX EXEC  - Extract files from an append file       *   FILE 768
//*     3. VTT2EXEC FILES - CMS EXEC files                          *   FILE 768
//*     4. VTT2JCL  FILES - MVS JCL files                           *   FILE 768
//*     5. VTT2SRCE FILES - Assembler source and copy files         *   FILE 768
//*     6. VTT2DOC  FILES - Sam's documentation files               *   FILE 768
//*     7. VTT2TEST FILES - Two test files from Sam's download      *   FILE 768
//*     8. VTT2TEXT FILES - CMS executable TEXT files               *   FILE 768
//*                                                                 *   FILE 768
//*     The IEBUPDAP exec was used to create append files for       *   FILE 768
//*     each of the different file types.  There is a './ ADD       *   FILE 768
//*     NAME=filename cmsattrb' where cmsattrb are the CMS          *   FILE 768
//*     attributes of the file.  Ex;( ./ ADD NAME=IEBUPDAP EXEC     *   FILE 768
//*     F 80 9/27/07 8:17:46)                                       *   FILE 768
//*                                                                 *   FILE 768
//*     The IEBUPDEX exec will extract the individual files         *   FILE 768
//*     from the append files and write them to a CMS disk or       *   FILE 768
//*     directory.  IEBUPDTE can be used to add the files to an     *   FILE 768
//*     MVS PDS.                                                    *   FILE 768
//*                                                                 *   FILE 768
//*     IEBUPDEX command format;                                    *   FILE 768
//*     IEBUPDEX infn FILES infm outfm                              *   FILE 768
//*     If outfm is omitted the files will be written to the        *   FILE 768
//*     file mode identified by infm.                               *   FILE 768
//*                                                                 *   FILE 768
//*     These are the execs and files in the VTT2EXEC FILES file    *   FILE 768
//*                                                                 *   FILE 768
//*     VTT2     CNTRL   - Assembly control file                    *   FILE 768
//*     IEBUPDAP EXEC    - Build an IEBUPDTE format append file     *   FILE 768
//*     IEBUPDEX EXEC    - Extract files from an append file        *   FILE 768
//*     VTT2ASM  EXEC    - Assemble a VTT2 source file              *   FILE 768
//*     VTT2CNVU EXEC    - Convert VB AWSTAPE disk file to FB       *   FILE 768
//*     VTT2DISK EXEC    - Real tape to AWSTAPE disk file           *   FILE 768
//*     VTT2FK2T EXEC    - FAKETAPE disk file to real tape          *   FILE 768
//*     VTT2INST EXEC    - Build VTT2MAC maclib and assemble        *   FILE 768
//*                        all source                               *   FILE 768
//*     VTT2TAPE EXEC    - AWSTAPE disk file to real tape           *   FILE 768
//*     VTT2T2FK EXEC    - Real tape to FAKETAPE disk file          *   FILE 768
//*     VTT2DISK INPUT   - SYSIN for VTT2DISK and VTT2T2FK execs    *   FILE 768
//*     VTT2TAPE INPUT   - SYSIN for VTT2TAPE and VTT2FK2T execs    *   FILE 768
//*     VTT2AWS INSTDISK - Dummy file to identify the install       *   FILE 768
//*                        disk                                     *   FILE 768
//*                                                                 *   FILE 768
//*     The VTT2INST exec will rebuild the VTT2MAC MACLIB and       *   FILE 768
//*     assemble all of the assembler source.  The maclib and       *   FILE 768
//*     text files will be written to the disk that contains        *   FILE 768
//*     the VTTAWS INSTDISK file.  You can optionally specify a     *   FILE 768
//*     file mode when you execute the VTT2INST exec.               *   FILE 768
//*                                                                 *   FILE 768
//*     The VTT2INST exec will erase the VTT2MAC MACLIB and         *   FILE 768
//*     regenerate the maclib with the VTTEQUAT COPY file.  If      *   FILE 768
//*     you want to add additional macros or copy files in the      *   FILE 768
//*     VTT2MAC MACLIB you can add MACLIB ADD statements            *   FILE 768
//*     following the MACLIB GEN in the exec.  The VTT2INST         *   FILE 768
//*     exec executes the VTT2ASM exec for each assemble file       *   FILE 768
//*     on the install disk.  The VTT2ASM EXEC uses the             *   FILE 768
//*     VMFHLASM exec for the assemblies.  If you do not have       *   FILE 768
//*     the high level assembler you will need to change the        *   FILE 768
//*     VTT2ASM exec for the assembler you use.  The VTT2 CNTRL     *   FILE 768
//*     file is used to specify the macro libraries for the         *   FILE 768
//*     VMFHLASM exec.                                              *   FILE 768
//*                                                                 *   FILE 768

```
