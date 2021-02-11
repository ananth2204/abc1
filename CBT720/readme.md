```
//***FILE 720 is from Bill Sweeney and contains a large collection  *   FILE 720
//*           of utilities.  Please see the member called $DIR      *   FILE 720
//*           for an explanation of the contents of each program.   *   FILE 720
//*                                                                 *   FILE 720
//*           email:  whsweeney@sscmainframe.com                    *   FILE 720
//*                                                                 *   FILE 720
//*     $DIR     - This directory member. Contact me if you         *   FILE 720
//*                require further documentation for some of        *   FILE 720
//*                this code: whsweeney@sscmainframe.com            *   FILE 720
//*                                                                 *   FILE 720
//*     ALEXCMDS - APF authorized program that uses SVC 34 to       *   FILE 720
//*                issue commands, STIMER to issue WAITs, WTOs      *   FILE 720
//*                (rollable and highlighted), search Address       *   FILE 720
//*                Space Control Block (ASCB), invoke a REXX        *   FILE 720
//*                EXEC using the IRXJCL program, and perform       *   FILE 720
//*                simple scheduling using the JES2 $TA command     *   FILE 720
//*                                                                 *   FILE 720
//*     ALEXTDAT - Program used by ALEXCMDS to resolve Date and     *   FILE 720
//*                Day information Assemble and link it first,      *   FILE 720
//*                and then include it when linking ALEXCMDS.       *   FILE 720
//*                                                                 *   FILE 720
//*     ALEXT00  - ISPF Message table used by the AutoOps           *   FILE 720
//*                application. Copy member to an ISPMLIB           *   FILE 720
//*                concatenated data set, or LIBDEF to this PDS     *   FILE 720
//*                                                                 *   FILE 720
//*     ALXEXCOM - All purpose REXX utility program that uses       *   FILE 720
//*                the IRXEXCOM feature of REXX to STORE and        *   FILE 720
//*                FETCH variables. Program is invoked by any       *   FILE 720
//*                of the ALEX REXX functions that require          *   FILE 720
//*                access to variables from/to REXX                 *   FILE 720
//*                                                                 *   FILE 720
//*     ALXPEXH1 - ISPF Help Panel used by the AutoOps              *   FILE 720
//*                application. Copy member to an ISPPLIB           *   FILE 720
//*                concatenated data set, or LIBDEF to this PDS     *   FILE 720
//*                                                                 *   FILE 720
//*     ALXPEXH2 - ISPF Help Panel used by the AutoOps              *   FILE 720
//*                application. Copy member to an ISPPLIB           *   FILE 720
//*                concatenated data set, or LIBDEF to this PDS     *   FILE 720
//*                                                                 *   FILE 720
//*     ALXPEXT  - ISPF Panel used by the AutoOps application.      *   FILE 720
//*                Copy member to an ISPPLIB concatenated data      *   FILE 720
//*                set, or LIBDEF to this PDS                       *   FILE 720
//*                                                                 *   FILE 720
//*     ALXRCONC - REXX function to ALLOCATE and CONCATENATE        *   FILE 720
//*                datasets in a TSO session                        *   FILE 720
//*                                                                 *   FILE 720
//*     ALXRDASD - REXX function that performs a UCBSCAN of all     *   FILE 720
//*                DASD or Tape, and returns the information        *   FILE 720
//*                into compound REXX variables                     *   FILE 720
//*                                                                 *   FILE 720
//*     ALXRDDIR - REXX function to return the directory            *   FILE 720
//*                contents of a PDS as compound REXX variables     *   FILE 720
//*                                                                 *   FILE 720
//*     ALXRDOZE - REXX function to SLEEP/WAIT for a period of      *   FILE 720
//*                time                                             *   FILE 720
//*                                                                 *   FILE 720
//*     ALXRFNDM - REXX function to find a member in a PDS          *   FILE 720
//*                                                                 *   FILE 720
//*     ALXREXT  - ISPF REXX EXEC used by the AutoOps               *   FILE 720
//*                application. Copy member to a SYSPROC or         *   FILE 720
//*                SYSEXEC data set                                 *   FILE 720
//*                                                                 *   FILE 720
//*     ALXRFNDS - REXX function to find a load module in the       *   FILE 720
//*                system LPALST or LNKLST concatenation of         *   FILE 720
//*                datasets                                         *   FILE 720
//*                                                                 *   FILE 720
//*     ALXRGETM - REXX function to read a member of a PDS          *   FILE 720
//*                dataset into REXX compound variables             *   FILE 720
//*                                                                 *   FILE 720
//*     ALXRPDSC - REXX function to SCRATCH, RENAME or assign       *   FILE 720
//*                an ALIAS to a member of a PDS. ALIAS does        *   FILE 720
//*                not work with PDS-E files                        *   FILE 720
//*                                                                 *   FILE 720
//*     ALXRQSCN - REXX function that uses GQSCAN to determine      *   FILE 720
//*                if any enqueues exist for data sets, and         *   FILE 720
//*                return the data set, owner and the waiter as     *   FILE 720
//*                compound REXX variables                          *   FILE 720
//*                                                                 *   FILE 720
//*     ALXRWRTM - REXX function to write a member of a PDS         *   FILE 720
//*                dataset from REXX compound variables             *   FILE 720
//*                                                                 *   FILE 720
//*     ALXRWTO  - REXX function to issue a WTO                     *   FILE 720
//*                                                                 *   FILE 720
//*     ALXRWTOR - REXX function to issue a WTOR and return the     *   FILE 720
//*                reply                                            *   FILE 720
//*                                                                 *   FILE 720
//*     ASMLAOPS - JCL to Assemble and Link MSGTABLE to IEAVMXIT    *   FILE 720
//*                                                                 *   FILE 720
//*     ASMLTABL - JCL to Assemble and Link MSGTABLE to             *   FILE 720
//*                IEAVMXIT, and then refresh IEAVMXIT with new     *   FILE 720
//*                messages                                         *   FILE 720
//*                                                                 *   FILE 720
//*     ASMLVMXT - JCL to Assemble and Link changes to IEAVMXIT     *   FILE 720
//*                                                                 *   FILE 720
//*     CATCLEAN - Old Assembler program that is provided as an     *   FILE 720
//*                example. It was written in MVS/SP, and it        *   FILE 720
//*                does the following: EXCP read of the VTOC,       *   FILE 720
//*                use of SVC 26 for Catalog function, read an      *   FILE 720
//*                ICF Catalog as a VSAM KSDS, and use SVC 99       *   FILE 720
//*                dynamic allocation                               *   FILE 720
//*                                                                 *   FILE 720
//*     CBR3750I - REXX EXEC sample that is placed in the           *   FILE 720
//*                SYSEXEC file defined in the OPSAUTO Started      *   FILE 720
//*                Task JCL. Entry must be defined in the           *   FILE 720
//*                MSGTABLE AutoOps member to be used by the        *   FILE 720
//*                IEAVMXIT exit                                    *   FILE 720
//*                                                                 *   FILE 720
//*     CLEANPDS - Assembler program to compare two PDS files,      *   FILE 720
//*                and delete members that are duplicate. Good      *   FILE 720
//*                for cleaning up old Linklist libraries, when     *   FILE 720
//*                vendor put all products in one library           *   FILE 720
//*                                                                 *   FILE 720
//*     COPYISPF - REXX EXEC that uses supplied Assembler REXX      *   FILE 720
//*                functions to copy PDS members and change the     *   FILE 720
//*                ISPF statistics. It is what was used to          *   FILE 720
//*                create this PDS with the squirrely CREATED       *   FILE 720
//*                and CHANGED dates (day I was born, and end       *   FILE 720
//*                of day if and when I turn 75)                    *   FILE 720
//*                                                                 *   FILE 720
//*     COUTCPCM - Assembler program to issue VM CP commands        *   FILE 720
//*                (DIAGNOSE command) Good when running as a        *   FILE 720
//*                guest under VM, and you want to issue CP         *   FILE 720
//*                commands                                         *   FILE 720
//*                                                                 *   FILE 720
//*     COUTLOGC - Assembler program to create the next file on     *   FILE 720
//*                a multi-file tape. As an example, used when      *   FILE 720
//*                wanting to stack monthly SMF data on the         *   FILE 720
//*                same tape.                                       *   FILE 720
//*                                                                 *   FILE 720
//*     DASDBOX  - REXX EXEC that used the ALXRDASD REXX            *   FILE 720
//*                function to provide output of all defined        *   FILE 720
//*                DASD volumes in a BOX format. Uses a call to     *   FILE 720
//*                IDCAMS, and the DCOLLECT command to get the      *   FILE 720
//*                free space information. You must add IDCAMS      *   FILE 720
//*                to the IKJTSOxx member in PARMLIB, under         *   FILE 720
//*                AUTHPGM, in order to issue the CALL.             *   FILE 720
//*                                                                 *   FILE 720
//*     EZACICSE - Assembler CICS security exit for the TCP/IP      *   FILE 720
//*                Listener. I included it because I remember       *   FILE 720
//*                trying to find a sample when I had to write      *   FILE 720
//*                it                                               *   FILE 720
//*                                                                 *   FILE 720
//*     E0016    - REXX EXEC sample that is placed in the           *   FILE 720
//*                SYSEXEC file defined in the OPSAUTO Started      *   FILE 720
//*                Task JCL. This EXEC was used to track OAM        *   FILE 720
//*                messages issued by the VTS, and if a problem     *   FILE 720
//*                is identified, then the Operator's are told      *   FILE 720
//*                to use the 'Phone Home' feature of the VTS.      *   FILE 720
//*                EXEC is invoked because of the CBR3750I          *   FILE 720
//*                message, and is invoked from the CBR3750I        *   FILE 720
//*                EXEC                                             *   FILE 720
//*                                                                 *   FILE 720
//*     E0017    - REXX EXEC sample that is placed in the           *   FILE 720
//*                SYSEXEC file defined in the OPSAUTO Started      *   FILE 720
//*                Task JCL. This EXEC was used to track OAM        *   FILE 720
//*                messages issued by the VTS. EXEC is invoked      *   FILE 720
//*                because of CBR3750I message, and is invoked      *   FILE 720
//*                from the CBR3750I EXEC                           *   FILE 720
//*                                                                 *   FILE 720
//*     IEAVMXIT - WTO/WTOR exit that will process all MVS          *   FILE 720
//*                messages that are defined for automation in      *   FILE 720
//*                the MSGTABLE entry                               *   FILE 720
//*                                                                 *   FILE 720
//*     INRECXIT - Assembler Network Print Facility (NPF) input     *   FILE 720
//*                record exit for inserting HP PCL in the print    *   FILE 720
//*                stream. NPF was free from IBM, so if you are     *   FILE 720
//*                using it, the exit might help                    *   FILE 720
//*                                                                 *   FILE 720
//*     LCB      - REXX EXEC that can be executed from ISPF 3.4     *   FILE 720
//*                data set list, to issue an IDCAMS LISTCAT        *   FILE 720
//*                and return the information in an ISPF Browse     *   FILE 720
//*                session. EXEC includes the code to display       *   FILE 720
//*                the last modified TIMESTAMP as something you     *   FILE 720
//*                can read                                         *   FILE 720
//*                                                                 *   FILE 720
//*     MESSAGE  - Assembler MACRO used to build MSGTABLE used      *   FILE 720
//*                by IEAVMXIT.  Macro is located in                *   FILE 720
//*                SYS2.ISPF.LOCAL.MACLIB                           *   FILE 720
//*                                                                 *   FILE 720
//*     MSGTABLE - Assembler table created by the ISPF/REXX         *   FILE 720
//*                AutoOps interface, and contains all of the       *   FILE 720
//*                messages to be processed by IEAVMXIT             *   FILE 720
//*                                                                 *   FILE 720
//*     MSGTABLE - Assembler Table used by AutoOps application.     *   FILE 720
//*                It is built using the supplied ISPF/REXX         *   FILE 720
//*                panels and EXECs included in this PDS. It        *   FILE 720
//*                currently contains sample entries that           *   FILE 720
//*                should be removed when you are ready to use      *   FILE 720
//*                it.                                              *   FILE 720
//*                                                                 *   FILE 720
//*     OPSAUTO  - JCL PROC used by the AutoOps application and     *   FILE 720
//*                invoked as an MVS START command from the         *   FILE 720
//*                IEAVMXIT                                         *   FILE 720
//*                                                                 *   FILE 720
//*     PDSPCLOD - PC REXX EXEC to take the output from PDSUNLDV    *   FILE 720
//*                program and place the members in a directory     *   FILE 720
//*                on your PC                                       *   FILE 720
//*                                                                 *   FILE 720
//*     PDSRELDV - Assembler program to rebuild a PDS from the      *   FILE 720
//*                PDSUNLDV program.                                *   FILE 720
//*                                                                 *   FILE 720
//*     PDSUNLDV - Assembler program to create a sequential         *   FILE 720
//*                file from an FB or VB PDS, for unloading         *   FILE 720
//*                from the mainframe. Use PDSPCLOD REXX EXEC       *   FILE 720
//*                on your Personal Computer to unload the          *   FILE 720
//*                members into a directory (you can download       *   FILE 720
//*                REGINA if you want to run REXX on your PC).      *   FILE 720
//*                Does not retain the ISPF STATs info.             *   FILE 720
//*                                                                 *   FILE 720
//*     SSCLKPDS - Assembler program that allows the SSCUCPDS       *   FILE 720
//*                program to issue Multiple change commands.       *   FILE 720
//*                The name of the SSCUCPDS program is              *   FILE 720
//*                contained in this program, so if you change      *   FILE 720
//*                it, you must change it in this program as        *   FILE 720
//*                well.                                            *   FILE 720
//*                                                                 *   FILE 720
//*     SSCUCPDS - Assembler program written in 1984 to perform     *   FILE 720
//*                mass edits of multiple PDS or sequential         *   FILE 720
//*                files. Originally used as a migration tool       *   FILE 720
//*                for doing massive changes to libraries with      *   FILE 720
//*                JCL. Program only works on RECFM FB, LRECL 80    *   FILE 720
//*                files, because it maintains the integrity of     *   FILE 720
//*                column 72 within the code.  The default is to    *   FILE 720
//*                show you what the changes would look like        *   FILE 720
//*                before actually changing the files. Once         *   FILE 720
//*                satisfied, specify PARM=CHGE to perform the      *   FILE 720
//*                change. Program also has a parameter function    *   FILE 720
//*                to SCAN PDS files, without doing any changes.    *   FILE 720
//*                SSCLKPDS program was written later, so that      *   FILE 720
//*                multiple change input control cards could be     *   FILE 720
//*                supplied.                                        *   FILE 720
//*                                                                 *   FILE 720
//*     SYSURDR  - Assembler program that will allow you to         *   FILE 720
//*                build and submit a job from the Operator         *   FILE 720
//*                Console. Program issues WTORs, and when          *   FILE 720
//*                complete, submits the job for execution. I       *   FILE 720
//*                saw this done on DOS/VSE and thought it was      *   FILE 720
//*                a good idea if the network was done. REXX        *   FILE 720
//*                using the ALXRWTOR assembler function would      *   FILE 720
//*                be easier to maintain, but I figured I'd         *   FILE 720
//*                include this program.                            *   FILE 720
//*                                                                 *   FILE 720
//*     SUBTTIME - REXX EXEC that will take two date/time           *   FILE 720
//*                fields as input arguments, and calculate the     *   FILE 720
//*                time difference. Found it useful in AutoOps      *   FILE 720
//*                when making a decision on the frequency of       *   FILE 720
//*                an occurrence                                    *   FILE 720
//*                                                                 *   FILE 720
//*     TAPESTCK - Assembler program that was originally written    *   FILE 720
//*                to convert from 3480 tape to 3590 tape.          *   FILE 720
//*                Program will stack the input files on to the     *   FILE 720
//*                output tape, and build the necessary IDCAMS      *   FILE 720
//*                DELETE/DEFINE control cards to recatalog the     *   FILE 720
//*                input files to the new media.  Also builds       *   FILE 720
//*                CA1 SCRATCH control cards, if you need them.     *   FILE 720
//*                Will support 64k blocks.                         *   FILE 720
//*                                                                 *   FILE 720
//*     VARYOFF  - REXX EXEC that uses ALXRDASD REXX function       *   FILE 720
//*                and input control cards to vary selected         *   FILE 720
//*                DASD offline at IPL time. Allows you to          *   FILE 720
//*                specify selection criteria                       *   FILE 720
//*                                                                 *   FILE 720
//*     VARYOFFJ - Started Task JCL for invoking VARYOFF EXEC       *   FILE 720
//*                                                                 *   FILE 720
//*     VARYOFFP - Control card input to VARYOFF EXEC               *   FILE 720
//*                                                                 *   FILE 720

```
