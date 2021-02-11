
## @FILE887.txt
```
//***FILE 887 is from Scott Vetter and contains a large collection  *   FILE 887
//*           of programs and usermods for MVS 3.8J to make it more *   FILE 887
//*           modern and workable.                                  *   FILE 887
//*                                                                 *   FILE 887
//*       email:  svetter@ameritech.net                             *   FILE 887
//*                                                                 *   FILE 887
//*                 INDEX TO PROGRAMS / USERMODS                    *   FILE 887
//*                                                                 *   FILE 887
//*     LAST CHANGE:  04/26/2012                                    *   FILE 887
//*                                                                 *   FILE 887
//*              -------------   PROGRAMS   -------------           *   FILE 887
//*      NAME   STATUS   MODULE(S)             PURPOSE              *   FILE 887
//*     CMDSHR    O      CMDSHR            A PROGRAM THAT ALLOWS    *   FILE 887
//*                                        A USER ON ONE SYSTEM     *   FILE 887
//*                                        TO ENTER A COMMAND       *   FILE 887
//*                                        AND HAVE IT RUN ON       *   FILE 887
//*                                        ANOTHER.                 *   FILE 887
//*     CMDSHRA   O      CMDSHRA           FOR ABOVE - PARMLIB      *   FILE 887
//*                                        ENTRY                    *   FILE 887
//*     CMDSHRR   O      CMDSHRR           FOR ABOVE - PROCLIB      *   FILE 887
//*                                        ENTRY                    *   FILE 887
//*     DAPF      O      DAPF              USED TO DISPLAY THE      *   FILE 887
//*                                        APF DATASET LIST ON      *   FILE 887
//*                                        THE TSO USER'S           *   FILE 887
//*                                        SCREEN.                  *   FILE 887
//*     DAPFC     O      DAPFC             USED TO DISPLAY THE      *   FILE 887
//*                                        APF DATASET LIST ON      *   FILE 887
//*                                        THE OPERATOR'S           *   FILE 887
//*                                        CONSOLE.                 *   FILE 887
//*                                                                 *   FILE 887
//*              -------------   USERMODS   -------------           *   FILE 887
//*      NAME   STATUS   MODULE(S)             PURPOSE              *   FILE 887
//*     TSM0002   O      IEFUTL (SRC)      MVS SMF TIME LIMIT       *   FILE 887
//*                                        EXIT                     *   FILE 887
//*     TSM0020   O      NETSOL (SRC)      VTAM LOGO SCREEN         *   FILE 887
//*     TSM0021   O      ISTNSC00 (SRC)    VTAM ASSEMBLE THE        *   FILE 887
//*                                        LOGO                     *   FILE 887
//*     TSM0022   T      IKJEFLD (SRC)     TSO FULL SCREEN LOGON    *   FILE 887
//*     TSM0025   O      IEECDCM (MAC)     MVS CONSOLE (K S)        *   FILE 887
//*                                        CHANGES                  *   FILE 887
//*     TSM0026   T      IEECVETC (ZAP)    MVS CONSOLE (K S)        *   FILE 887
//*                                        CHANGES                  *   FILE 887
//*     TSM0027   O      IEERDCM / IEETDCM (MAC)  MVS DCM MACROS    *   FILE 887
//*     TSM0028   O      IEECVETQ (SRC)    MVS CONSOLE ADDS         *   FILE 887
//*                                        ADDRESS AND ID TO        *   FILE 887
//*                                        IEE152I MESSAGE LINE     *   FILE 887
//*     TSM0029   T      IEECVETC (SRC)                             *   FILE 887
//*     TSM0034   T      IHASVC   (MAC)    INSTALLS MACRO IHASVC    *   FILE 887
//*     TSM0035   D      IEFJJOBS (SRC)    IN DEVELOPMENT - USED    *   FILE 887
//*                                        TO READ THE MASTER       *   FILE 887
//*                                        JCL FROM PARMLIB.        *   FILE 887
//*     TSM0036   D      IRBMFINP (ZAP)    CHANGES THE DDNAME       *   FILE 887
//*                                        FOR MF/1 PARM INPUT.     *   FILE 887
//*     TSV0000   O               (MACS)   CREATE A SYS1.MODGEN     *   FILE 887
//*                                        DATASET NOT AN SMP       *   FILE 887
//*                                        JOB (YET).               *   FILE 887
//*     TSV0001   O      RESETPL           COPY MACRO TO MACLIB     *   FILE 887
//*     TSV0002   O      IKJEFTE2          TSO AUTHORIZED COMMAND   *   FILE 887
//*                                        TABLE                    *   FILE 887
//*     TSV0003   O      IKJEFTE8          TSO AUTHORIZED COMMAND   *   FILE 887
//*                                        TABLE                    *   FILE 887
//*     TSV0004   O      IEEVSND6          REMOVE CN(00) FROM       *   FILE 887
//*                                        MESSAGES                 *   FILE 887
//*     TSV0005   T      IKJEFF10          TSO SUBMIT EXIT          *   FILE 887
//*     TSV0006   O      IKJEFT25          TSO CHANGE TIME          *   FILE 887
//*                                        COMMAND TO SHOW THE      *   FILE 887
//*                                        PROPER CENTURY/YEAR      *   FILE 887
//*     TSV0007   O      MSTRJCL           MVS MASTER JCL           *   FILE 887
//*     TSV0008   T      HEWLFINT          LINKAGE EDITOR           *   FILE 887
//*     TSV0009   O      IEFACTRT (SRC)    MVS JCL STEP/JOB END     *   FILE 887
//*                                        EXIT                     *   FILE 887
//*     TSV0010   O      IEE3503D (SRC)    MVS CONSOLE ADD PROPER   *   FILE 887
//*                                        CENTURY/YEAR ON DATE     *   FILE 887
//*                                        (D T) COMMAND ALSO (D    *   FILE 887
//*                                        IPLINFO), (D XCF), (D    *   FILE 887
//*                                        SMF), AND (D SYMBOLS)    *   FILE 887
//*     TSV0011   T      HEWLFFNL          LINKAGE EDITOR           *   FILE 887
//*     TSV0012   O      ISTSDCRC          VTAM REMOVE REQUIREMENT  *   FILE 887
//*                                        FOR VTAMOBJ              *   FILE 887
//*                                        DDNAME/DATASET NAME      *   FILE 887
//*     TSV0013   O      IEFJSSNT          MVS SUBSYSTEM NAME       *   FILE 887
//*                                        TABLE UPDATE             *   FILE 887
//*     TSV0014   O      SGIEF0PT (MAC)    MVS PROGRAM PROPERTIES   *   FILE 887
//*                                        TABLE (PPT)              *   FILE 887
//*     TSV0015   O      IEEPFKEY          MVS CONSOLE SET PF KEYS  *   FILE 887
//*     TSV0016   O      ISTINCLM          VTAM LOGON INTERPRET     *   FILE 887
//*                                        TABLE                    *   FILE 887
//*     TSV0017   O      BSPLMT01          VTAM LOGMODE TABLES      *   FILE 887
//*     TSV0018   O      CLS (SRC)         TSO CLEAR SCREEN COMMAND *   FILE 887
//*     TSV0019   T      IKJEFF53          TSO OUTPUT EXIT          *   FILE 887
//*     TSV0020   O      IEECVXIT (SRC)    MVS CONSOLE MESSAGE      *   FILE 887
//*                                        PROCESSING EXIT          *   FILE 887
//*     TSV0021   O      IEE0403D (SRC)    MVS COMMAND ROUTER -     *   FILE 887
//*                                        ALLOW COMMAND QUIESCE    *   FILE 887
//*                                        TO BE SPECIFIED AS       *   FILE 887
//*                                        "QU"                     *   FILE 887
//*     TSV0022   O      IKJEFLPA (SRC)    TSO LOGON/LOGOFF         *   FILE 887
//*                                        PROCESSOR - CHANGE       *   FILE 887
//*                                        CENTURY FROM '19' TO     *   FILE 887
//*                                        '20'.                    *   FILE 887
//*     TSV0023   O      IKTCAS41 (ZAP)    REMOVES THE MESSAGE      *   FILE 887
//*                                        IKT012D AFTER ISSUES     *   FILE 887
//*                                        THE P TSO COMMAND.       *   FILE 887
//*     TSV0024   O      IEESMCA  (MAC)    SMF CONTROL TABLE AND    *   FILE 887
//*                      IEEMB820 (SRC)    SMF INITIALIZATION       *   FILE 887
//*                                        ROUTER TO ALLOW FOR      *   FILE 887
//*                                        IPL DATE AND TIME.       *   FILE 887
//*                      IEEMB821 (SRC)    SMF INITIALIZATION       *   FILE 887
//*                                        PARM PROCESSOR ALLOWS    *   FILE 887
//*                                        COMMENT LINES IN         *   FILE 887
//*                                        SMFPRMXX!                *   FILE 887
//*     TSV0025   T      IEAVNP03 (SRC)    ADDS PARAMETERS TO       *   FILE 887
//*                                        IEASYS-- OF              *   FILE 887
//*                                        SYS1.PARMLIB -           *   FILE 887
//*                                        DOESN'T DO ANYTHING      *   FILE 887
//*                                        MORE THOUGH.             *   FILE 887
//*     TSV0026   0      DAPF     (SRC)    ADDS A TSO USER          *   FILE 887
//*                                        COMMAND DAPF WHICH       *   FILE 887
//*                                        SHOWS WHAT IS IN THE     *   FILE 887
//*                                        APF LIST.                *   FILE 887
//*     TSV0031   O      $FSSBA   (MAC)    INSTALLS THE FULL        *   FILE 887
//*                                        SCREEN MACRO             *   FILE 887
//*     TSM0032   O      IEDIAE/K (SRC)    VTAM - INSTALLS          *   FILE 887
//*                                        UNUSED EXITS -           *   FILE 887
//*                                        PREVENTS VTAM            *   FILE 887
//*                                        MESSAGES.                *   FILE 887
//*     TSM003T   T      IECSDSL1 (MAC)    FORMAT 1 DSCB            *   FILE 887
//*                                        DESCRIPTION - TO         *   FILE 887
//*                                        SUPPORT HOLDING          *   FILE 887
//*                                        CENTURY ON DATES.        *   FILE 887
//*                                                                 *   FILE 887
//*     RAKF0001  O      IFG0194A/IFG0194C  RAKF OPEN ALWAYS        *   FILE 887
//*                                         CALL SVC UPDATE.        *   FILE 887
//*     RAKF0002  O      RAKFPROF/RAKFUSER  RAKF OPERATING TABLES.  *   FILE 887
//*     RAKF0003  O      IGC0013A/B/        RAKF SVC INSTALL.       *   FILE 887
//*     RAKF0004  O      RAKFINIT/USER/PROF RAKF PROGRAM INSTALL.   *   FILE 887
//*     RAKF0005  O      RAKF               RAKF JCL PROC INSTALL.  *   FILE 887
//*                                                                 *   FILE 887
//*      ----  OUTSIDE DEVELOPED MODS                               *   FILE 887
//*                                                                 *   FILE 887
//*     SLB0002   T      IEFVEA             ALLOWS FOR MB           *   FILE 887
//*                      IEFVJA             SPECIFICATION IN THE    *   FILE 887
//*                                         REGION PARAMETER        *   FILE 887
//*                                         ON BOTH THE JOB         *   FILE 887
//*                                         AND EXEC JCL CARDS.     *   FILE 887
//*     ZP60004   O      IEECVETV           MCS CONSOLE CHANGE TO   *   FILE 887
//*                                         HIGHLITE ACTION         *   FILE 887
//*                                         MESSAGES                *   FILE 887
//*     ZP60014   T      IKJCT431, IKJCT433 ADDS EXTENSIONS         *   FILE 887
//*                      IKJEFT56           TO TSO CLIST            *   FILE 887
//*                                         CAPABILITIES            *   FILE 887
//*     ZP60019   T      IEFSD263           ALLOWS RECORDING OF     *   FILE 887
//*                                         CPU TIME FOR JOBS       *   FILE 887
//*                                         RUNNING WITH            *   FILE 887
//*                                         TIME=1440               *   FILE 887
//*     ZP60021   T      IEAVAD51           CHANGES DUMP OUTPUT     *   FILE 887
//*                                         SHOWING CHARS THAT      *   FILE 887
//*                                         ARE SHOWN ON US         *   FILE 887
//*                                         KEYBOARD.               *   FILE 887
//*                                                                 *   FILE 887
//*       NOTE:                                                     *   FILE 887
//*             MEMBERS ENDING IN A 'B' ARE BACKUPS FOR             *   FILE 887
//*                PREVIOUSLY MODIFIED USERMODS.                    *   FILE 887
//*             MEMBERS ENDING IN A 'I' ARE TEST JOBS, AKA IVPS,    *   FILE 887
//*                FOR THE USERMOD.                                 *   FILE 887
//*                                                                 *   FILE 887
//*       STATUS LEGEND:                                            *   FILE 887
//*         T - TESTING - MAY NOT BE OPERATIONAL                    *   FILE 887
//*         O - OPERATIONAL - IN USE                                *   FILE 887
//*                                                                 *   FILE 887
```

