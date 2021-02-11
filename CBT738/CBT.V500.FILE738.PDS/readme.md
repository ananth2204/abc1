
## $$DOC.txt
```
 Last Update: 06/02/2009    Terry Miller
                            ConocoPhillips
                            tkmille@ConocoPhillips.com

 Modification Level: V01.02.02

 Corrected Help screen REORGVSH operands.
 Modified Rexx Exec REORGVSX to eliminate some redundant code.
 Modified Abender source to remove jcl (allow it to assemble)
   (Thanks to Michael Mayne)

 Modification Level: V01.02.01

 Added a second invocation Rexx Exec called REORGVSX to
 perform the I/O and work.  Exec REORGVS became a front-end
 exec to invoke an ISPF environment if the user invokes
 REORGVS in the foreground.  REORGVS continues to work
 as it did before if it is invoked in the background with
 the exception that there are now two invocation execs
 (REORGVS which calls REORGVSX to do the work).

 Modified Rexx exec REORGVS
   (requires site tailoring for SYSPROC lib)
 Added one new Rexx exec REORGVSX
   (requires site tailoring for ISPPLIB and ISPMLIB libs)
 Added three new ISPF panels:  REORGPN1, REORGPN2, REOHGPN1
 Added one   new ISPF message member: REOM00
 Modified the SYSHELP panel for REORGVS

 Modification Level: V01.01.08

 Updated REXX execs to add the following two
 user tailoring comment:
 1) Change the length of "sysid" to your specification.
     The default is 3 characters if this is not
     modified.

 Updated REXX exec "REORGVS5" to add the following additional
 tailoring comment:
 2) Change the HLQ of the log dataset to your
     specification.  The default is HLQ is "SYS3".

 Modification Level: V01.01.07

 Added a REXX exec call BADVSAM which identifies VSAM components
 which are defined with the "IMBED", "REPLICATE", and "KEYRANGE"
 parameters.  Calls program 'IGGCSI00' to look through each ICF
 catalog import connected to the master catalog.

 Modification Level: V01.01.06

 REORGVS is a REXX facility which allows a user to reorganize VSAM
 clusters without having to know the specifics of the allocation
 parameters and components associated with the cluster.

 It was written to reallocate and reorg VSAM clusters which were
 defined with the "IMBED" and "REPLICAT" parameters which are no
 longer supported by Z/OS 1.5 and higher.  It was written with the
 express purpose of converting these VSAM clusters, but it is also
 very useful in reorganizing clusters.  The user does not need to
 know the file attributes of the cluster or of the associates
 components in order to reorg a cluster.

 The facility executes REXX execs and IDCAMS in a background job.
 The REXX facility issues IDCAMS commands to parse out the
 DEFINE parameters and creates IDCAMS commands to reallocate the
 VSAM components.

 The reorg facility issues IDCAMS EXPORT and IMPORT FUNCTIONS
 BACKUP/RELOAD the cluster data.

 Multiple clusters can be reorged at the same time.  The REXX
 facility uses a random number suffix for the JOBNAME of each
 reorg job that it submits through the internal reader.

 The facility handles clusters having alternate indexes and paths.

 The facility assumes that RACF is installed as the security product.
 If RACF IS NOT INSTALLED ON YOUR SITE, YOU WILL HAVE TO MODIFY REXX
 EXEC "REORGVS4" TO ISSUE THE EQUIVALENT STATEMENTS FOR YOUR SECURITY
 PRODUCT AND CHANGES SOME OF THE "REORGVSS" SKELETON).  Alternately,
 you may choose to handle security profiles seperately after the fact.

 Please report any bugs to TERRY MILLER at Tkmille@ConocoPhillips.Com

 INSTALLATION INSTRUCTIONS:

 THE INSTALLATION INTRUCTIONS ARE IN MEMBER "$INSTALL"

 MEMBER NAMES AND DESCRIPTIONS:

     $$DOC     - THE DOCUMENTATION MEMBER FOR THE "REORGVS" FACILITY.

     $CHANGES  - CHANGE LOG OF THIS FACILITY SINCE IT WAS WRITTEN.

     @FILEXXX  - THE CBT INDEX MEMBER FOR THE "REORGVS" FACILITY.

     $INSTALL  - THE COMPLETE SET OF INSTALLATION PROCEDURES FOR
                 THE "REORGVS" FACILITY.

      INSTALL  - THE INSTALLATION EXEC. THIS EXEC PROMPTS FOR
                 RUNTIME INSTALL INFORMATION AND THEN ALLOCATES
                 THE RUNTIME LIBRARIES.  SEE MEMBER "$INSTALL"
                 FOR THE COMPLETE SET OF INSTALL INSTRUCTIONS.

     INSTALL2  - JCL TO ASSEMBLE THE TWO ASSEMBLER SOURCE PROGRAMS
                 USED BY THE "REORGVS" FACILITY. SEE MEMBER "$INSTALL"
                 FOR THE COMPLETE SET OF INSTALL INSTRUCTIONS.

     INSTALL3  - JCL TO COPY THE "REORGVS" REXX EXEC TO YOUR
                 FACILITY'S SYSPROC LIBRARY. SEE MEMBER "$INSTALL"
                 FOR THE COMPLETE SET OF INSTALL INSTRUCTIONS.

     INSTALL4  - JCL TO COPY THE "REORGVS" ISPF HELP PANEL TO YOUR
                 FACILITY'S SYSHELP LIBRARY. SEE MEMBER "$INSTALL"
                 FOR THE COMPLETE SET OF INSTALL INSTRUCTIONS.

      REORGVS  - THE INVOKING REXX EXEC.  THIS EXEC INVOKES THE
                 ISPF ENVIRONMENT IF CALLED FROM THE FOREGROUND.
                 IT ALSO CALLS EXEc REORGVSX.

      REORGVSX - THIS EXEC TAILORS THE SKELETON JCL MEMBER
                 ("REORGVSS") AND SUBMITS THE REORGANIZATION JOB
                 TO REORGANIZE A VSAM CLUSTER.

                 THIS REXX EXEC WILL BE PLACED INTO A "SYSPROC"
                 LIBRARY DURING THE INSTALL PROCESS WHERE IT CAN
                 BE INVOKED FROM EITHER FOREGROUND OR BACKGROUND TSO.

                 IF INVOKED FROM THE FOREGROUND, THE USER WILL ENTER
                 THE REORG PARMS ON AN ISPF PANEL (REORGPN1).

                 USERS CAN NOT ONLY REORGANIZE A VSAM CLUSTER USING
                 THIS EXEC, BUT THEY CAN ALSO INCREASE OR DECREASE
                 THE DATA COMPONENT'S PRIMARY AND SECONDARY SPACE
                 ALLOCATION VALUES BY A SPECIFIED PERCENTAGE.

                 BACKGROUND EXAMPLE INVOCATION SCENARIOS:

                 1) %REORGVS my.vsam.dataset
                 2) %REORGVS my.vsam.dataset HLQ(SYS5)
                 3) %REORGVS my.vsam.dataset HLQ(SYS5) PRI(+05)
                 4) %REORGVS my.vsam.dataset PRI(+10)
                 5) %REORGVS my.vsam.dataset PRI(+10) SEC(+10)
                 6) %REORGVS my.vsam.dataset PRI(-50) SEC(-50)
                 7) REORGVS my.vsam.dataset TEST
                 8) REORGVS my.vsam.dataset PRI(+10)  SEC(+10) TEST

                 BACKGROUND EXAMPLE EXPLANATIONS:

                 1) REORG Vsam Cluster named 'MY.VSAM.DATASET'
                 2) REORG Vsam Cluster named 'MY.VSAM.DATASET'
                       and create work datasets with the HLQ of 'SYS5'.
                 3) REORG Vsam Cluster named 'MY.VSAM.DATASET'
                       and create work datasets with the HLQ of 'SYS5'
                       and increase the data component's primary
                       allocation units value by 5%
                 4) REORG Vsam Cluster named 'MY.VSAM.DATASET'
                       and increase the data component's primary
                       allocation units value by 10%
                 5) REORG Vsam Cluster named 'MY.VSAM.DATASET'
                       and increase the data component's primary
                       allocation units value by 10% and increase
                       data component's secondary allocation units
                       value by 10%. (Note, if the secondary
                       allocation unit is presently zero, it will
                       remain 0 after the adjustment).
                 6) REORG Vsam Cluster named 'MY.VSAM.DATASET'
                       and decrease the data component's primary
                       allocation units value by 50% and decrease
                       data component's secondary allocation units
                       value by 50%. (Note, if the secondary
                       allocation unit is presently zero, it will
                       remain 0 after the adjustment).
                 7) Test the Reorganization (Simulation pass)
                       of the Vsam Cluster named
                       'MY.VSAM.DATASET'.  Does not affect the
                       Cluster on a TEST pass simulation.
                 8) Test the Reorganization (Simulation pass) of
                       the Vsam Cluster named 'MY.VSAM.DATASET'
                       and of increasing the primary allocation
                       units by +10% and of increasing the
                       secondary allocation units by +10%.  Does
                       not affect the Cluster on a TEST pass
                       simulation.

      REORGVS1 - THIS REXX EXEC BUILDS IDCAMS "LISTCAT" COMMANDS
                 TO LIST THE CLUSTER AND OBTAIN REALLOCATION
                 parameters.  IT ALSO BUILDS THE IDCAMS "EXPORT"
                 AND "IMPORT" STATEMENTS TO EXPORT/IMPORT THE
                 CLUSTER DATA IN IDCAMS STEPS.

                 NO TAILORING IS REQUIRED FOR THIS EXEC.  IT WILL
                 RESIDE IN "XXXXXXXX.REORGVS.EXEC", BUT THIS EXEC
                 LIBRARY DOES NOT NEED TO BE CONCATENATED TO A
                 SYSPROC CONCATENATION ALLOCATION.

      REORGVS2 - THIS REXX EXEC INPUTS AN IDCAMS "LISTCAT" SYSPRINT
                 REPORT AND PARSES OUT THE PARAMETERS TO REALLOCATE
                 THE VSAM CLUSTER BY BUILDING IDCAMS "DEFINE CLUSTER"
                 COMMANDS.  IF THE CLUSTER HAS ALTERNATE
                 INDEX ASSOCIATES, IT CREATES IDCAMS "LISTCAT"
                 COMMANDS FOR THE AIX COMPONENTS TO BE PROCESSED
                 IN AN IDCAMS STEP.

                 NO TAILORING IS REQUIRED FOR THIS EXEC.  IT WILL
                 RESIDE IN "XXXXXXXX.REORGVS.EXEC", BUT THIS EXEC
                 LIBRARY DOES NOT NEED TO BE CONCATENATED TO A
                 SYSPROC CONCATENATION ALLOCATION.

      REORGVS3 - THIS REXX EXEC INPUTS AN IDCAMS "LISTCAT" SYSPRINT
                 REPORT AND PARSES OUT THE PARAMETERS TO REALLOCATE
                 THE AIX COMPONENT BY BUILDING IDCAMS "DEFINE AIX",
                 "DEFINE PATH", AND "BLDINDEX" COMMANDS TO BE
                 EXECUTED BY AN IDCAMS STEP.

                 NO TAILORING IS REQUIRED FOR THIS EXEC.  IT WILL
                 RESIDE IN "XXXXXXXX.REORGVS.EXEC", BUT THIS EXEC
                 LIBRARY DOES NOT NEED TO BE CONCATENATED TO A
                 SYSPROC CONCATENATION ALLOCATION.

      REORGVS4 - THIS REXX EXEC INPUTS A RACF "LISTDSD" SYSPRINT
                 REPORT AND PARSES OUT THE PARAMETERS TO RE-ISSUE
                 THE RACF COMMANDS TO ADD BACK DISCRETE RACF PROFILES
                 (IF THEY EXIST).

                 THIS EXEC (AND FACILITY) ASSUMES THAT THE INSTALLATION
                 USES RACF FOR ITS SECURITY PRODUCT.  IF RACF IS
                 NOT INSTALLED AT YOUR FACILITY, YOU WILL WANT TO
                 OMIT CERTAIN STEPS FROM YOUR REORGVS SKELETON
                 LIBRARY (INCLUDING THE ONE WHICH EXECUTES THIS EXEC -
                 SEE MEMBER "$$DOC FOR FURTHER INSTRUCTIONS ON THIS).

                 NO TAILORING IS REQUIRED FOR THIS EXEC.  IT WILL
                 RESIDE IN "XXXXXXXX.REORGVS.EXEC", BUT THIS EXEC
                 LIBRARY DOES NOT NEED TO BE CONCATENATED TO A
                 SYSPROC CONCATENATION ALLOCATION.

      REORGVS5 - THIS REXX EXEC INPUTS A "GOOD" OR "BAD" PARAMETER
                 AND LOGS THE REORGANIZATION ENTRY TO A LOG FILE.
                 THE LOG FILE IS DYNAMICALLY ALLOCATED BEFORE THE
                 ENTRY IS LOGGED.  THERE WILL BE ONE ENTRY FOR EACH
                 REORG JOB SUBMITTED. IT WILL EITHER LOG A SUCCESS
                 OR A FAILURE WITH THE CLUSTER DATASET NAME, EXPORT
                 IMAGE DATASET NAME, AND THE DATE AND TIME.
                 THE EXEC CALLS ANOTHER EXEC CALLED "DYNALC" TO
                 DYNAMICALLY ALLOCATE THE LOG FILE.  "DYNALC" CALLS
                 ASSEMBLER PROGRAM "WAITFOR" (IF IT CANNOT
                 ALLOCATE THE LOG FILE ON THE FIRST ATTEMPT) WHICH
                 IS LINKED INTO THE REORGVS LOAD LIBRARY.

                 NO TAILORING IS REQUIRED FOR THIS EXEC.  IT WILL
                 RESIDE IN "XXXXXXXX.REORGVS.EXEC", BUT THIS EXEC
                 LIBRARY DOES NOT NEED TO BE CONCATENATED TO A
                 SYSPROC CONCATENATION ALLOCATION.

      REORGVS6 - THIS REXX INPUTS AN IDCAMS EXPORT SYSPRINT REPORT
                 FILE AND PARSES OUT THE RETURN CODES AND MESSAGES
                 TO DETERMINE THE RESULT OF THE EXPORT FUNCTION.
                 EXPORT WILL RETURN A RC=12 WHEN A VSAM CLUSTER IS
                 EMPTY (WITH MSG "IDC3351I" AND FEEDBACK CODE 160).
                 THIS PROGRAM DOES A SMART ANALYSIS TO CHECK
                 THE RESULTS OF THE EXPORT COMMAND INSTEAD OF USING
                 THE RETURN CODE SET BY EXPORT.

                 NO TAILORING IS REQUIRED FOR THIS EXEC.  IT WILL
                 RESIDE IN "XXXXXXXX.REORGVS.EXEC", BUT THIS EXEC
                 LIBRARY DOES NOT NEED TO BE CONCATENATED TO A
                 SYSPROC CONCATENATION ALLOCATION.

      DYNALC   - THIS REXX EXEC PERFORMS THE DYNALLOCATION FOR THE
                 LOG FILE ALLOCATION.  IT TRIES UP TO 1800 TIMES TO
                 DYNAMICALLY ALLOCATE THE LOG FILE IF THE FILE IS
                 BUSY AND WAITS FOR A 3 SECOND INTERVAL BETWEEN
                 ALLOCATION ATTEMPTS (FOR A TOTAL ELAPSED WINDOW OF
                 90 MINUTES BEFORE IT TIMES OUT).  IT CALLS PROGRAM
                 "WAITFOR" BETWEEN ALLOCATION ATTEMPTS TO ACCOMPLISH
                 THE ECB WAIT INTERVAL IF THE LOG FILE CANNOT BE
                 ALLOCATED ON THE FIRST ATTEMPT.

                 NO TAILORING IS REQUIRED FOR THIS EXEC.  IT WILL
                 RESIDE IN "XXXXXXXX.REORGVS.EXEC", BUT THIS EXEC
                 LIBRARY DOES NOT NEED TO BE CONCATENATED TO A
                 SYSPROC CONCATENATION ALLOCATION.

      REORGPN1 - ISPF PANEL USED TO ENTER THE REORG SPECIFICATIONS
                 IF THE REORGVS EXEC IS INVOKED FROM THE FOREGROUND.

      REOHGPN1 - ISPF HELP PANEL FOR ISPF PANEL REORGPN1.

      REORGPN2 - ISPF PANEL USED TO DISPLY THE MESSAGE RESULTS FROM
                 THE CLUSTER REORG IF THE REORGVS EXEC IS INVOKED
                 FROM THE FOREGROUND.

      REORGVSH - ISPF HELP PANEL FOR THE "REORGVS" COMMAND.
                 THIS MEMBER WILL BE COPIED TO YOUR FACILITY'S
                 "SYSHELP" ISPF LIBRARY DURING THE INSTALL PROCESS
                 (OPTIONAL INSTALL STEP).

      REORGVSS - SUBMIT JCL SKELETON MEMBER.  THIS MEMBER WILL BE
                 TAILORED AND SUBMITTED INTO THE INTERNAL READER
                 BY THE "REORGVS" EXEC WHEN IT IS EXECUTED.

                 DO NOT CHANGE THIS MEMBER ONCE IT IS INSTALLED
                 INTO THE "XXXXXXXX.REORGVS.CNTL" JCL LIBRARY !!!!!

      ABENDER  - THIS IS AN ABEND PROGRAM ASSEMBLER SOURCE CODE.
                 IT IS EXECUTED TO PRODUCE AN ABEND IF ERRORS
                 OCCUR DURING THE REORGVS PROCESSING.

                 THIS PROGRAM WILL BE ASSEMBLED AND LINKED INTO LOAD
                 LIBRARY "XXXXXXXX.REORGVS.LOADLIB" DURING THE
                 INSTALL PROCESS.  IT IS USED IN THE "REORGVSS"
                 MEMBER.

      WAITFOR  - STIMER MACRO WAIT PROGRAM IN ASSEMBLER SOURCE CODE.
                 IT ISSUES AN ECB WAIT FOR AN INTERVAL OF TIME
                 IF THE LOG FILE CANNOT BE ALLOCATED ON THE FIRST
                 ATTEMPT.

                 THIS PROGRAM WILL BE ASSEMBLED AND LINKED INTO LOAD
                 LIBRARY "XXXXXXXX.REORGVS.LOADLIB" DURING THE
                 INSTALL PROCESS.  IT IS CALLED IN THE "DYNALC"
                 REXX EXEC.

      IVPTEST  - SAMPLE JCL TO REORG A VSAM CLUSTER.  CAN BE USED
                 TO TEST THE FACILITY ONCE IT IS INSTALLED.

     REORGVSJ  - JCL TO RUN THE REORGVS FACILITY IN THE TSO BACKGROUND.

                 (THE "REORGVS" EXEC CAN ALSO BE RUN FROM THE TSO
                  FOREGROUND FROM THE SYSPROC LIBRARY.  THIS IS
                  WHERE THE INSTALL PROCESS COPIES IT TO).


 ASSUMPTIONS
 -----------

   THIS FACILITY ASSUMES THE USE OF IBM'S RACF PRODUCT AS A SECURITY
   PRODUCT.  IF YOUR INSTALLATION USES ANOTHER SECURITY PRODUCT, THIS
   FACILITY WILL NEED TO BE MODIFIED TO WORK.  THE RACF SECURITY
   IS USED ONLY TO RE-CREATE RACF DISCRETE DATASET CLASS PROFILES.
   IF DISCRETE (DISCRET TO A VOLSER) PROFILES ARE NOT BEING USED,
   THEN THE FOLLOWING NINE STEPS CAN BE OMITTED FROM THE REORG JCL
   STREAM IN SKELETON MEMBER "REORGVSS":

     GETRACF, CHK500, ABEND500, BLDRACF, CHK700, ABEND700,
     GENPROF, CHK750, ABEND750.

   ALSO, THE FOLLOWING REXX EXEC CAN BE DISCARDED:  REORGVS4

 CERTIFICATION
 -------------

 BATCH:

   THESE REXX EXECS AND JCL HAVE BEEN RUN IN A Z/OS ENVIRONMENT.
   THE SOURCE CODE FOR "ABENDER" AND "WAITFOR" HAVE BEEN ASSEMBLED
   WITH THE HIGH-LEVEL ASSEMBLER AND TESTED.  THEY DO NOT NEED TO
   RUN IN AN AUTHORIZED ENVIRONMENT.  THERE ARE NO SPECIAL
   REQUIREMENTS FOR ASSEMBLING AND LINKING THESE TWO MODULES.

 PROBLEM REPORTING
 -----------------

 PLEASE REPORT ANY BUGS OR SUGGESTIONS FOR IMPROVEMENT TO:
        TERRY MILLER AT Tkmille@ConocoPhillips.com

```

