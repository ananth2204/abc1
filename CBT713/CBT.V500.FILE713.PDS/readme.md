
## $$$DOC.txt
```
                               EMPTYPDS

The EMPTYPDS utility deletes all members in a PDS or PDS-E data
set.  For a PDS, EMPTYPDS resets the high water mark for the data
set so that the next member MVS writes to the data set
immediately follows the directory.

This version of EMPTYPDS is the only directory clear utility
available through CBT that supports PDSE data sets, and does not
require the program to the APF authorized, or requires a second
step that performs an IEBCOPY "compress in place" of the data set
to reset the high water mark for the data set.

JCL

Use the following JCL to run EMPTYPDS.

//stepnm  EXEC PGM=EMPTYPDS
//SYSPRINT DD  SYSOUT=*
//SYSUT2   DD  ... Data set descriptor for a PDS or PDSE data set ...

-----------------------------------------------------------------
|                      DD Statements                            |
|----------+----------+-----------------------------------------|
| DD name  | Comments | Description                             |
|----------+----------+-----------------------------------------|
| SYSPRINT | Optional | Message data set                        |
|----------+----------+-----------------------------------------|
|          |          | Data set descriptor for a PDS or PDSE   |
| SYSUT2   | Required | containing a directory to clear.  A     |
|          |          | PDSE data set must be allocated with    |
|          |          | DISP=OLD or DISP=MOD.                   |
-----------------------------------------------------------------

Messages

EPD001I SYSPRINT NOT ALLOCATED TO STEP

Reason: EMPTYPDS determined that the SYSPRINT DD statement is not
allocated to the step.
Action: EMPTYPDS continues execution.  No additional messages
will be directed to either SYSPRINT or the operator console.
Response: Specify a SYSPRINT DD statement the next time EMPTYPDS
is run.

EPD002E SYSUT2 NOT ALLOCATED TO STEP

Reason: EMPTYPDS determined no SYSUT2 DD statement is allocated
to the step.
Action: EMPTYPDS terminates.
Response: Specify a SYSUT2 DD statement the next time EMPTYPDS is
run.

EPD003E SYSUT2 DATA SET NOT ON VOLUME

Reason: EMPTYPDS determined the data set defined by the SYSUT2 DD
statement is not on the volume allocated to the statement.
Action: EMPTYPDS terminates.
Response: Correct the SYSUT2 DD statement and rerun EMPTYPDS.

EPD004E SYSUT2 DATA SET IS NOT PARTITIONED

Reason: EMPTYPDS determined the data set defined by the SYSUT2 DD
statement is not a partitioned data set.
Action: EMPTYPDS terminates.
Response: Correct the SYSUT2 DD statement and rerun EMPTYPDS.

EPD005E SYSUT2 DATA SET NOT ALLOCATED OLD OR MOD

Reason: EMPTYPDS determined the data set defined by the SYSUT2 DD
statement is a PDSE data set, but is not allocated using the
DISP=OLD or DISP=MOD parameter.  EMPTYPDS cannot clear the data
set.
Action: EMPTYPDS terminates.
Response: Correct the SYSUT2 DD statement and rerun EMPTYPDS.

ALL MEMBERS SCRATCHED FROM PDS

Reason: EMPTYPDS deleted all members in the PDS or PDSE.  The
high water mark for a PDS data set has been reset.
Action: EMPTYPDS terminates.
Response: None.

Message EPD001I is directed to the operator console, and also to
the JES job log and JES system messages data sets.  All other
messages are directed only to SYSPRINT.

The SYSPRINT DD statement is optional so that existing JCL that
runs earlier versions of EMPTYPDS will continue to operate
without error.
```

