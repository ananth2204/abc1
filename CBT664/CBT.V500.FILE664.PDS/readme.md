
## @FILE664.txt
```
//***FILE 664 is from Jay Moseley and contains date conversion      *   FILE 664
//*           subroutines written in Assembler.                     *   FILE 664
//*                                                                 *   FILE 664
//*           email:     jay@jaymoseley.com                         *   FILE 664
//*           web site:  www.jaymoseley.com                         *   FILE 664
//*                                                                 *   FILE 664
//*     In 1998 I, along with most of the rest of the world, was    *   FILE 664
//*     thinking about the approach of the year 2000 and the        *   FILE 664
//*     implications that held for incompatible two digit years.    *   FILE 664
//*     I brought together some routines I had written earlier      *   FILE 664
//*     in several languages (COBOL, BASIC, and Assembler) and      *   FILE 664
//*     the result was this group of Assembler subroutines that     *   FILE 664
//*     can be used to perform any required date format             *   FILE 664
//*     conversion:                                                 *   FILE 664
//*                                                                 *   FILE 664
//*     This is the source/jobstream dataset for the Y2K routines.  *   FILE 664
//*                                                                 *   FILE 664
//*     $INDEX   - this text                                        *   FILE 664
//*     EYEC     - ALC macro                                        *   FILE 664
//*     YREGS    - ALC macro                                        *   FILE 664
//*     Y2K$ASM  - jobstream to assemble/link the routines          *   FILE 664
//*     Y2K$INST - jobstream to allocate load library & submit      *   FILE 664
//*                Y2K$ASM                                          *   FILE 664
//*     Y2K$IVP  - jobstream to run the installation                *   FILE 664
//*                verification program                             *   FILE 664
//*     Y2KATOG  - Astronomical number to Gregorian date            *   FILE 664
//*     Y2KCONV  - Convert dates between formats                    *   FILE 664
//*     Y2KDFMT  - Edit Gregorian date using predefined formats     *   FILE 664
//*     Y2KDOWN  - Compute Day of Week number for date              *   FILE 664
//*     Y2KESTR  - Calculate date Easter falls on for given year    *   FILE 664
//*     Y2KGETD  - Return System date                               *   FILE 664
//*     Y2KGTOA  - Gregorian date to Astronomical number            *   FILE 664
//*     Y2KGTOJ  - Gregorian date to Julian date                    *   FILE 664
//*     Y2KIVP   - COBOL Installation Verification program          *   FILE 664
//*     Y2KIVPD  - SYSIN data for Y2KIVP program                    *   FILE 664
//*     Y2KJTOG  - Julian date to Gregorian date                    *   FILE 664
//*     Y2KLAGE  - Long term difference between dates               *   FILE 664
//*     Y2KLEAP  - Test year for Leap year status                   *   FILE 664
//*     Y2KPROJ  - Return date using given offset from given        *   FILE 664
//*                date                                             *   FILE 664
//*     Y2KSAGE  - Short term difference between dates              *   FILE 664
//*     Y2KTDOW  - Return date for given day of week and given      *   FILE 664
//*                date                                             *   FILE 664
//*                                                                 *   FILE 664
//*     For several financial applications I had written in the     *   FILE 664
//*     past, I required a date record to be provided from which    *   FILE 664
//*     interest would be calculated either from the prior run      *   FILE 664
//*     date to the current run date or from the current run        *   FILE 664
//*     date forward to the next run date.  I wrote a program       *   FILE 664
//*     that utilized the date routines above to derive such a      *   FILE 664
//*     date record using the current system date and a file of     *   FILE 664
//*     rules to specify the observed holidays:                     *   FILE 664
//*                                                                 *   FILE 664
//*         RUNDATES   Program to build run dates record            *   FILE 664
//*         RUNDCOPY   Copy book for run dates record               *   FILE 664
//*                                                                 *   FILE 664
//*     In addition to the date routines, I wrote a COBOL           *   FILE 664
//*     program to scan source code for likely date references.     *   FILE 664
//*     The program is based upon the design of a BASIC program     *   FILE 664
//*     that was placed in the public domain by the National        *   FILE 664
//*     Institute of Standards.  The program is driven by a         *   FILE 664
//*     glossary table read in at run time.                         *   FILE 664
//*                                                                 *   FILE 664
//*         Y2KSCAN                                                 *   FILE 664
//*                                                                 *   FILE 664
//*     On this file, there is also an MS/DOS executable, which     *   FILE 664
//*     will calculate the elapsed time between two dates.  This    *   FILE 664
//*     is member ELAPSEXE.  Just download the member to a PC       *   FILE 664
//*     in binary, give it an .exe suffix, and execute it.          *   FILE 664
//*     Equivalent COBOL source to run on the mainframe is          *   FILE 664
//*     included as member ELAPSED.  These programs use the         *   FILE 664
//*     subroutines (or PC equivalents) from the rest of this       *   FILE 664
//*     file.                                                       *   FILE 664
//*                                                                 *   FILE 664
```

