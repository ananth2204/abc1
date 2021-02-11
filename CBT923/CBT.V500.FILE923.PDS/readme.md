
## $$README.txt
```
SQLite 3.8.7 for z/OS UNIX
==========================
This is a port of the SQLite for use on z/OS.  The files in the UNIX
directory were originally downloaded from
http://www.sqlite.org/download.html on 2104-10-18T20:47:00Z (18 Oct 2014
at 10:47 p.m. GMT time).  The files in the directory are the files from
both the sqlite-autoconf-3080700.tar.gz and the
sqlite-amalgamation-3080700.zip .  They were orinally downloaded to my
Linux/Intel machine at home. I combined them there and created a tar
file from the combined directory contents. I then uploaded the tar file
to z/OS. I unwound the tar file into a UNIX directory using the command:

pax -ofrom=iso8859-1,to=ibm-1047 -rf "//sqlite.v3r8m7.tar"

This port was very simple due to the dilligence of the original author,
Dr. Richard Hipp, who had already implemented the EBCDIC logic. All that
I did was a bit of packaging and verification on z/OS UNIX.

Member in this library:
-----------------------
$$README - You're reading it.
$README  - The generic README for SQLite
ASMACL   - Compile and link SQLITE3A
COBSQLTE - COBOL copy book for SQLite functions
COBTEST1 - JCL to run TESTCOB1 program
COBTEST2 - JCL to run TESTCOB2 program
IGYWCL   - JCL to compile and link the TESTCOB1 and TESTCOB2 programs
LINK     - General template JCL for linking SQLite into a program.
LINKLIB  - TSO XMIT of the LINKLIB for SQLite 3.8.7
PAXFULL  - Compressed PAX archive of the source & compiled programs.
PAXRUN   - Compressed PAX archive of the "run time" compiled programs.
PLICB    - JCL to compile the PL/I test program.
PLISQLTE - PL/I %INCLUDE member for SQLite 3.8.7
SQLITE3A - Assembler source for the "normal" CALL interface to SQLite.
SQLITE3O - Object code from compiling the sqlite3.c program under UNIX.
TESTCOB1 - COBOL source code for a test.
TESTCOB2 - COBOL source code for a test.
TESTDB   - Binary copy of a test SQLite for z/OS data base file.
TSTPLI1  - PL/I source code for a test.
UNPAX    - JCL to unwind one of the PAX archives in this library.

Contents of PAXRUN file:
------------------------
./
./lib/
./lib/pkgconfig/
./lib/pkgconfig/sqlite3.pc
./lib/libsqlite3.la
./lib/libsqlite3.a
./bin/
./bin/sqlite3
./include/
./include/sqlite3.h
./include/sqlite3ext.h
./share/
./share/man/
./share/man/man1/
./share/man/man1/sqlite3.1

Contents of PAXFULL file:
-------------------------
sqlite-v3r8m7/
sqlite-v3r8m7/Makefile.am
sqlite-v3r8m7/config.sub
sqlite-v3r8m7/aclocal.m4
sqlite-v3r8m7/depcomp
sqlite-v3r8m7/sqlite3.1
sqlite-v3r8m7/configure.ac
sqlite-v3r8m7/README
sqlite-v3r8m7/shell.c
sqlite-v3r8m7/INSTALL
sqlite-v3r8m7/config.guess
sqlite-v3r8m7/missing
sqlite-v3r8m7/tea/
sqlite-v3r8m7/tea/pkgIndex.tcl.in
sqlite-v3r8m7/tea/generic/
sqlite-v3r8m7/tea/generic/tclsqlite3.c
sqlite-v3r8m7/tea/aclocal.m4
sqlite-v3r8m7/tea/configure.in
sqlite-v3r8m7/tea/README
sqlite-v3r8m7/tea/win/
sqlite-v3r8m7/tea/win/nmakehlp.c
sqlite-v3r8m7/tea/win/rules.vc
sqlite-v3r8m7/tea/win/makefile.vc
sqlite-v3r8m7/tea/tclconfig/
sqlite-v3r8m7/tea/tclconfig/tcl.m4
sqlite-v3r8m7/tea/tclconfig/install-sh
sqlite-v3r8m7/tea/Makefile.in
sqlite-v3r8m7/tea/license.terms
sqlite-v3r8m7/tea/configure
sqlite-v3r8m7/tea/doc/
sqlite-v3r8m7/tea/doc/sqlite3.n
sqlite-v3r8m7/sqlite3.c
sqlite-v3r8m7/sqlite3.pc.in
sqlite-v3r8m7/ltmain.sh
sqlite-v3r8m7/install-sh
sqlite-v3r8m7/sqlite3.h
sqlite-v3r8m7/Makefile.in
sqlite-v3r8m7/sqlite3ext.h
sqlite-v3r8m7/configure
sqlite-v3r8m7/do_config.jcl
sqlite-v3r8m7/do_config.sh
sqlite-v3r8m7/do_make.jcl
sqlite-v3r8m7/sqlite-run/
sqlite-v3r8m7/sqlite-run/lib/
sqlite-v3r8m7/sqlite-run/lib/pkgconfig/
sqlite-v3r8m7/sqlite-run/lib/pkgconfig/sqlite3.pc
sqlite-v3r8m7/sqlite-run/lib/libsqlite3.la
sqlite-v3r8m7/sqlite-run/lib/libsqlite3.a
sqlite-v3r8m7/sqlite-run/bin/
sqlite-v3r8m7/sqlite-run/bin/sqlite3
sqlite-v3r8m7/sqlite-run/include/
sqlite-v3r8m7/sqlite-run/include/sqlite3.h
sqlite-v3r8m7/sqlite-run/include/sqlite3ext.h
sqlite-v3r8m7/sqlite-run/share/
sqlite-v3r8m7/sqlite-run/share/man/
sqlite-v3r8m7/sqlite-run/share/man/man1/
sqlite-v3r8m7/sqlite-run/share/man/man1/sqlite3.1
sqlite-v3r8m7/config.log
sqlite-v3r8m7/config.status
sqlite-v3r8m7/.libs/
sqlite-v3r8m7/.libs/libsqlite3.lai
sqlite-v3r8m7/.libs/libsqlite3.a
sqlite-v3r8m7/.libs/libsqlite3.la -> ../libsqlite3.la
sqlite-v3r8m7/Makefile
sqlite-v3r8m7/sqlite3.pc
sqlite-v3r8m7/sqlite3
sqlite-v3r8m7/.deps/
sqlite-v3r8m7/.deps/shell.Po
sqlite-v3r8m7/.deps/sqlite3.Plo
sqlite-v3r8m7/sqlite3.o
sqlite-v3r8m7/libtool
sqlite-v3r8m7/libsqlite3.la
sqlite-v3r8m7/$UPDATES
sqlite-v3r8m7/shell.o
sqlite-v3r8m7/$$README.txt
sqlite-v3r8m7/$README.txt
sqlite-v3r8m7/ASMACL.jcl
sqlite-v3r8m7/COBSQLTE.cpy
sqlite-v3r8m7/COBTEST1.jcl
sqlite-v3r8m7/COBTEST2.jcl
sqlite-v3r8m7/IGYWCL.jcl
sqlite-v3r8m7/LINK.jcl
sqlite-v3r8m7/PLICB.jcl
sqlite-v3r8m7/PLISQLTE.pli
sqlite-v3r8m7/SQLITE3A.s
sqlite-v3r8m7/TESTCOB1.cbl
sqlite-v3r8m7/TESTCOB2.cbl
sqlite-v3r8m7/TSTPLI1.pli
sqlite-v3r8m7/UNPAX.jcl
sqlite-v3r8m7/cobtest2-db.pax.Z
sqlite-v3r8m7/sqlite3.lo
```

