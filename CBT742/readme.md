```
//***FILE 742 is from Bob Birdsall and contains a source code       *   FILE 742
//*           versioning system that works for PARMLIB and other    *   FILE 742
//*           system level datasets such as TCPPARMS.               *   FILE 742
//*                                                                 *   FILE 742
//*           email:  "Bob Birdsall" <bsquare@med.umich.edu>        *   FILE 742
//*                                                                 *   FILE 742
//*     Hi.  'Archive' is a source versioning system for ISPF       *   FILE 742
//*     Edit/View.                                                  *   FILE 742
//*                                                                 *   FILE 742
//*     It is in the early stages of development (it works,         *   FILE 742
//*     but...  :)                                                  *   FILE 742
//*     The documentation members all begin with #.                 *   FILE 742
//*     Everything else begins with A#.                             *   FILE 742
//*                                                                 *   FILE 742
//*     Documentation members are:                                  *   FILE 742
//*        #CONFIG  - ISPF configuration data                       *   FILE 742
//*        #CPARC   - Job to copy archive members                   *   FILE 742
//*        #DESC    - Overview of the system                        *   FILE 742
//*        #DETAIL  - Detailed information                          *   FILE 742
//*        #FORMAT  - Data format used for the archives             *   FILE 742
//*        #HISTORY - Revision history                              *   FILE 742
//*        #INSTALL - Installation instructions                     *   FILE 742
//*        #TOUCHJB - update Last Known Working Member's time       *   FILE 742
//*                                                                 *   FILE 742
//*     We do use this for SYS1.PARMLIB, SYS1.TCPPARMS and          *   FILE 742
//*     other datasets, but there are only 3 z/OS system            *   FILE 742
//*     programmers in my shop.                                     *   FILE 742
//*                                                                 *   FILE 742
//*     We do not use this for application source code, yet.        *   FILE 742
//*     It needs some more work (and management acceptance).        *   FILE 742
//*                                                                 *   FILE 742
//*     The only warning I would like to give those to whom         *   FILE 742
//*     this is distributed follows:                                *   FILE 742
//*                                                                 *   FILE 742
//*     NOTE: all these rexx execs, etc. are SAMPLES ONLY.  Any     *   FILE 742
//*     experimentation with them is at your own risk.  Do not      *   FILE 742
//*     trust your data/processes to them without personally        *   FILE 742
//*     verifying all logic and operation.  All supplied execs      *   FILE 742
//*     are works in progress and DO contain bugs and               *   FILE 742
//*     significant undocumented limitations.                       *   FILE 742
//*                                                                 *   FILE 742
//*     I hope you enjoy this.                                      *   FILE 742
//*                                                                 *   FILE 742

```
