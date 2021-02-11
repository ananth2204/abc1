
## $$$DOC.txt
```

  ALL OF OUR USERMODS ARE IN MVS.OSMAINT.USERMODS ON THE TECPLEX.

  Each usermod(LSES5**) member has a corresponding member suffixed with
  a "J".  The members with the "J" suffixes are sample jcl install
  members.

  FOR JES2 WE HAVE THE FOLLOWING usermods - These are ALL of our JES2
   mods - most folks who are interested in only using the mellon mods
  should refer to the next section, entitled -

    " THE FOLLOWING CAN BE CONSIDERED MELLON MOD REPLACEMENTS "

all of our JES2 usermods:

MOD NAME   IMPLEMENTED     LMOD NAME   DESCRIPTION
LSES500   ZOS6-09/01/2005  STJTABS  - CREATES OUR EXTENSIONS TO JQE AND JCT
LSES502   ZOS6-09/01/2005  STSCX01A - JES2 EXIT1 - BANNER PAGE EXIT (NON 3800)
LSES503   zOS6-09/01/2005  STSCX04A - parses /*ROUTE cards
LSES504   ZOS6-09/01/2005  STSCX04B - PARSES /*BEFORE/*AFTER/*WITH AND /*CNTL
LSES505   ZOS6-09/01/2005  STSCX05A - PROCESS $REPEXIT AND $ADDEXIT COMMANDS
LSES506   zOS6-09/01/2005  STSCX05B - prevents purging jobs by range
LSES507   ZOS6-09/01/2005  STSCX06A - MOVES VALID XEQ VALUES TO SCHENV VALUES
LSES509   ZOS6-09/01/2005  STSCX15A - FORCES FCB LOAD UNLESS CHGING STD FORMS
LSES510   ZOS6-09/01/2005  STSCX20A - END OF INPUT - MOVE JCT INFO TO JQE
LSES511   zOS6-09/01/2005  STSCX36A - SAF process of RJE submitted jobs
LSES512   ZOS6-09/01/2005  STSCX49A - IMPLEMENT BEFORE|AFTER|WITH|CNTL USAGE
LSES513   ZOS6-09/01/2005  STSCX100 - FCB SETUP / TRANSLATION USER EXIT100
LSES514   ZOS6-09/01/2005  HASPPRPU - INSERT USER EXIT100 INTO HASPPRPU CODE
-------- ---------------   ---------------------------------------------

 ***********

OF THESE MODS, THE FOLLOWING CAN BE CONSIDERED MELLON MOD REPLACEMENTS

 ***********

MOD NAME   IMPLEMENTED     LMOD NAME   DESCRIPTION
LSES500   ZOS6-09/01/2005  STJTABS  - CREATES OUR EXTENSIONS TO JQE AND JCT
LSES503   zOS6-09/01/2005  STSCX04A - parses /*ROUTE cards
LSES504   ZOS6-09/01/2005  STSCX04B - PARSES /*BEFORE/*AFTER/*WITH AND /*CNTL
LSES507   ZOS6-09/01/2005  STSCX06A - MOVES VALID XEQ VALUES TO SCHENV VALUES
LSES510   ZOS6-09/01/2005  STSCX20A - END OF INPUT - MOVE JCT INFO TO JQE
LSES512   ZOS6-09/01/2005  STSCX49A - IMPLEMENT BEFORE|AFTER|WITH|CNTL USAGE

 ***********
 ***********

   The installation instructions for the Mellon MODs only, can be found
   in member DOCINS.

   The overview documentation for the mellon mods is in member DOCOVW.

   The user documentation for the mellon mods is in member DOCUSR.

 ***********
 ***********

* * * PLEASE NOTE ! * * *

*
*    SPECIAL THANKS GO TO BOB BREAK OF ST. LOUIS FOR THE ORIGINAL CODE
*  TO PARSE THE "/*ROUTE XEQ RESNAME" CARDS AND SET THE APPROPRIATE
*  EXECUTION ENVIRONMENT.
*
*    SPECIAL THANKS TO JUDY RUNT OF WISCONSIN ELECTRIC FOR THE ORIGINAL
*  CODE TO HANDLE THE "/*CNTL BEFORE|AFTER|WITH,RESNAME" AND "/*CNTL
*  RESNAME,EXC|SHR" ROUTINES.  THE USE OF THE BLOCK EXTENSION REUSABLE
*  TABLES, and BERT'S, TO EXTEND THE JCT AND JQE.
*
*  although some changes have been made to all of the code, their
*  combined help was invaluable.
*
*

  It is customary to transfer a PDS such as this in tso xmit format -
  to create the xmit format dataset, use the following command -
   "xmit n32.t0sm0,outdsname('t0sm0.xmit.jes2mods'),dataset('t0sm0.tso.
    jes2mods")
  where t0sm0.xmit.jes2mods is an fb 80X3120 dataset, and
  where t0sm0.tso.jes2mods is the pds to be sent.
  Be sure to transfer the file, type=binary when sent via e-mail.
```