## $README.txt
```
SQLITE 3.8.7 for z/OS
=====================

Sqlite is a self-contained, server-less, zero-configuration,
transactional SQL database engine.  This is the standard sqlite library
which is available on many UNIX and Linux systems. The code was compiled
with almost no changes. The code is dependent on z/OS UNIX System
Services.  The original code supports EBCDIC in addition to the normal
ASCII. This distribution has been compiled to support EBCDIC characters
and IEEE (BFP) floating point numbers. This latter is important because
most other z/OS languages use the historical HFP floating point.

At present, the code only has C language bindings on z/OS.  There is a
"shim" or "stub" HLASM interface program which can be called from COBOL
or PL/I to access the C subroutines. It is named SQLITE3A.  The
parameters passed into this routine are the same ones as documented in
the sqlite C API, except that the first parameter is a C style
null-delimited character string which is the name of the C subroutine to
be invoked. In COBOL, this is a Z'...' character string. The COBSQLTE
and PLISQLTE members are the COBOL COPY book and PL/I %INCLUDE members
which define COBOL or PL/I variables which contain these strings. In the
case of COBOL, the underscore characters shown in the C API names are
replace by a dash because an underscore is not valid in a COBOL data
name. The variable names are in upper case, but the values are in lower
case, due to the fact that the C subroutine names are in lower case.

Sqlite 3.8.7 is documented at http://sqlite.org, and this code runs as
described there. Therefore, no futher documentation is supplied at
present.  When the COBOL and PL/I bindings are done, those will be
documented here.

This document does _not_ attempt to teach you how to use sqlite. It
assumes you already know how to use it, or can learn it yourself. It
does attempt to explain how to use it on z/OS by showing some COBOL and
PL/I examples. If you have a C license, I strongly suggest writing your
code in C. It will be more understandable to most.

Wish list items.
----------------
1. At present, the file which contains the sqlite database must reside
   in a UNIX subdirectory. This means that the user of sqlite must have
   an z/OS UNIX identity.  I would like to be able to use a VSAM Linear
   Dataset for storing the sqlite data at some time. Mainly due to the
   number of shops which have not really embraced z/OS UNIX.  This may
   be possible using a "shim" sqlite VFS as documented here:
   http://sqlite.org/vfs.html which would use a VSAM LDS as the backing
   store for a sqlite in-memory data base.

2. Write a REXX interface.

3. Write a batch program based on the sqlite3 UNIX command. This would
   allow SQL commands to be run in a step in a batch job.

4. JDBC for Java access.


Members in this library:
------------------------
- $README  - This member. The README in markdown format.

- ASMACL   - The JCL to compile and link the SQLITE3A assembler program.
             It would be wise to run this to recompile SQLITE3A on your
             system, if at all possible.

- COBSQLTE - The COBOL copy book which defines various SQLITE3 related
             variables and initializes them.  The member contains a fair
             number of comments on how to use SQLITE3A in a COBOL
             program to invoke each of the 204(!) different sqlite
             subroutines.

- COBTEST1 - The JCL to run the TESTCOB1 program.
             Unless you are running z/OS 2.1, you need to recompile
             the program before running this test job. There are LE
             dependencies.

- COBTEST2 - The JCL to run the TESTCOB2 program.
             Unless you are running z/OS 2.1, you need to recompile
             the program before running this test job. There are LE
             dependencies.

- IGYWCL   - The JCL to compile and link the TESTCOB1 and TESTCOB2
             program. You really need to recompile these program on
             your system due to possible LE dependencies.

- LINK     - The JCL to link the SQLITE3 object code into a LINKLIB.
             This composite links in the C and LE library subroutines.

- LINKLIB  - XMIT copy of the SQL387.LINKLIB library containing the
             z/OS batch executable programs: SQLITE3A, TESTCOB1, and
             TESTCOB2. However, these program will likely only run on
             a z/OS 2.1 system due to COBOL dependencies on LE.

- PAXFULL  - This is a compressed pax archive for the entire SQLITE3
             application, Including all source code and make
             information.

- PAXRUN   - This is a compressed pax archive containing only the files
             needed to use SQLITE. This is really all you need if you
             want to develop C language programs which use SQLITE.  This
             is not needed for COBOL or HLASM programs.

- PLICB    - The JCL to compile a PL/I program.

- PLISQLTE - The PL/I %INCLUDE member to define and initialize a number
             of variables to ease the use of SQLITE3A.

- SQLITE3A - LE enabled HLASM subroutine which presents an API to the
             SQLITE3 C subroutines which is designed for use by COBOL or
             PL/I code. It is composite (statically) bound with the C
             object code.
             This code has not been fully tested yet and may contain
             errors.

- SQLITE3O - The object code for SQLITE to be bound into the
             application.  This was compiled on z/OS 1.13, but the C
             compiler options were for compatibility with z/OS 1.11 or
             higher.

- TESTCOB1 - Example Enterprise COBOL program. It is very basic.  It
             uses the SQLITE3A stub to invoke SQLITE3 operations.
             If you look at this, you will realize that I am very
             "wordy" and am definitely not an advanced COBOL programmer.

- TESTCOB2 - Example Enterprise COBOL program. It is very basic.
             It's main example is of how to retrieve a double
             precision floating point number, COMP-2, from an
             sqlite data base, converting it from BFP to HFP format.
             The table is defined like:
             CREATE TABLE xz (int INTEGER, fd DOUBLE);
             This table can be created and loaded from a z/OS UNIX shell
             prompt using the "sqlite3" UNIX command.

             From my testing, it appears that sqlite, unlike most other
             RDMS systems is case sensitive for the names of objects
             such as columns and tables.

- TESTDB   - A pax archive which contains the testdb.sqlite3 UNIX file
             used by the TESTCOB2 program. This needs to be restored
             to a subdirectory (/tmp in the example code). This can be
             done with a UNIX command sequence such as:

             cd /tmp
             pax -rzf "//sql387.cntl(testdb)"

- TSTPLI1  - Example Enterprise PL/I program. It is very basic.
             It is functionally equivalent to TESTCOB1.
             This is not working at present.
             I don't normally program in PL/I because I have never
             worked in a shop which used it.

- UNPAX    - The JCL needed to unwind either the PAXFULL or PAXRUN
             member into a z/OS UNIX subdirectory.

Notes on the SQLITE3A interface program.
----------------------------------------

Notes on how to use SQLITE3A with COBOL.
----------------------------------------
1. One major oddity which can be quite confusing is that the C language
   calling sequence is quite different from the normal COBOL calling
   sequence. This difference is why many of the parameters being passed
   to sqlite3 _must_ be BY VALUE instead of BY REFERENCE. In particular
   things such as integers (COMP-?) and doubles must be passed BY VALUE.
   Character strings are passed BY REFERENCE, but generally require that
   they be terminated with by LOW-VALUES byte. In modern COBOLs, this
   type of string can be initialized using the Z'value' construct.

2. When reading the C API documentation, the main thing to remember is
   that when you see a varible prefixed with an ampersand, you need to
   pass it BY REFERENCE. If you see a variable suffixed with an
   asterisk, this indicates that the variable name in COBOL needs to be
   defined as USAGE POINTER. This is also passed BY VALUE.

3. Another critical point is that when you see a function return an
   "int", which is a 32 bit integer, or a name prefixed by an asterisk,
   you receive these into a COBOL variable by using the phrase RETURNING
   cobol-var-name.  All other types of returned variables, such as
   double floating point, are received by inserting a BY REFERENCE
   phrase as the second parameter in the CALL verb's USING clause.
   Please review TESTCOB2 for an example.

4. Unlike most z/OS languages, sqlite stores floating point numbers in
   IEEE 754 format. On the z, this is called a BFP or Binary Floating
   Point number. After retrieving a BFP number from sqlite, you will
   likely need to call the function "CONVERT-BFP-TO-HFP". Likewise,
   before sending a value to sqlite, you need to convert it to BFP by
   calling the "CONVERT-HFP-TO-BFP" function.  The former is shown in
   the TESTCOB2 example.  My suggestion is to define BFP number in your
   COBOL as COMP-2 variables, perhaps suffixed with -BFP. Use COMP-2 for
   your COBOL floating point number also, not COMP-1. Both of these
   formats use an 8 bytes for storage.


Notes on how to use SQLITE3A with PL/I.
---------------------------------------
No notes at present. Mainly due to my lack of PL/I skills.


Note: This member is in "markdown" compatible format. For more
information on markdown, go to
http://daringfireball.net/projects/markdown/
```

