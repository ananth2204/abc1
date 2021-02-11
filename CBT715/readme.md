```
//***FILE 715 is a revival of the Tape Erase program that used to   *   FILE 715
//*           be on File 370 of the CBT Tape Version 249 from July  *   FILE 715
//*           1985.  This is an old program from the Federal Bank   *   FILE 715
//*           of (West) Germany from the very early 1980s.          *   FILE 715
//*                                                                 *   FILE 715
//*       Questions or problems about this program should be        *   FILE 715
//*       directed to Sam Golob:   sbgolob@cbttape.org              *   FILE 715
//*                                                                 *   FILE 715
//*       Two versions of this program are presented.  The first    *   FILE 715
//*       is called DSE, and the second, for MVS systems that are   *   FILE 715
//*       too primitive to have the OPEN with EXTEND option, is     *   FILE 715
//*       called DSEALT.  The original two programs and instruc-    *   FILE 715
//*       tions are presented unchanged, as member DSEORIG.         *   FILE 715
//*                                                                 *   FILE 715
//*       Modern assembly-linkedit JCL is member DSE$, and some     *   FILE 715
//*       sample run JCL is presented as member DSE@.  Below is     *   FILE 715
//*       the original description of the program from CBT Tape     *   FILE 715
//*       File 001, with only the German spelling of the word       *   FILE 715
//*       "programm" changed to the spelling "program".             *   FILE 715
//*                                                                 *   FILE 715
//*  Original description of this program...                        *   FILE 715
//*                                                                 *   FILE 715
//*          FILE 370 IS A TAPE ERASE PROGRAM FROM THE              *   FILE 715
//*          FEDERAL BANK OF WEST GERMANY.  THE FOLLOWING           *   FILE 715
//*          IS A DETAILED DESCRIPTION.                             *   FILE 715
//*                                                                 *   FILE 715
//*          PROGRAM TO ERASE A TAPE STARTING AFTER A               *   FILE 715
//*          GIVEN DATASET UNTIL IT REACHES THE REFLECTIVE          *   FILE 715
//*          SPOT, THEREAFTER IT WRITES SOME ERASE GAPS TO          *   FILE 715
//*          BE 200 PERCENT SURE.                                   *   FILE 715
//*                                                                 *   FILE 715
//*          THIS PROGRAM HANDLES SL AND NL TAPES, AND              *   FILE 715
//*          USES THE DATA-SECURITY-ERASE HARDWARE                  *   FILE 715
//*          COMMAND TO DO THE JOB. NO CHANNEL BUSY, NO             *   FILE 715
//*          CPU-BUSY. MERELY THE CONTROL UNIT IS BUSY.             *   FILE 715
//*                                                                 *   FILE 715
//*          WITH THIS PROGRAM YOU CAN ERASE BOTH SL AND            *   FILE 715
//*          NL TAPES.  ALL YOU HAVE TO DO IS SUPPLY THE            *   FILE 715
//*          LAST DATASET NAME THAT SHOULD REMAIN ON THE            *   FILE 715
//*          VOLUME.                                                *   FILE 715
//*                                                                 *   FILE 715
//*          THE PROGRAM HANDLES ALL POSSIBLE CONDITIONS            *   FILE 715
//*                                                                 *   FILE 715
//*             IT CHECKS THAT THERE IS A FILE-PROTECT              *   FILE 715
//*             RING ON THE TAPE.                                   *   FILE 715
//*                                                                 *   FILE 715
//*             IT CHECKS THE CONDITION THAT THE FILE               *   FILE 715
//*             ALREADY REACHED THE REFLECTIVE SPOT.                *   FILE 715
//*                                                                 *   FILE 715
//*          NORMAL OPERATION FOR A MULTI-VOLUME DATASET            *   FILE 715
//*          IS THAT THE PROGRAM TAKES THE LAST VOLUME              *   FILE 715
//*          AND ERASES IT, YOU CAN SUPPLY A PARM VALUE OF          *   FILE 715
//*          'H', IN THAT CASE THE PROGRAM TAKES EVERY              *   FILE 715
//*          VOLUME OF A MULTI-VOLUME DATASET AND ERASES            *   FILE 715
//*          IT, THIS WAS TO HANDLE A SITUATION IN OUR              *   FILE 715
//*          INSTALLATION WHERE A PROGRAM HAD TO WRITE A            *   FILE 715
//*          GIVEN AMOUNT OF BLOCKS ON EVERY SINGLE REEL            *   FILE 715
//*          OF A MULTI-VOLUME DATASET AND THEN SWITCHED            *   FILE 715
//*          THE VOLUME USING FORCED-END-OF-VOLUME.                 *   FILE 715
//*                                                                 *   FILE 715

```
