
## @FILE867.txt
```
//***FILE 867 is from somitcw and contains programs to help in      *   FILE 867
//*           transporting data files from one system to another.   *   FILE 867
//*                                                                 *   FILE 867
//*               email:  somitcw@yahoo.com                         *   FILE 867
//*                                                                 *   FILE 867
//*    Programs:                                                    *   FILE 867
//*                                                                 *   FILE 867
//*    RDW2VB   - Program which supplies Block Descriptor Words     *   FILE 867
//*               (BDW's) to a dataset that was FTP'ed from         *   FILE 867
//*               somewhere else, to properly reconstruct a VB      *   FILE 867
//*               file from a VB file that was FTP'ed to a PC       *   FILE 867
//*               previously.                                       *   FILE 867
//*                                                                 *   FILE 867
//*               The problem is:  When you ftp a RECFM=VB          *   FILE 867
//*               data set to a PC as binary the default is         *   FILE 867
//*               to remove any record indicator.  If               *   FILE 867
//*               locsite rdw or quote site rdw is                  *   FILE 867
//*               specified then the RDW is saved but there         *   FILE 867
//*               is no standard way to return the data to          *   FILE 867
//*               the main frame and reconstruct a RECFM=VB         *   FILE 867
//*               data set.                                         *   FILE 867
//*                                                                 *   FILE 867
//*               This program will copy the binary data            *   FILE 867
//*               with RDWs to a RECFM=VB data set.                 *   FILE 867
//*                                                                 *   FILE 867
//*    RECU2AWS - This program copies the blocks of a               *   FILE 867
//*               sequential data set or member to an AWSTAPE       *   FILE 867
//*               image data set.  It pretends that the input       *   FILE 867
//*               is RECFM=U whether it is or not to use QSAM       *   FILE 867
//*               to read blocks of data instead of logical         *   FILE 867
//*               records.                                          *   FILE 867
//*                                                                 *   FILE 867
//*               Note: RECU2AWS may be replaced with a program     *   FILE 867
//*               DSET2AWS that uses BSAM for input as soon as      *   FILE 867
//*               I have time.                                      *   FILE 867
//*                                                                 *   FILE 867
//*               Override note: I have not written DSET2AWS        *   FILE 867
//*               but changed this program to also handle           *   FILE 867
//*               RECFM=FB and RECFM=VB input.                      *   FILE 867
//*                                                                 *   FILE 867
//*               Warning: this program is for sequential data,     *   FILE 867
//*               not a PDS.  Trying to use it on a PDS would       *   FILE 867
//*               only get the directory.                           *   FILE 867
//*                                                                 *   FILE 867
```

