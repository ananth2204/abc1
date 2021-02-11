```
//***FILE 948 is from Duc Tuan Nguyen (dt n) and contains REXX      *   FILE 948
//*           programs of considerable complexity, which he has     *   FILE 948
//*           found useful in his z/OS, DB2, and CICS work.         *   FILE 948
//*                                                                 *   FILE 948
//*           email:  dt n <ndt2004@gmail.com>                      *   FILE 948
//*                                                                 *   FILE 948
//*     Description of Programs -                                   *   FILE 948
//*                                                                 *   FILE 948
//*     IFCREADS - REXX WHICH READS AN IFCID401 SAMPLE AND          *   FILE 948
//*             PROVIDES A CSV DATASET FOR ANALYSIS                 *   FILE 948
//*             (Comma Separated Variables)                         *   FILE 948
//*                                                                 *   FILE 948
//*     This Rexx is inspired from Rexx program MEMU provided       *   FILE 948
//*     by IBM. It starts a Monitor trace and reads the buffer      *   FILE 948
//*     returned. In this Rexx I read IFCID401 which is called      *   FILE 948
//*     "Static Statement Cache".  The data returned can be         *   FILE 948
//*     used in different ways.                                     *   FILE 948
//*                                                                 *   FILE 948
//*     IFCID 401 is mapped using a "varying length repeating       *   FILE 948
//*     group", so the processing is different than IFCID 225       *   FILE 948
//*     (easier) which is read by MEMU for example.                 *   FILE 948
//*                                                                 *   FILE 948
//*     The data returned is really huge so you should filter       *   FILE 948
//*     directly from the REXX or by qualifying your READS          *   FILE 948
//*     request. Time is GMT (I think) so don't be surprised.       *   FILE 948
//*                                                                 *   FILE 948
//*     PDS2SEQ - A REXX program to put a PDS into sequential       *   FILE 948
//*               format                                            *   FILE 948
//*                                                                 *   FILE 948
//*     I use my PC as a "data store", where I have anything        *   FILE 948
//*     on it (Manuals, Redbooks, documents, presentations          *   FILE 948
//*     ...). And with the help of a search software                *   FILE 948
//*     (Archivarius seems to be the best search software that      *   FILE 948
//*     I've found after many tests), I am able to find             *   FILE 948
//*     anything on my PC (A sort of Google search on my PC).       *   FILE 948
//*                                                                 *   FILE 948
//*     So, it is interesting for me to be able to retrieve         *   FILE 948
//*     data that are on PDS from my search software.  This         *   FILE 948
//*     Rexx reads a PDS, puts it in a sequential format , so       *   FILE 948
//*     I can ftp it on my PC. It provides also jcl that you        *   FILE 948
//*     can use to reload the sequential into a PDS format.         *   FILE 948
//*                                                                 *   FILE 948
//*     It is adapted from a Rexx that I've found on the web        *   FILE 948
//*     (unfortunately I am not able to find the first author.)     *   FILE 948
//*                                                                 *   FILE 948
//*     (Revised by dt n, Mar 26, 2019).                            *   FILE 948
//*                                                                 *   FILE 948
//*     S110CSV - REXX TO CREATE A CSV DATASET FROM SMF110          *   FILE 948
//*                      (CICS PERFORMANCE RECORDS)                 *   FILE 948
//*                                                                 *   FILE 948
//*     This REXX reads the unloaded dataset written from the       *   FILE 948
//*     standard program DFH$MOLS which prints SMF110 CICS          *   FILE 948
//*     performance records.                                        *   FILE 948
//*                                                                 *   FILE 948
//*     The output of DFH$MOLS unfortunately is not easy for        *   FILE 948
//*     analysis.                                                   *   FILE 948
//*                                                                 *   FILE 948
//*     This REXX provide a CSV dataset (I like Excel), with        *   FILE 948
//*     Transaction ID, elapsed and CPU time associated with        *   FILE 948
//*     the number of DB2 requests. This is useful to have          *   FILE 948
//*     quickly a performance indicator of your information         *   FILE 948
//*     system to compare (which is mainly CICS and DB2 ...).       *   FILE 948
//*     As SMF110 includes DB2 time, all your consumption is        *   FILE 948
//*     here.                                                       *   FILE 948
//*                                                                 *   FILE 948
//*     More detailed than SMF30                                    *   FILE 948
//*                                                                 *   FILE 948
//*     More convenient than SMF101 (in my shop SMF101 is not       *   FILE 948
//*     collected for CICS transactions because it is really        *   FILE 948
//*     huge)                                                       *   FILE 948
//*                                                                 *   FILE 948
//*     Prereq:  Execute DFHMNDUP then DFH$MOLS with the            *   FILE 948
//*              UNLOAD option                                      *   FILE 948
//*                                                                 *   FILE 948
//*     S100CSV - REXX TO CREATE A CSV DATASET FROM SMF100          *   FILE 948
//*                      (DB2 STATISTICS RECORDS)                   *   FILE 948
//*     This REXX provides a sample of DB2 statistics fields,you    *   FILE 948
//*     can use it as a basis to expand its capability              *   FILE 948
//*                                                                 *   FILE 948
//*     S101CSV - REXX TO CREATE A CSV DATASET FROM SMF101          *   FILE 948
//*                      (DB2 ACCOUNTING RECORDS)                   *   FILE 948
//*     This REXX providesa sample of DB2 accountings fields,you    *   FILE 948
//*     can use it as a basis to expand its capability              *   FILE 948
//*                                                                 *   FILE 948

```
