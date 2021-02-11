```
//***FILE 692 is from David Merrifield and contains his UATAPE      *   FILE 692
//*           tape mapping, printing, and dumping utility.  This    *   FILE 692
//*           is an extremely useful tool for finding out what is   *   FILE 692
//*           on a tape, and it also copies tapes.                  *   FILE 692
//*                                                                 *   FILE 692
//*              DAVID L. MERRIFIELD                                *   FILE 692
//*              UNIVERSITY OF ARKANSAS                             *   FILE 692
//*              COMPUTING SERVICES                                 *   FILE 692
//*              155 RAZORBACK ROAD                                 *   FILE 692
//*              FAYETTEVILLE, AR 72701                             *   FILE 692
//*              PHONE:  479-575-5829                               *   FILE 692
//*              FAX  :  479-575-4753                               *   FILE 692
//*              email:  dlm@uark.edu                               *   FILE 692
//*                                                                 *   FILE 692
//*       Fixed to handle 64K blocks on a tape.  Old version        *   FILE 692
//*       has also been included as a fallback.  Load library       *   FILE 692
//*       has been included in XMIT format, for convenience. (SBG)  *   FILE 692
//*                                                                 *   FILE 692
//*       Updated by Johan Derr-Haverlach to allow UATAPE to        *   FILE 692
//*       recognize 3490's and 3590's.  Please see member $$NOTE1.  *   FILE 692
//*                                                                 *   FILE 692
//*       email:  Johan.DerrHaverlach@combined.com                  *   FILE 692
//*                                                                 *   FILE 692
//*   PARM FIELD OPTIONS:                                           *   FILE 692
//*                                                                 *   FILE 692
//*       OPTIONS ARE SPECIFIED IN THE PARM= PARAMETER ON THE       *   FILE 692
//*       EXEC STATEMENT.  EACH OPTION SHOULD BE SEPARATED BY A     *   FILE 692
//*       SINGLE COMMA, WITH NO SPACES ALLOWED.  THE LIST OF        *   FILE 692
//*       VALID OPTIONS FOLLOWS:                                    *   FILE 692
//*                                                                 *   FILE 692
//*       LIST     - PRINT LABEL RECORD INFORMATION (DEFAULT)       *   FILE 692
//*       COPY     - COPY SYSUT1 TAPE TO SYSUT2 TAPE                *   FILE 692
//*       DUMP     - PRINT ALL DATA RECORDS IN HEX FORMAT           *   FILE 692
//*       DUMPLAB  - PRINT ALL LABEL RECORDS IN HEX FORMAT          *   FILE 692
//*       DUMPALL  - PRINT ALL LABEL RECORDS AND DATA RECORDS       *   FILE 692
//*                  IN HEXADECIMAL FORMAT                          *   FILE 692
//*       BLOCKS   - PRINT SIZE OF DATA RECORDS                     *   FILE 692
//*       PRINT    - PRINT ALL DATA RECORDS (EBCDIC FORMAT)         *   FILE 692
//*       CRT      - OUTPUT IS FORMATTED FOR 80-COLUMN CRT          *   FILE 692
//*                  SCREEN                                         *   FILE 692
//*       ATOE     - ALL LABELS AND DATA ON SYSUT1 TRANSLATED       *   FILE 692
//*                  FROM ASCII TO EBCDIC                           *   FILE 692
//*       ETOA     - ALL LABELS AND DATA ON SYSUT1 TRANSLATED       *   FILE 692
//*                  FROM EBCDIC TO ASCII                           *   FILE 692
//*       BYPASS   - BYPASSES LABEL CHECKING FOR SYSUT2 TAPE IF     *   FILE 692
//*                  COPY ALSO SPECIFIED                            *   FILE 692
//*       VERBATIM - DOES NOT CHANGE CONTENT OF DATA RECORDS        *   FILE 692
//*                  (E.G., WON'T CHANGE LABEL INFORMATION LIKE     *   FILE 692
//*                  VOLUME SERIAL, DENSITY FIELD, ETC.)            *   FILE 692
//*       DUMPMAX=NNN  - SPECIFY MAXIMUM NUMBER OF BLOCKS TO        *   FILE 692
//*                      DUMP IF DUMP, DUMPLAB, OR DUMPALL IS       *   FILE 692
//*                      ALSO SPECIFIED                             *   FILE 692
//*       PRINTMAX=NNN - SPECIFY MAXIMUM NUMBER OF RECORDS TO       *   FILE 692
//*                      PRINT IF PRINT SPECIFIED                   *   FILE 692
//*       MAXFILES=NNN - SPECIFY MAXIMUM NUMBER OF FILES ON         *   FILE 692
//*                      TAPE TO TO PROCESS                         *   FILE 692
//*       LTM      - IGNORE ANY LEADING TAPE MARKS ON THE           *   FILE 692
//*                  SYSUT1 TAPE                                    *   FILE 692
//*       SKIPLAB  - SKIP WRITING ANY LABELS ON THE SYSUT2 TAPE     *   FILE 692
//*                  WHILE COPYING IF COPY IS ALSO SPECIFIED.       *   FILE 692
//*                  IN EFFECT, SYSUT2 TAPE WILL BE A               *   FILE 692
//*                  NON-LABELED TAPE AFTERWARDS                    *   FILE 692
//*       SKIPBAD  - SKIP OVER ANY BLOCKS OF DATA ON INPUT TAPE     *   FILE 692
//*                  THAT CAUSE PERMANENT I/O ERRORS IN AN          *   FILE 692
//*                  EFFORT TO RECOVER ANY DATA THAT FOLLOWS THE    *   FILE 692
//*                  BAD BLOCK(S).  (RECOMMEND USE WITH SKIPLAB     *   FILE 692
//*                  AND COPY OPTIONS TO BUILD A NON-LABELED        *   FILE 692
//*                  TAPE CONTAINING ONLY THE READABLE BLOCKS OF    *   FILE 692
//*                  THE BAD TAPE.)                                 *   FILE 692
//*                                                                 *   FILE 692

```
