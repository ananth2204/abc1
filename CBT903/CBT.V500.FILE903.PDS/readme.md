
## $FMTDOC.txt
```
Input/Output Field Editing Routines

    (Assembler)  I first started putting together this collection
    when I discovered BIF DEDIT didn't do much for fields entered
    into my CICS programs.  But the collection first became a
    set, and also became re-entrant, back in 1993 when I had some
    spare time.  The logic for the numbers to words routine
    (OFMTMONY) was originally in written in COBOL back in 1976
    when another programmer told me I couldn't write the routine
    in COBOL efficiently enough to run in production.

    I updated the installation procedure on September 3, 2003.
    So if you have an earlier version, and have checked back here
    and are worried that the version you got on an earlier date
    needs updating, relax.  There have been no significant
    changes to the routines themselves, just an update to the
    jobstreams that load them onto your system.  And I made a
    minor change to the Installation Verification COBOL program's
    report (the output for IFMTLJST was not printing the field
    returned from the assembler routine).

    The installation/verification jobstream is in fmt$load.tgz
    ÝMD5: DF68D84AB0B125FB0797D25DCEF4254D¨.  This is an IEBUPDTE
    job that will create a PDS containing the assembler and COBOL
    source and three jobstreams, plus an index member ($INDEX).
    As configured for my system, the source/jobstream PDS is on a
    3330, VOL=SER=JAY001, and is named JAY01.FORMAT.SOURCE.  You
    will probably want to change all of those parameters for your
    system.  When the installation jobs run, they will create a
    PDS load library.  Again, on my system it is configured to
    reside on the same 3330 as the source library and is named
    JAY01.FORMAT.LOADLIB.  These two datasets are referenced in a
    number of DD cards in the jobstreams, so it would probably be
    easiest for you to use a text editor on your host OS
    (Linux/Windows/???) and make all the changes in the "reload"
    jobstream before you submit it to MVS.

    Once the changes above are correct for your system, and you
    have created the source/JCL PDS, submit the jobstream:
    FMT$INST from the source/JCL PDS.  The first step of this job
    deletes the target load library so you can resubmit this job
    if you need to restart it or want to recreate the load
    library for any reason.  The second step simply submits the
    jobstream:  FMT$ASM from the source/JCL PDS.  This job
    assembles and link-edits all eight of the routines to the
    load library PDS.  If you want to run the installation
    verification program, submit the jobstream:  FMT$IVP.  This
    will compile and run a COBOL program which calls all the
    routines with a test data value.

```

