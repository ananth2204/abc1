```
//***FILE 864 is from John McKown and contains UNIX shell commands  *   FILE 864
//*           for z/OS which he wrote, to run under z/OS UNIX.      *   FILE 864
//*           The commands are as described below, and are meant    *   FILE 864
//*           to be compiled (using make) under z/OS UNIX only.     *   FILE 864
//*                                                                 *   FILE 864
//*       This package is in alpha status, currently.  Folks        *   FILE 864
//*       are encouraged to try it out and write to the author      *   FILE 864
//*       about fixes and improvement suggestions.                  *   FILE 864
//*                                                                 *   FILE 864
//*       email:  "McKown, John" <john.archie.mckown@GMAIL.com>     *   FILE 864
//*                                                                 *   FILE 864
//*    Below is a description of the contents and idea of this      *   FILE 864
//*    file.  See the pds member called $$README for further        *   FILE 864
//*    detail.                                                      *   FILE 864
//*                                                                 *   FILE 864
//*    This is an alpha version of my UNIX tools. Many of the       *   FILE 864
//*    files are simply skeletons at present. Only a few work       *   FILE 864
//*    completely. The man pages (documentation) are                *   FILE 864
//*    definitely a work in progress.                               *   FILE 864
//*                                                                 *   FILE 864
//*    Note that the assembler source is not formatted properly     *   FILE 864
//*    to be read using only ASMA90.  It requires that you have     *   FILE 864
//*    FLOWASM installed in either a library in the link list,      *   FILE 864
//*    or in a library assigned to the UNIX STEPLIB environment     *   FILE 864
//*    variable.  The system is set up to do compiles in a UNIX     *   FILE 864
//*    shell by using the make command, which references the        *   FILE 864
//*    makefile file.                                               *   FILE 864
//*                                                                 *   FILE 864
//*    FLOWASM is on CBT Tape File 724.                             *   FILE 864
//*                                                                 *   FILE 864
//*    You start by changing the UNPAX job to point to an           *   FILE 864
//*    existent UNIX subdirectory in which a new subdirectory       *   FILE 864
//*    called utilities-1 will be created. The files in the pax     *   FILE 864
//*    archive, member UTILPAXZ, will be extracted into this        *   FILE 864
//*    directory.                                                   *   FILE 864
//*                                                                 *   FILE 864
//*    Once you have extracted the files, you may run the job       *   FILE 864
//*    in the member MAKEALL to compile and link all the            *   FILE 864
//*    programs. You need to change this job to point to the        *   FILE 864
//*    same subdirectory as in the UNPAX job.  The output will      *   FILE 864
//*    be placed in this same subdirectory.  This is not really     *   FILE 864
//*    necessary because the executable programs are already in     *   FILE 864
//*    the subdirectory.                                            *   FILE 864
//*                                                                 *   FILE 864
//*    There are many extraneous files in this subdirectory         *   FILE 864
//*    because I haven't cleaned it up yet. The ones which          *   FILE 864
//*    actually work are:                                           *   FILE 864
//*                                                                 *   FILE 864
//*    ams - Invokes the IDCAMS batch program, redirecting          *   FILE 864
//*          SYSIN from the UNIX "stdin" and the SYSPRINT to        *   FILE 864
//*          "stdout". The source is in ams.s.                      *   FILE 864
//*                                                                 *   FILE 864
//*    isgquery.o - is a subroutine (object code) used by lsenq     *   FILE 864
//*          which does the ISGQUERY macro. The source is in        *   FILE 864
//*          isgquery.s.                                            *   FILE 864
//*                                                                 *   FILE 864
//*    lsdasd - Lists the space on all on-line DASD volumes. I      *   FILE 864
//*             plan, some day, to include the storage group        *   FILE 864
//*             name for SMS managed volumes in the output, and     *   FILE 864
//*             to allow specification of volume series, with       *   FILE 864
//*             "wildcarding" to subset the list. The source is     *   FILE 864
//*             in lsdasd.s.                                        *   FILE 864
//*                                                                 *   FILE 864
//*    lsenq - Lists enqueue information. You can specify a         *   FILE 864
//*            resource name, with wildcarding. You may also        *   FILE 864
//*            specify an queue name. If a queue name is not        *   FILE 864
//*            specified, it defaults to SYSDSN. The queue name     *   FILE 864
//*            can also be wild carded. Also, if (and only if)      *   FILE 864
//*            the queue name is defaulted, the resource name       *   FILE 864
//*            is assumed to be a dataset name and is upper         *   FILE 864
//*            cased.  Syntax: lsenq ÝÝqname¨ Ýrname¨¨.             *   FILE 864
//*                                                                 *   FILE 864
//*    mkjcl - is a shell script, not a compiled program. It        *   FILE 864
//*            reads a "template" file, which is specified on       *   FILE 864
//*            the command line, and modifies it by replacing       *   FILE 864
//*            embedded UNIX-style variables with their values.     *   FILE 864
//*            It writes its output to "stdout" so that it may      *   FILE 864
//*            be piped to a subsequent command, such as            *   FILE 864
//*            "submit". The variables are passed to the            *   FILE 864
//*            command as shell environment variables, via the      *   FILE 864
//*            export command, or on the command line itself.       *   FILE 864
//*            This is the normal way that named variables are      *   FILE 864
//*            done in UNIX.  An example of a template jcl is       *   FILE 864
//*            supplied in the "iefbr14.jcl" file.                  *   FILE 864
//*                                                                 *   FILE 864
//*    All files which have file name of SKELETON are just          *   FILE 864
//*    that, my SKELETON files which I use as the basis for the     *   FILE 864
//*    actual program code. The suffix specifies the language.      *   FILE 864
//*    ".1" for man source files. ".cat1" for "compiled" man        *   FILE 864
//*    source files. ".a" for "library archive" files (which        *   FILE 864
//*    contain object code for subroutines which are                *   FILE 864
//*    "statically linked").  ".awk" for awk source files. ".o"     *   FILE 864
//*    for compiled object files. ".pl" for Perl source files.      *   FILE 864
//*    ".rexx" for rexx programs. ".sh" for shell script files.     *   FILE 864
//*    ".s" for HLASM source files.                                 *   FILE 864
//*                                                                 *   FILE 864
//*    Some of the other ".s" files are for things I am still       *   FILE 864
//*    planning for.                                                *   FILE 864
//*                                                                 *   FILE 864

```
