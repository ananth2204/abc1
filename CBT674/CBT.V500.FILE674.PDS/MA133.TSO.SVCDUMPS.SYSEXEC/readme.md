
## $DOC.txt
```
/*********************************************************************/
/* Welcome to SVCDumps                                               */
/*********************************************************************/
THESE UTILITIES ARE PROVIDED AS IS WITH NO WARRANTIES OR GUARANTEES OF
ANY KIND WHATSOEVER. USE AT YOUR OWN RISK!

you may contact me at: mvs@robinandmariette.com
you may recieve udpates at: http://www.robinandmariette.com/mvs/rexx/

I tried a couple of freeware svcdump managers, and found they didn't
meet my needs. They were a bit dated, being written in clist or
assembler. I decided to write one in rexx from scratch. Although the
external interface may look similar to others you've seen, the internal
code has been written from scratch and is completely original.

This code will handle SVC dumps in either SYS1.DUMPxx format or using
the dynamic dump method by using the 'DD NAME=' operator command. The
only requirement with the dynamic method is that you specify a date
and time in the dump dataset qualifiers so that the dump management
can be properly executed.

You can park your dumps on sms or non-sms packs. If you use non-sms,
it is better if you specify a pool of candidate packs (see the $install
member for details) and install MXI off the cbttape. Using MXI will
enable the dump manager to pick the pack with the most freespace,
similar to what sms would do. If you don't want to use sms or the
non-sms pooling, you can specify just one non-sms pack for dump usage,
and it is then up to you to ensure enough space is available.

A flat file log is maintained of the dumps, and any processing of the
log, via batch or online, occurs via an ISPF private table shell. When
the batch or interactive processing is complete, only the updated
records are copied back into the log, and even then only if you have the
latest timestamp than what is in the log. The log is thus properly
maintained in a shared environment. I find this method easier to manage
and code than using a shared ISPF table approach.

To install, follow the steps in the $install member.
```

