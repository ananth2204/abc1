
## $$$$DOC.txt
```
 IEFACTRT Jobs statistics after each step.

 IEFUTL   extends wait time based on job type: batch and stc, forever
          and TSO for 2 hours only

 IEFU29   starts dumpsmf automatically at ds switch

 IEFU29A  starts purgsmf like u28; smf data goes to bit bucket

 IEFU83   excp stats at ds close time; see also MPFLST83 and MSG.. exits

 MPFLST83 prevent IEFU83 messages to consoles or log

 MSGFLUSH, MSGJOBLG, MSGNOJLG, MSGNOLOG - useful mpf exits

 PDSSCAN  just what the name says. very fast.

 PDSUPDTE again, just what the name says. very fast; does update in
          place

 SMFDUMP  the elusive dumpsmf program, last distributed by IBM, long ago

 SVCMAP   program to display the SVC table and extended SVC's.  A quick
          dump of the first few bytes of each SVC is included in the
          display.

 SVCMAB   REXX to BROWSE the output of the SVCMAP program
 SVCMAE   REXX to EDIT   the output of the SVCMAP program
 SVCMAR   REXX to REVIEW the output of the SVCMAP program
 SVCMAV   REXX to VIEW   the output of the SVCMAP program

 TCPU83, TCBU84 U83 and U84 exits for ftp statistics. Crude but they
          work

 Remainder contains necessary macros, related procs, etc.

 Collected or developed by:
 Rick Fochtman

 Support:   Sam Golob

   email:   sbgolob@cbttape.org    or
            sbgolob@attglobal.net

```

