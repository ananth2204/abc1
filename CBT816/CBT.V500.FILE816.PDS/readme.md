
## @FILE816.txt
```
//***FILE 816 is from Sam Golob and contains an APF-authorized      *   FILE 816
//*           TSO command to quickly and instantly change the       *   FILE 816
//*           default number of Global Notices that an ACCOUNT      *   FILE 816
//*           and SYNC combination will create, when it formats     *   FILE 816
//*           a SYS1.BRODCAST dataset (or any active Broadcast      *   FILE 816
//*           Dataset).                                             *   FILE 816
//*                                                                 *   FILE 816
//*           email:  sbgolob@cbttape.org     or                    *   FILE 816
//*                   sbgolob@attglobal.net                         *   FILE 816
//*                                                                 *   FILE 816
//*           IBM officially makes this number very difficult       *   FILE 816
//*           to change.  You have to zap the hex number into       *   FILE 816
//*           csect IKJEBLMT of module IKJEFXSR and the change      *   FILE 816
//*           will not take effect until the next IPL.  Very        *   FILE 816
//*           silly and unlike IBM....  This must have had a        *   FILE 816
//*           reason when it was designed, but it doesn't seem      *   FILE 816
//*           to make much sense nowadays, with IPLs so few         *   FILE 816
//*           and far between.                                      *   FILE 816
//*                                                                 *   FILE 816
//*           Fortunately, there is a solution.  The actual         *   FILE 816
//*           number that SYNC looks at, is located squarely        *   FILE 816
//*           in the CVT itself.  It isn't even chained off it!     *   FILE 816
//*           The number is a fullword at location CVT + X'5A8'.    *   FILE 816
//*           And loading this up initially, is the reason for      *   FILE 816
//*           the necessity of the IPL.                             *   FILE 816
//*                                                                 *   FILE 816
//*           IBM could have done better (and it still might,       *   FILE 816
//*           if you submit a requirement for a console command     *   FILE 816
//*           to change the default, through SHARE).  However,      *   FILE 816
//*           we are not waiting for IBM.  Here is a TSO command    *   FILE 816
//*           (that of course has to be APF-authorized), which      *   FILE 816
//*           will change the number instantly in the CVT, by       *   FILE 816
//*           simply plugging in a new number.  It works.  Just     *   FILE 816
//*           say BDMNNOTC 500, and an ACCOUNT + SYNC will produce  *   FILE 816
//*           a Broadcast Dataset that has 500 Global Notices       *   FILE 816
//*           messages.  Set a different number, and you get        *   FILE 816
//*           that number of Global Notices produced by the         *   FILE 816
//*           ACCOUNT + SYNC.  In my experience, you can even       *   FILE 816
//*           go over 1000 (IBM's professed limit).  I created      *   FILE 816
//*           a Broadcast Dataset with 4000 Notice slots, and       *   FILE 816
//*           it appears to work just fine.                         *   FILE 816
//*                                                                 *   FILE 816
//*           Again, you have to APF-authorize this TSO command     *   FILE 816
//*           by including its name in table IKJEFTE2 (authcmd)     *   FILE 816
//*           in PARMLIB, or by using one of our tools (TSUB,       *   FILE 816
//*           LWATMGR, or LLWA) that are in CBT Files 185 and       *   FILE 816
//*           797.  Good luck.                                      *   FILE 816
//*                                                                 *   FILE 816
//*           Note:  I have not imposed an upper limit on the       *   FILE 816
//*           number CVTBCLMT within the BDMNNOTC program.  But     *   FILE 816
//*           my advice is that it shouldn't be over 1000 in        *   FILE 816
//*           a production environment.  (SBG - 12/2009)            *   FILE 816
//*           With large numbers, errors caused by ACCOUNT +        *   FILE 816
//*           SYNC might occur.                                     *   FILE 816
//*                                                                 *   FILE 816
//*           I am supplying a load module library in member        *   FILE 816
//*           LOADMODS, which contains my commercial BDMCLEAN       *   FILE 816
//*           program as well as BDMNNOTC.  BDMCLEAN is a TSO       *   FILE 816
//*           command that cleans up deleted junk in Broadcast      *   FILE 816
//*           Datasets that makes them hard to browse or REVIEW.    *   FILE 816
//*           (REVIEW is the preferred browser for Broadcast        *   FILE 816
//*           Datasets - see File 135 for load modules, or CBT      *   FILE 816
//*           File 134 for source code.)  ISPF Browse leaves        *   FILE 816
//*           off the last byte of the Broadcast Dataset, which     *   FILE 816
//*           you often have to look at, to trace message           *   FILE 816
//*           chains.                                               *   FILE 816
//*                                                                 *   FILE 816
```

