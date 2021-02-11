
## @FILE793.txt
```
//***FILE 793 is from Richard Rice and contains his modifications   *   FILE 793
//*           to SDF (Spool Display Facility) for JES3.  Changes    *   FILE 793
//*           were made to SDF 2.9, whereas SDF 3.4 is the current  *   FILE 793
//*           version.  Further explanations are shown below.       *   FILE 793
//*                                                                 *   FILE 793
//*           The modifications presented here are coded for SDF    *   FILE 793
//*           3.4, but they were not tested--they just assembled    *   FILE 793
//*           cleanly using the SDF 3.4 macros.  So at this time,   *   FILE 793
//*           we have to regard this code as an alpha test.         *   FILE 793
//*                                                                 *   FILE 793
//*           email:  Richard.L.Rice@conocophillips.com             *   FILE 793
//*                                                                 *   FILE 793
//*    What was done:                                               *   FILE 793
//*                                                                 *   FILE 793
//*       Here are the source, ISPPLIB, and ISPMLIB for the new     *   FILE 793
//*       functions I added to our SDF.                             *   FILE 793
//*                                                                 *   FILE 793
//*       Again we use SDF 2.9.  I have no way to test SDF 3.4.     *   FILE 793
//*                                                                 *   FILE 793
//*       Anyone that wants to try this will need to update their   *   FILE 793
//*       assembly and link jobs.  The MAIN line program changes    *   FILE 793
//*       quite a bit from 2.9 to 3.4.  I'm not too sure that       *   FILE 793
//*       update I made to SDFMAIN is all that is required for      *   FILE 793
//*       SDFMAIN or not.                                           *   FILE 793
//*                                                                 *   FILE 793
//*       I added "A" and "E" as primary options, so I updated      *   FILE 793
//*       our primary menu SPF panel.  The new ACT and ENQ          *   FILE 793
//*       functions use new ISPF panels.  I think I have included   *   FILE 793
//*       all the new panels in the "sdfplib".  There were some     *   FILE 793
//*       new messages, so there is one new member in the           *   FILE 793
//*       SDFMLIB.                                                  *   FILE 793
//*                                                                 *   FILE 793
```

