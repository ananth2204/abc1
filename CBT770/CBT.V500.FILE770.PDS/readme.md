
## $DOCTXT.txt
```

zCBT Automation Tools
) 2006 - Deru Sudibyo


What is zCBT?

zCBT is a miniature of zJOS.  zCBT is the simplest solution for
z/OS system event management at no cost.  You don't need special
skill to automate your system using zCBT. Once zCBT is properly
setup, you will very able to manage your system events using very
simple rexx scripting.  All you need is rexx skill.

zCBT is a combined of subsystem functions and resource manager
which run on z/OS as a subsystem, instead of an address space.
zCBT subsystem supports 5 types of events:

Messages (MSG) events for both WTO and WTOR. Message is trapped
before sent to console, hence you can optionally suppress it. By
trapping substring of message text, you can do several actions.
For WTOR message, you can reply it.

Command (CMD) events.  Command is trapped before sent console,
hence you can optionally suppress it.  This is an opportunity for
you to have your own console commands.  By preparing rexx routine
to trap certain command verbs (regardless they are valid
commands) and their associated actions, you will have your own
commands.

End-of-jobstep (EOS) events for both jobs and STCs.  EOS event is
trapped at almost the time of its occurrence and reporting
condition codes. If you are a smart programmer, by using zCBT you
can develop your own scheduler in rexx language.

End-of-job (EOJ) events for jobs and STCs.  EOJ event is
simulated from all related EOS previously occurred.  Hence, there
is a short time delay (less than 1 sec).

Time-of-day (TOD) events.  TOD is very common event people can
trap.  Internally it just STIMER or STIMERM macro which doesn't
need authorization as privileged routine.  Since rexx able to
obtain date and time, zCBT only support TOD time event for both
clock and interval time.

The way zCBT subsystem supports system automation is by providing
some rexx functions.  Request regarding which event you want to
trap is sent to zCBT as function arguments.  Trapped event
information is then returned to you as result value of the issued
function.  Although rexx is executed synchronously, you can
however, trap multiple events within a single rexx program.
CBTIVP member of REXXLIB dataset gives you example how to handle
multiple events.

Your rexx program can run on TSO TMP session, TSO batch or
non-TSO job.  To run CBTIVP, you can start JCBTEST1 member of
JCLLIB as either normal STC or under MSTR subsystem.   If you
need zCBT to automate your system startup, you must run your rexx
program as STC under MSTR subsystem.


zCBT Supported Rexx Functions

You can easily handle 5 types of events, message, command,
end-of-jobstep (EOS), end-of-job (EOJ) and time-of-day (TOD) by
using ordinary rexx scripting or programming. To do so, zCBT
provides 7 rexx functions, these are:

cbcmd()
cbevent()
cbserver()
cbset()
cbwait()
cbwto()
cbwtor()


zCBT Installation

zCBT package is in TSO XMIT format and reside in ZIP file.  To
install it, do the following steps:

Extract zCBT.FREEWARE.XMI and CBTSETUP.REX files from ZIP.

Log in to your TSO user.  Your TSO user must have system support
or administration authorization.

Upload zCBT.FREEWARE.XMI file onto your z/OS.  Transfer must be
in BINARY mode.  Target must be a sequential dataset with FB 80
record format.  Use any name to meet your naming standard.

Upload CBTSETUP.REX file onto your z/OS.    Transfer must be in
ASCII mode.  Target must be a member of partitioned dataset (PDS
or PDSE) which is concatenated in your existing SYSEXEC or
SYSPROC file of TSO user you are currently logging on.  Targeted
member name must be CBTSETUP.

Select TSO command shell panel (option 6) or menu bar choice 4,
then issue the following command:

  CBTSETUP DSN=xmi_file_name PREF=hlq
  Where:
  xmi_file_name is uploaded zCBT package dataset name
  hlq is high level qualifier you prefer for all zCBT datasets.

Upon completion of CBTSETUP, 6 zCBT datasets are extracted from the package:
  hlq.CBT.LOADLIB .
  hlq.CBT.REXXLIB
  hlq.CBT.SAMPLIB
  hlq.CBT.SRCLIB
  hlq.CBT.MACLIB
  hlq.CBT.JCLLIB

Register hlq.CBT.LOADLIB into APF and apply it.

Read @README member of hlq.CBT.SAMPLIB carefully.  Follow the
instructions and recommendation in @README member to customize
ZCBT, CBTIPL, IEALPA00, IEFSSN00, JCBTEST1 and JCBTEST2 members.

Copy customized ZCBT, CBTIPL and JCBTEST1 members of SAMPLIB
dataset into your current PROCLIB.

Copy or merge customized IEALPA00 and IEFSSN00 members of SAMPLIB
into your current PARMLIB.

Start ZCBT under master subsystem, e.g. START ZCBT,SUB=MSTR.  It
will setup a subsystem named CBT.  If you prefer to use different
name, start with the following command:

START ZCBT,SUB=MSTR,SSN=subsysname

Note that, if IEALPA00 and IEFSSN00 samples are implemented, you
don't need to start ZCBT in next IPL.


zCBT Verification

Once ZCBT is brought up, zCBT subsystem is active and ready for
automation or EMS.  The STC ZCBT itself immediately down when
setup is complete. To make sure zCBT is working properly, do the
following verification steps: Assume you have customized JCBTEST1
and JCBTEST2 members of SAMPLIB dataset, and JCBTEST1 is ready in
PROCLIB.  Start JCBTEST1 either under primary subsystem (START
JCBTEST1) or under master subsystem (START JCBTEST1,SUB=MSTR).
Issue command CBT LIST on console to see event definition
currently requested by JCBTEST1.  Submit customized JCBTEST2.
See the log or console.

JCBTEST1 issues cbset() function to define events and request
zCBT subsystem to collect information of these defined event each
time they occur.   Then issue cbevent() function without argument
to wait and receive information regarding previously requested
events.   cbevent() is iterated until all requested events are
received.    It only issue WTO message using cbwto() function as
action against each event occurrence.

JCBTEST2 is a 2-step job to generate event requested by JCBTEST1.
Step 1 is to generate MSG and EOS events.  Step 2 is to generate
CMD and EOS events.  When the job terminate, EOJ event is
generated.


zCBT Usage and License

By learning rexx program CBTIVP (called by job JCBTEST1), CBTIVP1
and CBTIVP2 (called by job JCBTEST2), and CBTIPL (called by job
CBTIPL) in REXXLIB dataset, you would understand how to use zCBT.
Nothing special and does not need additional skill.   As a
freeware, you can use zCBT any time at no cost.   However, as a
freeware product, all the common term of use of freeware are
applicable to zCBT.   Although you may use it in your production
system, you may not use its parts or components in any commercial
activities.

zCBT consists of 2 program modules, CBTREX and CBTEMS.  CBTREX
module is a rexx functions package module.  To give you a chance
to add some more functions, CBTREX and all associated macros
source codes are provided.   If you are assembler or C
programmer, you can easily implement your innovation by enhancing
the CBTREX module.

CBTEMS is a core of zCBT.  The source code of CBTEMS is not
provided.  This to avoid abusing or violence of the usage of
zCBT, since it can be enhanced to become complete EMS solution as
normally provided by ISVs.

zCBT uses ESR SVC code 212.  If you have constraint with this
code on your environment and expect to use other code, please
send request to the author.   A complete package with different
ESR code will be sent to you.


 Automating Your System using zCBT

As a toy, zCBT is quite capable to manage system events to
automate your z/OS system.  You can implement system automation
only with a single rexx program.  By combining cbset() and
cbevent() functions smartly, your rexx program capable to capture
and handle any occurrence of expected messages, commands,
end-of-step (EOS) and end-of-job (EOJ) events.  Both cbset() and
cbevent() functions are the main design of zCBT subsystem.   The
following example illustrates the logic skeleton of how rexx
program can manage system event smartly based on zCBT
architecture.

/* -------------------------------------- */
/* Request zCBT for the following events: */
/* -------------------------------------- */
set1   = zjset('MSG','msg_string')
set2   = zjset('CMD','cmd_string','SUPPRESS')
set3   = zjset('EOS','jobname.stepname')
set4   = zjset('EOJ','jobname')

/* -------------------------------------- */
/* Wait notification from zCBT if any one */
/* of the above events occurs.            */
/* -------------------------------------- */
Do forever
   event  = zjevent()
   evtype = strip(word(event,1))
   Select
      When evtype = 'MSG' then call MSG_handler
      When evtype = 'CMD' then call CMD_handler
      When evtype = 'EOS' then call EOS_handler
      When evtype = 'EOJ' then call EOJ_handler
      Otherwise NOP
   End
End
Exit

MSG_handler:
/* routine to handle message events */
Return

CMD_handler:
/* routine to handle command events */
Return

EOS_handler:
/* routine to handle end-of-step events */
Return

EOJ_handler:
/* routine to handle end-of-job events */
Return

Other function such as cbstate(), cbcmd() and cbwait() in
addition, will give you chance to enhance your rexx program
performing EMS functions smarter.   You can detect whether a
workload or job is up by using cbstate() function.   To issue a
console command, you can use cbcmd() function.  Cbwait() function
is to enter to wait state based on either TOD clock or interval.

Unless really required, you should not use cbwait() function
within combined cbset() and cbevent() functions mechanism.  Doing
so might impact to the timing precision of events occurrences.
It can even worst when cbwait() is issued in the wrong place.


zCBT Functions Reference

cbcmd()

cbcmd() is a rexx function to pass command text to console for
execution.  As it is a privileged function which normally
forbidden in rexx environment, it needs authorization from zCBT.
Hence it can only be used when zCBT subsystem is active.
Nevertheless, the use of cbcmd() also depend on your local
security setting.

Syntax:

var = cbcmd('command_text')

or

var = cbcmd(cmdvar)

Where:
'command_text' is text of command string, which must be enclosed
with either single or double quote.

cmdvar is variable name to contain text of command string.

var is variable name to contain function result.  Possible results are:

  'ISSUED' - command was issued
  'UNAUTHORIZED nnn' - command was not granted
  nnn is zCBT authorization exception code

Example:

To issue MVS command D PROG,APF, you can write it in rexx as follow:

x = cbcmd('D PROG,APF')

Alternatively,   you can use variable as follow:

cmd = "D PROG,APF"
x = cbcmd(cmd)
if x = 'ISSUED' then ...
else ...


cbevent()

cbevent() is a rexx function to request zCBT subsystem for
notification when a certain event as specified in its arguments
occurs, or when any event previously requested by using cbset()
function occurs, and optionally perform an immediate simple
action.  When issued, cbevent() function may entering wait state
condition to listen notification from zCBT subsystem regarding
the occurrence of previously selected event.  You must realize
that it will be sleeping forever and only wake up when the event
occurs.

When issued with arguments, cbevent() only listens an event as
specified in the arguments and perform a simple action if one
specified in argument.  Function is immediately woken up and
terminated when the event occurs.  Actually when notified by zCBT
subsystem that the expected event occurs.  To wait next similar
event, you must iterate it.  By using cbevent() function with
arguments, your rexx program can only listen a single event at a
time.

When issued without argument, cbevent() listens all previously
requested events by using cbset() function.  Hence, cbevent()
without argument must be preceded by cbset() function.  This
gives you chance to your rexx program to listen multiple events
at a time.  When one of expected events occurs, cbevent() is
immediately woken up and terminated.  To continue wait for next
event, either similar or other event, you must iterate it.   As
cbset() function does not support immediate action, no action is
perform when cbevent() function without argument is woken up.
All action must be handle in your rexx program by using cbcmd()
function.

As it is a privileged function, it needs authorization from zCBT
subsystem.  Hence it can only be used when zCBT subsystem is
active.  Besides, it actively communicates with zCBT subsystem to
send request to and receive event information from zCBT
subsystem.  Nevertheless, the use of cbevent() also depend on
your local security setting.

Syntax:

var = cbevent('evtype','evtext',Ý'SUPPRESS'¨,'action')

or

var = cbevent(evtypevar,evtextvar,optvar,actionvar)

or

var = cbevent()    /* without argument */

Where:

Arguments:
  'evtype' (expression) or evtypevar (variable) is type of event
  in 3-character abbreviation, which MSG for message event, CMD
  for command event, EOJ for end-of-job event or EOS for
  end-of-step event.

  'evtext' (expression) or evtextvar (variable) is text or string
  represents part of the source of event information you want to
  capture or trap.

  'SUPPRESS' (expression) or optvar (variable) is suppression
  option for MSG or CMD event only.  If optvar (variable) is
  used, it must contain 'SUPPRESS' or nulls or blanks.

  SUPPRESS for MSG event causes message to be suppressed.  Hence
  messages no longer eligible for subsequent trapping for either
  cbevent() invocations or EMS table entries.

  SUPPRESS for CMD event causes command to be suppressed and not
  executed.  Hence command no longer eligible for subsequent
  trapping for either cbevent() invocations or EMS table entries.

  'action' (expression) or actionvar (variable) is text to
  express a simple action you want to perform.  There are 3
  possible simple actions:

  'MSG=messagetext'
  'CMD=commandtext'
  'REPLY=replytext'

var is variable name to contain function result, which depends on
event type:

  For MSG event from WTO message, var contains:
  'MSG message text'
  For MSG event from WTOR message, var contains:
  'MSG (REPLYID=nn) message text'
  For CMD event, var contains:
  'CMD command text'
  For EOJ event, var contains:
  'EOJ JOB=jobname SCC=nnn MAXCC=nnn '
  For EOS event, var contains:
  'EOS JOB=jobname STEP=stepname SCC=nnn UCC=nnn'
  If one or more arguments were invalid or missing, var contains:
  'ERROR_ARGUMENT'
  If command was not granted, var contains:
  'UNAUTHORIZED nnn'
  nnn is zCBT authorization exception code

Example:

To capture command D APF and change it to D PROG,APF, you can
write it in rexx as follow:

X = cbevent('CMD','D APF','SUPPRESS',
            'CMD=d prog,apf')

Alternatively,   you can use variable as follows:

cmd = "D APF"
xcmd = "CMD=D PROG,APF"
x = cbevent('cmd',cmd,'SUPPRESS',xcmd)
if x = cmd then ...

With option SUPPRESS, D APF command will appear as a valid
command and result as if you issue D PROG,APF command.

Notes:

When a CMD or MSG event occurs and more than one cbevent() and/or
cbset() functions are issued at the same time (by several users,
each cbevent() is notified in sequent.  Therefore, you must care
of suppression option of cbevent() function.  If event is
suppressed, event may no longer eligible for either subsequent
cbevent().

When more than one cbevent() functions are active at the same
time to capture WTOR message, only one user can issue reply
command.  Other reply will result no outstanding reply.

Once cbevent() got missed, it will remain stay in wait state
until similar event occurs.  Unless very urgent situation, you
should not cancel it.  Doing so, causes an orphaned EVB control
block and will remain in ECSA until next IPL.

cbevent() function can be issued without argument.  This only
valid when you have requested events collection by issuing
cbset() function.  Otherwise, cbevent() will result
unpredictable.


cbset()

cbset() is a rexx function to request zCBT subsystem for
notification when a certain event as specified in its arguments
occurs. Unlike cbevent(), once request is confirmed by zCBT
subsystem, cbset() is not entering to wait state until notified
by zCBT subsystem.  Rather, cbset() immediately finish and return
to your rexx program when request is confirmed. You responsible
to handle the notification from zCBT subsystem by issuing
cbevent() function without argument.

Such mechanism gives chance to your rexx program to handle
multiple events or multiple types of events at a time.  You may
issue several cbset() for all expected events, then followed by
iterated cbevent() without argument as in the following example:

req1 = cbset('MSG','$HASP492')
req2 = cbset('MSG','IST020I')
req3 = cbset('CMD','P','SUPPRESS')
Do forever
   event = cbevent()
   evtype = strip(word(event,1))
   Select
      When evtype = 'MSG' then,
         Do
            msgid = strip(word(event,2))
            Select
               When msgid = '$HASP492' then,
                  Do
                     action1 = cbcmd('START VTAM')
                     action2 = cbcmd('START SDSF')
                  End
               When msgid = 'IST020I' then,
                  Do
                     action1 = cbcmd('START TSO')
                     action2 = cbcmd('START CICSPROD')
                  End
               Otherwise NOP
             End
         End
      When evtype = 'CMD' then,
         Do
            cmdverb = strip(word(event,2))
            cmdtarg = strip(word(event,3))
            If cmdverb = 'P' then,
               If cmdtarg = 'VTAM' then,
                  action3 = cbcmd('Z NET,QUICK')
               Else,
                  action3 = cbcmd('STOP ' || cmdtarg)
         End
      Otherwise NOP
End

The above example shows you how rexx program can handle $HASP392
and IST020I messages and STOP command.   When $HASP392 message
occurs, this indicates JES2 initialization complete, then start
VTAM and SDSF.   When IST020I message occurs, this indicates VTAM
initialization complete, then start TSO and CICSPROD.   Such idea
is very common in EMS implementation.

One thing you should keep in mind is the way this example handle
P command.  P is a short form of STOP command verb.  When P
command issuance occurs, suppress it to avoid execution.  Then,
check the command argument, which is a name of workload or job to
be brought down.   If the targeted job is VTAM, then issue Z
NET,QUICK.   Else, issue STOP for the same target.  This will
affect as if P command applicable for VTAM, which is actually
not.   Although STOP and P are actually executed by the same
processor, STOP verb won't be trapped since ZCBT subsystem only
evaluate the command text.

Combined cbset() and cbevent() functions is the main design idea
of zCBT subsystem.  Both functions gives you chance to automate
actions against several MSG, CMD, EOS and EOJ events in a single
rexx program which fully follows your own idea.

As it is a privileged function, it needs authorization from zCBT.
Nevertheless, the use of cbset() also depend on your local
security setting.

Syntax:

var = cbset('evtype','evtext',Ý'SUPPRESS'¨)

or

var = cbset(evtypevar,evtextvar,optvar)

Where:

Arguments:
  'evtype' (expression) or evtypevar (variable) is type of event
  in 3-character abbreviation, which MSG for message event, CMD
  for command event, EOJ for end-of-job event or EOS for
  end-of-step event.

  'evtext' (expression) or evtextvar (variable) is text or string
  represents part of the source of event information you want to
  capture or trap.

  'SUPPRESS' (expression) or optvar (variable) is suppression
  option for MSG or CMD event only.  If optvar (variable) is
  used, it must contain 'SUPPRESS' or nulls or blanks.

  SUPPRESS for MSG event causes message to be suppressed.  Hence
  messages no longer eligible for subsequent trapping.

  SUPPRESS for CMD event causes command to be suppressed and not
  executed.  Hence command no longer eligible for subsequent
  trapping.

var is variable name to contain function result:
  If request was confirmed, var contains:
  'SET'
  If one or more arguments were invalid or missing, var contains:
  'ERROR_ARGUMENT'
  If authorization was not granted, var contains:
  'UNAUTHORIZED nnn'
  nnn is zJOS authorization exception code

Example:

See the above example.

Note:

Logical path length between cbset() and cbevent() functions
issuance could be vary, depend on your rexx program logic.  If
the path length is quite significant, event might occur prior to
cbevent() function issuance.  In such case, cbevent() will
immediately return to your rexx program, since event information
has already given in your program area.  There is no indicator
telling you whether event occurs earlier than cbevent() function
issuance.  You, therefore, should care of path length if time
precision is required.


cbstate()

cbstate() is a rexx function to obtain state information of any
local workload.  As it is a privileged function, it needs
authorization from zCBT.  Nevertheless, the use of cbstate() also
depend on your local security setting.

Syntax:

var = cbstate('workload_name')

or

var = cbstate(namevar)

Where:

'workload_name' is text of name of workload (jobname), which must
be enclosed with either single or double quote.

namevar is variable name to contain text of workload name
(jobname).

var is variable name to contain function result.
  If workload up, var variable will contain 5 words of:
  'UP type ASCB=xxxxxxxx ASID=xxxx JOBID=xxxxxxxx'
  Type is either STC, JOB or TSU
  If workload down, var contains:
  'DOWN'
  If argument invalid (no argument or argument more than 8-byte)
  'ERROR_ARGUMENT'
  If authorization not granted by zCBT
  'UNAUTHORIZED nnn'
  nnn is zCBT authorization exception code

Example:

To obtain state information of VTAM, you can write in rexx:

x = cbstate('VTAM')
vtamstate = word(x,1)

Alternatively,   you can use variable as follow:

job = "VTAM"
x = cbstate(job)
vtamstate = word(x,1)

Upon completion, if VTAM is up, x may contains:

"UP STC ASCB=00F8A000 ASID=0021 JOBID=STC09703"

You can get all information by parsing the result (x) as follows:

If vtamstate = 'UP' then,
   Parse var x,
      'UP' jobtype 'ASCB=' ascb 'ASID=' asid,
      'JOBID=' jobid


cbwait()

cbwait() is a rexx function to enter to wait state based on TOD
clock or interval. Entering wait state is not a privileged
process, hence cbwait() function need not authorization. Hence,
you can use cbwait() regardless zCBT subsystem is active.  While
waiting, your rexx program is suspended until time is expired.

Syntax:

var = cbwait('timeval')

or

var = cbwait(timevar)

Where:

'timeval' is time value, which must be enclosed with either
single or double quote.   Time value must be in the following
format:

  TOD value - wait until specified TOD.  Format is:
  HH:MM:SS
  Interval value - wait for specified interval.  Formats are:
  +HH:MM:SS
  +MM:SS
  +SS

timevar is variable name to contain time value.

var is variable name to contain function result.
  If wait state was entered:
  'EXPIRED FOR nnnnnn SECS'
  If wait state was not entered (for example: already late):
  'EXPIRED FOR -nnnnnn SECS'
  If CPU clock was error:
  'ERROR_CLOCK RC=nnnn'
  If argument invalid (no argument or argument more than 9-byte)
  'ERROR_ARGUMENT'

Example:

To wait until 23:30:00:

x = cbwait('23:30:00')

To wait for 5 minutes 45 seconds and using variable:

interval = '+05:45'
x = cbwait(interval)



cbwto()

cbwto() is a rexx function to issue WTO message to console.
Issuing WTO is not a privileged process, hence function need not
authorization, and internally is nothing to do with zCBT
subsystem.  Hence, you can use cbwto() regardless zCBT subsystem
is active.

Syntax:

var = cbwto('message_text')

or

var = cbwto(msgvar)

Where:

'message_text' is a text of message to be issued, which must be
enclosed with either single or double quote.

msgvar is variable name to contain message text.

var is variable name to contain function result.
  If WTO was successfully issued:
  'ISSUED'
  If WTO was unsuccessful:
  'ABORTED'
  If argument invalid (no argument or argument more than 126-byte
    length)
  'ERROR_ARGUMENT'


Example:

To issue "Good morning!" to system console:

x = cbwto(Good morning!')

cbwtor()

cbwtor() is a rexx function to issue WTOR message to console.
Issuing WTOR is not a privileged process, hence function need not
authorization.   Hence, you can use cbwto() regardless zCBT
subsystem is active.

As it is WTOR, reply is required to finish the function.  While
waiting for reply, your rexx program is suspended until your
message is replied.   Reply text can be any 1 to 54 characters in
length.

Syntax:

var = cbwtor('message_text')

or

var = cbwtor(msgvar)

Where:

'message_text' is a text of message to be issued, which must be
enclosed with either single or double quote.

msgvar is variable name to contain message text.

var is variable name to contain function result.
  If WTOR was successfully issued:
  'REPLY=replytext'
  If WTOR was unsuccessful:
  'ABORTED RC=nnn'
  If argument invalid (no argument or argument more than 126-byte
    length)
  'ERROR_ARGUMENT'

Example:

To issue "Good morning!" to system console and require reply:

x = cbwtor(Good morning!')
/* check reply text */
If substr(x,1,6) = "REPLY=" then,
   Parse var x "REPLY=" reply


zCBT Commands Reference

zCBT provides 2 subsystem commands to support you managing system
events better.   These are LIST and MSG.   As these are subsystem
commands, you can only use them when zCBT subsystem is active.
Otherwise, command will not be recognized and z/OS will reject
them as invalid command.


LIST Command

LIST command is to display list of listened events which either
requested by issuing cbevent() or cbset() functions.   This gives
you chance to monitor how many outstanding events listeners.

Syntax

CBT LIST

MSG Command

MSG command is to issue WTO message interactively.   This gives
you chance to simulate a certain message to test your rexx
program.

Syntax

CBT MSG message_text




 The Author needs Your Help

The author of zCBT is the author of zJOS.  zJOS is a proven
integrated EMS and workload scheduling.   Although zJOS has
already marketed locally in Indonesia and currently is running on
production systems, it has no future in Indonesia.   The only way
to earn better future is if it is acquired by well known ISV.  It
should be quite interesting product since not all ISV provide
such solution.  Besides, the automation solution normally is
quite expensive.

The author needs help to market it to well known ISV and offers
50-50 sharing.  If you capable to do it up to close the deal at
all cost, you will earn 50%.  This rule is applicable to
everybody.   Hence, if you are the buyer and directly deal with
the author, fairly you only need to pay 50% of the price.  Should
you are interested to do it, kindly notify the author.

zJOS can handle total automation of multiple z/OS systems
integrally.  However, zJOS agent only supports z/OS and late
OS/390 platforms.  To support other platform, the only effort
required is developing agent for the targeted platform, and zJOS
becomes one of enterprise automation solution.

The standard zJOS agent communication protocol is provided.
Agent is simple, consists of 2 major processes, IP socket client
and events listener. Unfortunately, author doesn't have enough
skill for internal of non-z/OS platforms.  Author offers
ownership sharing to anybody who interested to develop agent for
open system and other non-z/OS platforms proportionally.  Should
you are the guy, kindly let author know.


Contact the Author

Emails: @bogor.net, @gmail.com or @SSH
Company address and phone: see www.sumbersolusindo.co.id.
Mobile:  +62-812-110-6577



```

