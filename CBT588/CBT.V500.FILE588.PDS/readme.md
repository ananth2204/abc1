
## $DOC.txt
```
This dataset contains a simple REXX application SYSCNTL
that helps automate routine operations like system SHUTDOWN
or check if critical tasks are running and responding.
This application can be run as a batch job or started task.
See $SYSCNTL for atomated shutdown program documentation.

A set of useful REXX functions is included to work with data sets
outside (and inside) TSO environment (e.g. under IRXJCL),
that saves 10-20% resourses like CPU and virt memory:
See $IRXFLOC for REXX functions included to IRXFLOC.

The IRX@MGCR authorised program is included that could be called
either from REXX or JCL to reply an outstanding console request.

Also included is a set of rexx execs (PW, etc) I use to run
rexx from batch job stream (//TEMPL DD *).
You can see examples in step GO for Assemler source members
of some rexx functions. That step executes PW to run some
inline rexx that tests the function immediately after
it was assembled and linked.

The contents of this PDS are:

$CHANGES update history log
$DOC     what you are reading
$INSTALL Installation guide
$RXFLOC  User Guide for rexx functions
$SYSCNTL User Guide for SYSCNTL application
ASM      The asm source lib in TSO Transmit (IDTF) format
EXEC     The rexx exec lib  in TSO Transmit (IDTF) format
JCL      The jcl proclib    in TSO Transmit (IDTF) format
LOAD     The load lib       in TSO Transmit (IDTF) format
MACLIB   The ASM maclib     in TSO Transmit (IDTF) format
RECEIVE  A simple exec to receive the members
         into partitioned datasets

To execute the RECEIVE member issue
   "TSO EXEC 'hlq.pds-dsname(RECEIVE)' EXEC"
See $INSTALL member for details.

Each program has self-documenting comments included to source.

Comments, suggestions, and complaints should be directed
to the author: see @FILE588 for address.
```

