
## @FILE226.txt
```
//***FILE 226 IS A COMPARE PROGRAM RECEIVED FROM YALE UNIVERSITY    *   FILE 226
//*           WHICH WAS WRITTEN BY MR DAVID B COLE.                 *   FILE 226
//*                                                                 *   FILE 226
//*     DAVE COLE IS NOW AT COLE SOFTWARE IN CHARLOTTESVILLE, VA.   *   FILE 226
//*                                                                 *   FILE 226
//*           Colesoft Marketing, Inc.                              *   FILE 226
//*           414 3rd ST. NE                                        *   FILE 226
//*           Charlottesville, VA 22902 USA                         *   FILE 226
//*           540-456-8210                                          *   FILE 226
//*           www.colesoft.com                                      *   FILE 226
//*           email:  dbcole@gmail.com                              *   FILE 226
//*                                                                 *   FILE 226
//* THE MACROS NEEDED TO ASSEMBLE THIS VERSION ARE CONTAINED IN     *   FILE 226
//* FILE 408 OF THIS UTILITIES TAPE.  FOR ADDITIONAL INFORMATION    *   FILE 226
//* SEE THE COMMENTS IN THE SOURCE CODE ITSELF.                     *   FILE 226
//*                                                                 *   FILE 226
//*      THE CMPRSEQ PROGRAM COMPARES TWO SEQUENTIAL CARD           *   FILE 226
//*      IMAGE FILES AND REPORTS PRECISELY THE DIFFERENCES          *   FILE 226
//*      BETWEEN THE TWO.  SUCH DIFFERENCES CAN CONSIST OF          *   FILE 226
//*      INSERTIONS, DELETIONS, AND REPLACEMENTS (OF EITHER         *   FILE 226
//*      EQUAL OR UNEQUAL SIZES).                                   *   FILE 226
//*                                                                 *   FILE 226
//*      CMPRSEQ ACCOMPLISHES THIS BY READING THE TWO INPUT         *   FILE 226
//*      FILES ALTERNATELY AND COMPARING THE CARD IMAGES AS IT      *   FILE 226
//*      GOES ALONG.  WHEN IT ENCOUNTERS TWO CARDS THAT             *   FILE 226
//*      MISMATCH, IT SAVES THEM AND CONTINUES TO READ THE TWO      *   FILE 226
//*      FILES ALTERNATELY.  EACH TIME IT READS A CARD FROM ONE     *   FILE 226
//*      FILE, IT COMPARES IT TO ALL CARDS THAT IT HAS READ         *   FILE 226
//*      FROM THE OTHER FILE SINCE THE START OF THE MISMATCH.       *   FILE 226
//*      IF NO MATCH IS FOUND, THEN IT SAVES THAT CARD AND          *   FILE 226
//*      PROCEEDS TO READ THE NEXT CARD FROM THE OTHER FILE.        *   FILE 226
//*      CMPRSEQ CONTINUES ALTERNATING BACK AND FORTH IN THIS       *   FILE 226
//*      MANNER UNTIL IT HAS READ A CARD THAT DOES MATCH ONE        *   FILE 226
//*      OF THE SAVED CARDS FROM THE OTHER FILE.  THE MISMATCH      *   FILE 226
//*      THEN CONSISTS OF ALL CARDS IN THE TWO SAVED STACKS         *   FILE 226
//*      THAT ARE BELOW THE TWO MATCHING CARDS.                     *   FILE 226
//*                                                                 *   FILE 226
//*      THE MISMATCHED CARDS ARE DUMPED OUT TO LOGGING             *   FILE 226
//*      DATASETS, AND THEN CMPRSEQ PROCEEDS TO LOOK FOR THE        *   FILE 226
//*      NEXT MISMATCHED BLOCK.                                     *   FILE 226
//*                                                                 *   FILE 226
//*                   LIMITATIONS                                   *   FILE 226
//*                                                                 *   FILE 226
//*      CMPRSEQ WILL COMPARE ONLY CARD IMAGE FILES - I.E.,         *   FILE 226
//*      FILES HAVING FIXED LENGTH RECORDS THAT ARE 80 BYTES        *   FILE 226
//*      LONG.                                                      *   FILE 226
//*                                                                 *   FILE 226
//*      CMPRSEQ WILL COMPARE ONLY ONE PAIR OF FILES PER            *   FILE 226
//*      INVOCATION.  IT WILL NOT COMPARE AN ENTIRE PDS             *   FILE 226
//*      LIBRARY, ALTHOUGH IT WILL COMPARE A JCL SELECTED PDS       *   FILE 226
//*      LIBRARY MEMBER.                                            *   FILE 226
//*                                                                 *   FILE 226
//*      IF AN INSERTION BLOCK (FOR EXAMPLE) CONTAINS A CARD        *   FILE 226
//*      WHOSE DUPLICATE ALREADY APPEARS COMMONLY THROUGHOUT        *   FILE 226
//*      THE FILES BEING COMPARED (E.G., THE "SPACE 1"              *   FILE 226
//*      ASSEMBLER LANGUAGE STATEMENT, ETC.), THEN THE              *   FILE 226
//*      COMPARISON MAY BECOME, TO A GREATER OR LESSER DEGREE,      *   FILE 226
//*      DESYNCHRONIZED DUE TO THE INSERTED CARD FINDING A          *   FILE 226
//*      MATCH WITH A PRE-EXISTING COPY OF THAT CARD IN THE         *   FILE 226
//*      OTHER FILE.  CMPRSEQ PROVIDES MECHANISMS TO HELP DEAL      *   FILE 226
//*      WITH SYNCHRONIZATION PROBLEMS.  (NOTE, SYNCHRONIZATION     *   FILE 226
//*      PROBLEMS CAN OCCUR, NOT JUST WITH INSERTED BLOCKS,         *   FILE 226
//*      BUT ALSO WITH DELETED BLOCKS AND WITH REPLACED             *   FILE 226
//*      BLOCKS).                                                   *   FILE 226
//*                   JCL                                           *   FILE 226
//*                                                                 *   FILE 226
//*      EXEC CARD KEYWORD: REGION=                                 *   FILE 226
//*                                                                 *   FILE 226
//*      CMPRSEQ'S MEMORY REQUIREMENTS VARY ACCORDING TO THE        *   FILE 226
//*      AGGREGATE SIZE OF THE LARGEST PAIR OF MISMATCHED           *   FILE 226
//*      BLOCKS ENCOUNTERED.  IF A MEMORY SHORTAGE OCCURS, THEN     *   FILE 226
//*      CMPRSEQ TERMINATES IMMEDIATELY; CONSEQUENTLY, IT IS        *   FILE 226
//*      BEST TO PROVIDE A GENEROUS AMOUNT OF AVAILABLE             *   FILE 226
//*      MEMORY.  USUALLY, REGION=1024K SHOULD BE ENOUGH.           *   FILE 226
//*                                                                 *   FILE 226
//*      EXEC CARD KEYWORD: PARM=FULL                               *   FILE 226
//*                                                                 *   FILE 226
//*      BY DEFAULT CMPRSEQ WILL COMPARE TWO CARDS ONLY IN          *   FILE 226
//*      COLUMNS 1 THROUGH 72, THUS IGNORING THE SEQUENCE           *   FILE 226
//*      NUMBER FIELD.  SPECIFYING PARM=FULL CAUSES CMPRSEQ TO      *   FILE 226
//*      EXAMINE EACH CARD IN ALL 80 COLUMNS.                       *   FILE 226
//*                                                                 *   FILE 226
//*      DDNAMES: OLD AND NEW                                       *   FILE 226
//*                                                                 *   FILE 226
//*             ATTRIBUTES                                          *   FILE 226
//*             ACCESS METHOD   QSAM                                *   FILE 226
//*             DSORG           PS                                  *   FILE 226
//*             RECFM           F OR FB                             *   FILE 226
//*             LRECL           80                                  *   FILE 226
//*             BLKSIZE         80*N                                *   FILE 226
//*             DEFAULTS        (PS,F,80,80)                        *   FILE 226
//*                                                                 *   FILE 226
//*      THESE DDNAMES (OLD AND NEW) MUST DESIGNATE THE TWO         *   FILE 226
//*      FILES TO BE COMPARED. THEIR EXISTANCE IS REQUIRED.         *   FILE 226
//*      USUALLY, ONE FILE IS AN UPDATED (NEWER) VERSION OF         *   FILE 226
//*      THE OTHER, HENCE NAMES OLD AND NEW.                        *   FILE 226
//*                                                                 *   FILE 226
//*      DDNAME: SYSPRINT                                           *   FILE 226
//*                                                                 *   FILE 226
//*             ATTRIBUTES                                          *   FILE 226
//*             ACCESS METHOD   QSAM                                *   FILE 226
//*             DSORG           PS                                  *   FILE 226
//*             RECFM           UA, VA, VBA, FA, OR FBA             *   FILE 226
//*             LRECL           133 OR LARGER                       *   FILE 226
//*             BLKSIZE         133 OR LARGER                       *   FILE 226
//*             DEFAULTS        (PS,VBA,137,4096)                   *   FILE 226
//*                                                                 *   FILE 226
//*      THE SYSPRINT FILE IS OPTIONAL.  IF IT IS AVAILABLE,        *   FILE 226
//*      THEN IT RECEIVES A LOG OF ALL DISCOVERED MISMATCHES.       *   FILE 226
//*      FOR EACH MISMATCHED BLOCK, BOTH THE OLD AND NEW            *   FILE 226
//*      VERSION OF THAT BLOCK IS SHOWN.                            *   FILE 226
//*                                                                 *   FILE 226
//*      DDNAMES: OLDLIST AND NEWLIST                               *   FILE 226
//*                                                                 *   FILE 226
//*             ATTRIBUTES                                          *   FILE 226
//*             ACCESS METHOD   QSAM                                *   FILE 226
//*             DSORG           PS                                  *   FILE 226
//*             RECFM           UA, VA, VBA, FA, OR FBA             *   FILE 226
//*             LRECL           133 OR LARGER                       *   FILE 226
//*             BLKSIZE         133 OR LARGER                       *   FILE 226
//*             DEFAULTS        (PS,VBA,137,4096)                   *   FILE 226
//*                                                                 *   FILE 226
//*      BOTH OLDLIST AND NEWLIST ARE OPTIONAL. IF ONE (OR          *   FILE 226
//*      BOTH) ARE AVAILABLE, THEN A COPY OF THE OLD (OR NEW)       *   FILE 226
//*      FILE IS WRITTEN TO IT WITH THE LOCATIONS OF ALL            *   FILE 226
//*      MISMATCHES CLEARLY FLAGGED.                                *   FILE 226
//*                                                                 *   FILE 226
//*      DDNAME: IGNORE                                             *   FILE 226
//*                                                                 *   FILE 226
//*             ATTRIBUTES                                          *   FILE 226
//*             ACCESS METHOD   QSAM                                *   FILE 226
//*             DSORG           PS                                  *   FILE 226
//*             RECFM           F OR FB                             *   FILE 226
//*             LRECL           80                                  *   FILE 226
//*             BLKSIZE         80*N                                *   FILE 226
//*             DEFAULTS        (PS,F,80,80)                        *   FILE 226
//*                                                                 *   FILE 226
//*      THE IGNORE FILE IS OPTIONAL.  IF IT IS AVAILABLE, THEN     *   FILE 226
//*      IT IS USED TO HELP CONTROL THE POSSIBLE                    *   FILE 226
//*      DESYNCHRONIZATION PROBLEMS DISCUSSED EARLIER.  THE         *   FILE 226
//*      IGNORE FILE SHOULD CONTAIN COPIES OF CARD IMAGES THAT      *   FILE 226
//*      APPEAR REPEATEDLY THROUGHOUT THE FILES BEING               *   FILE 226
//*      COMPARED, AND ESPECIALLY APPEARING IN AREAS AFFECTED       *   FILE 226
//*      BY INSERTIONS AND DELETIONS.  COPIES OF THESE CARDS,       *   FILE 226
//*      WHEN ENCOUNTERED DURING A MISMATCH RESOLUTION              *   FILE 226
//*      PROCESS, WILL NOT BE USED TO RESOLVE THE MISMATCH.  BY     *   FILE 226
//*      THIS MEANS THE POSSIBILITY OF DESYNCHRONIZATION CAN        *   FILE 226
//*      BE REDUCED.                                                *   FILE 226
//*                                                                 *   FILE 226
//*      DDNAME: SYNC                                               *   FILE 226
//*                                                                 *   FILE 226
//*             ATTRIBUTES                                          *   FILE 226
//*             ACCESS METHOD   QSAM                                *   FILE 226
//*             DSORG           PS                                  *   FILE 226
//*             RECFM           F OR FB                             *   FILE 226
//*             LRECL           80                                  *   FILE 226
//*             BLKSIZE         80*N                                *   FILE 226
//*             DEFAULTS        (PS,F,80,80)                        *   FILE 226
//*                                                                 *   FILE 226
//*      UNFORTUNATELY, VERY LARGE FILES MAY HAVE TOO MANY          *   FILE 226
//*      COMMONLY REOCCURING CARDS FOR THE IGNORE FILE TO BE        *   FILE 226
//*      WHOLLY EFFECTIVE IN ELIMINATING DESYNCHRONIZATION          *   FILE 226
//*      PROBLEMS.  IF THIS IS THE CASE, THEN THE SYNC FILE CAN     *   FILE 226
//*      BE PROVIDED TO FORCE RESYNCHRONIZATION AT PARTICULAR       *   FILE 226
//*      POINTS IN THE FILES BEING COMPARED.  THIS FILE SHOULD      *   FILE 226
//*      CONTAIN COPIES OF ONE OR MORE CARDS EACH OF WHICH          *   FILE 226
//*      APPEARS EXACTLY ONCE IN BOTH THE OLD AND NEW FILES.        *   FILE 226
//*      THE CARDS IN THE SYNC FILE SHOULD APPEAR IN THE SAME       *   FILE 226
//*      ORDER BY WHICH THEY APPEAR IN THE OLD AND NEW FILES.       *   FILE 226
//*      THEY SHOULD REPRESENT POINTS IN THE OLD AND NEW FILES      *   FILE 226
//*      AT WHICH YOU WISH TO FORCE COMPARISON SYNCHRONIZATION.     *   FILE 226
//*      GENERALLY, SUCH POINTS WILL BE FOLLOWING THOSE AREAS       *   FILE 226
//*      WHERE OTHERWISE UNRECOVERABLE DESYNCHRONIZATION HAS        *   FILE 226
//*      OCCURED.                                                   *   FILE 226
//*                                                                 *   FILE 226
//*      WHEN CMPRSEQ ENCOUNTERS A RESYNCHRONIZATION POINT          *   FILE 226
//*      (I.E., WHEN IT HAS READ A CARD FROM ONE OF THE             *   FILE 226
//*      COMPARISON FILES THAT EXACTLY MACTHES THE NEXT CARD        *   FILE 226
//*      FROM THE SYNC FILE), IT WILL NOT READ ANY FURTHER          *   FILE 226
//*      FROM THAT FILE UNTIL IT READS THE IDENTICAL CARD FROM      *   FILE 226
//*      THE OTHER FILE.  THIS HAS THE EFFECT OF FORCING THE        *   FILE 226
//*      RESOLUTION OF A CURRENT MISMATCH (IF ANY) AT THE           *   FILE 226
//*      RESINCHRONIZATION POINT.                                   *   FILE 226
//*                                                                 *   FILE 226
//*      THE SYNC FILE IS OPTIONAL.  IF IT IS AVAILABLE, THEN       *   FILE 226
//*      IS MUST BE CORRECTLY FORMED.  IF IT IS NOT (I.E., IF       *   FILE 226
//*      IT IS OUT OF SEQUENCE, OR IF IT CONTAINS A CARD THAT       *   FILE 226
//*      DOES NOT APPEAR IN BOTH THE OLD AND NEW FILES), THEN       *   FILE 226
//*      THE CMPRSEQ RUN WILL FAIL.                                 *   FILE 226
//*                                                                 *   FILE 226
//*                   COMPLETION CODES                              *   FILE 226
//*                                                                 *   FILE 226
//*       0 - PROCESSING HAS COMPLETED SUCCESSFULLY.  NO            *   FILE 226
//*           MISMATCHES HAVE BEEN FOUND.                           *   FILE 226
//*                                                                 *   FILE 226
//*       4 - PROCESSING HAS COMPLETED SUCCESSFULLY.  AT LEAST      *   FILE 226
//*           ONE MISMATCH HAS BEEN FOUND.                          *   FILE 226
//*                                                                 *   FILE 226
//*      12 - PROCESSING HAS FAILED.  A MEMORY SHORTAGE HAS         *   FILE 226
//*           OCCURED.                                              *   FILE 226
//*                                                                 *   FILE 226
//*      16 - PROCESSING HAS ABORTED.  ONE OF THE COMPARISON        *   FILE 226
//*           FILES (DDNAME OLD OR NEW) IS NOT AVAILABLE.           *   FILE 226
//*                                                                 *   FILE 226
//*                                                                 *   FILE 226
```

