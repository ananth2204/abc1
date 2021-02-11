
## @FILE716.txt
```
//***FILE 716 is from Jim Moore and contains an ISPF application    *   FILE 716
//*           to display MVS enqueues using the new ISPF interface  *   FILE 716
//*           called QUERYENQ.                                      *   FILE 716
//*                                                                 *   FILE 716
//*           A detailed article explaining this interface was      *   FILE 716
//*           published in the March 2005 issue of "Technical       *   FILE 716
//*           Support" magazine from NaSPA.  A version of this      *   FILE 716
//*           article is in this file, as member $ARTICLE.          *   FILE 716
//*                                                                 *   FILE 716
//*           email for Jim Moore:     conlogco@comcast.net         *   FILE 716
//*                                                                 *   FILE 716
//*           email for Mike Tomkins:  mjt6@daimlerchrysler.com     *   FILE 716
//*                                                                 *   FILE 716
//*           email for Lionel Dyck:   lbdyck@gmail.com             *   FILE 716
//*                                                                 *   FILE 716
//*       Newly updated by Lionel Dyck, who incorporated the        *   FILE 716
//*       panels into the REXX.  Please see his notes at the        *   FILE 716
//*       beginning of the program.                                 *   FILE 716
//*                                                                 *   FILE 716
//*       Notes below pertain to Mike Tomkins' updates, and         *   FILE 716
//*       are carried over into Lionel's update.                    *   FILE 716
//*                                                                 *   FILE 716
//*       Mike Tomkins' version is member ENQ00.  Lionel's is       *   FILE 716
//*       member ENQ.                                               *   FILE 716
//*                                                                 *   FILE 716
//*       Once Jim created this package and wrote his article,      *   FILE 716
//*       Mike Tomkins has found a few ways to improve it.  Mike's  *   FILE 716
//*       version may be found in the two members called ENQ00 and  *   FILE 716
//*       ENQ@.  To make it easier to create the pds that installs  *   FILE 716
//*       Mike's ENQ package, I've included two members here, the   *   FILE 716
//*       PDSLOAD program, in TSO XMIT format, and the $PDSLOAD     *   FILE 716
//*       member, which is one-stop JCL to create the install pds   *   FILE 716
//*       for ENQ.  (Maybe overkill--it could have been done by     *   FILE 716
//*       hand.  SBG)  Mike's notes are in member ENQ@.  An         *   FILE 716
//*       excerpt is copied below:                                  *   FILE 716
//*                                                                 *   FILE 716
//*       I thought you might like to get my updates to the ISPF    *   FILE 716
//*       ENQ facility in file 716 originally provided by Jim       *   FILE 716
//*       Moore which accompanied his article in Technical          *   FILE 716
//*       Support.                                                  *   FILE 716
//*                                                                 *   FILE 716
//*       I've loosened the restictions, so to speak, to allow      *   FILE 716
//*       its use as a more general ENQ display facility.  The      *   FILE 716
//*       following are the changes:                                *   FILE 716
//*                                                                 *   FILE 716
//*       1. Removed the restriction that the input must be a       *   FILE 716
//*          DSN; i.e. any pattern or no input can be supplied as   *   FILE 716
//*          an "*" is automatically appended to the input.  If     *   FILE 716
//*          there is no RNAME input, ALL ENQ's for ALL QNAMES      *   FILE 716
//*          are displayed.                                         *   FILE 716
//*                                                                 *   FILE 716
//*       2. Updated to allow a larger popup window width of 77     *   FILE 716
//*          vs. 46.                                                *   FILE 716
//*                                                                 *   FILE 716
//*       3. Updated to allow a larger popup window depth of 39     *   FILE 716
//*          for mod4's and 20 for all other devices vs. the        *   FILE 716
//*          original 8.                                            *   FILE 716
//*                                                                 *   FILE 716
//*       4. Added LIMIT(0) to the QUERYENQ invocation to           *   FILE 716
//*          override the default limit of 5,000 returned table     *   FILE 716
//*          rows.                                                  *   FILE 716
//*                                                                 *   FILE 716
```

