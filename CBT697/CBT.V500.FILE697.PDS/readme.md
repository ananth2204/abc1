
## $DOC.txt
```
This PDS contains documentation and JCL to install code on a system
running Perl and PostgreSQL. This code emulates the DB2 code supplied
by IBM with CICS/Transaction server 1.3.

This documentation assumes that you or your are familar with:
    z/OS
    CICS/Transaction Server 1.3.
    Linux
    Perl on Linux
    PostgreSQL on Linux
    How to do SQL queries (at the psql prompt and/or in Perl)

This documentation does not attempt to teach you about these.

In particular, this PDS contains the following members:
1. $DOC     - This member, which contains the basic documentation
2. DFH0FORC - Example JCL to run DFH0FORC, which will create the
              sequential file version of the CICS CSD information.
3. RECEIVE  - The basic JCL to create the file which is to be
              ftp'ed to the Linux system and then ftp that file
              to the Linux system.
              This member must be customized as described therein.
4. TARFILE  - This member contains the output of an XMIT command.
              This member must be RECEIVE'd (see RECEIVE member)
              in order to create a sequential file. This sequential
              file must then be binary ftp'ed to the Linux system
              upon which the system will run. This sequential file
              is the output from a tar command, run on Linux, which
              was binary ftp'ed to a z/OS system. Don't bother trying
              to read it, it looks like binary junk.

=======================================================

Steps required to install and use this facility

1. If you have not already done so, compile the DFH0FORC program into
   a load library. This program is supplied by IBM in the SDFHSAMP
   library.

2. Run the RECEIVE job. This job will create the tar file in an MVS
   sequential file. The second step will the ftp this to your Linux
   system. Please note that you must customize the ftp step with the
   IP address of your Linux system as well as the appropriate userid
   and password on your Linux system.

3. Run the DFH0FORC program referenced above. This creates a
   sequential file with the contents of the CICS CSD. Example JCL
   exists in the DFH0FORC member.

4. The remainder of the steps must be done on your Linux system.
   Logon to it.

5. Change to the "cicsrdo" subdirectory created by the RECEIVE job.

6. Use ftp to download the dataset created by the DFH0FORC job.  You
   must remember to preserve trailing blanks or the load Perl programs
   will not work correctly. If you are using the IBM TCP/IP stack,
   this is done with the ftp subcommand:
       quote site trailingblanks
   This is an "ascii" download.  In my examples below, I assume that
   the DFH0F0RC output is downloaded to the file "dfh0forc.data".

7. Create the "cicsrdo" database and tables by entering the following
   command:
     psql <create_rdo_tables.psql
   Note that this psql control file will drop and create the "cicsrdo"
   database, thus loosing any information contained therein.

   Note that all my Perl programs and psql script depend on the
   database being named "cicsrdo". If you want to use some other database
   to contain the tables, you must search for where "cicsrdo" is used as
   a database name and change it to your database name.

8. Run the Perl program "dfh$sqlt.pl" by entering:
       ./dfh\$sqlt.pl dfh0forc.data
   This program will abort (die) with an error message if there is any
   problem.  The program will output a message for every 1000 lines of
   input which it reads. This is for your comfort that it is doing
   something. This program does not issue a "commit" until all records
   have been successfully processed.  When this program completes, the
   CICS CSD database informatin will have been loadede into a number
   of PostgreSQL tables, which are The easiest way to find the names
   of the tables created and the columns defined in them is by looking
   at the dfh$sqlt.txt file.

   If you need to recreate the dfh$sqlt.pl program, you must have
   downloaded the DFH$SQLT member of SDFHSAMP as dfh$sqlt.txt
   and run the program:
     export database='cicsrdo'
     mkdb2load dfh$sqlt.txt >dfh$sqlt.pl
     chmod 755 dfh$sqlt.pl

9.  At this point the "cicsrdo" database will have all of its tables
    defined and information loaded into them.

10. You will periodically need to rerun the DFH0FORC job, download the
    output and rerun the dfh$sqlt.pl program as documented in step 8.
    This is to keep the information current. Note that the dfh$sqlt.pl
    program will remove all the old information.

=======================================================

Maintenance of the programs and scripts is the your responsibility. If
you go to a new release of CICS and the CSD has been enhanced, there
is a possibility that you will need to modify the dfh$sqlt.pl script.
Hopefully, you can do this by downloading the DFH$SQLT member of
SDFHSAMP and rerunning mkdb2load.pl using it.

=======================================================

The contents of the tar file are:

bad_tran_def.psql
  This is an example psql script which will show transaction which
  are likely to be unexecutable.

create_rdo_tables.psql
  This psql script will DROP (delete) and CREATE the CICS RDO tables.

dfh$sqlt.pl
  This Perl program will load the RDO information into the appropriate
  tables.

dfh$sqlt.txt

mkdb2load.pl
  This Perl program is used to create the dfh$sqlt.pl program. It is
  run by issuing the commands:

  export database='cicsrdo'
  ./mkdb2load.pl dfh$sqlt.txt >dfh$sqlt.pl
  chmod 755 dfh$sqlt.pl


  You must export the environment variable "database" to name the
  database in which the tables are created. If you use something other
  than "cicsrdo", then you must change all the *.psql files to use that
  database in the "\c cicsrdo" control statement.

  The plus of this is that it is driven by dfh$sqlt.txt file.  This
  means that if IBM changes the CICS CSD for new information and
  updates the DFH$SQLT member in SDFHSAMP the dfh$sqlt.pl program can
  be updated simply. I assure you that you don't want to create these
  programs by hand.

  This program removes all DB2 comments and any data in columns 73-80
  so there is should be no need to "clean up" the DB2 LOAD control
  statements.

  Actually, this program should be able to create a Perl program to
  load any set of tables for which you have LOAD control statement of
  the DB2 utilities.


mktar.sh
  This shell script creates the gzip'ed tar file with all the *.pl,
  *.sh, *.txt, *.psql files in it.

noseq.pl
  This Perl program is used to remove any sequence numbers in columns
  73 through 80, then remove any trailing blanks.

```

