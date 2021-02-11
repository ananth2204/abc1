```
//***FILE 949 is an IEHMOVE substitute program called PDSUR, which  *   FILE 949
//*           is more flexible than IEHMOVE, and is much easier to  *   FILE 949
//*           use.  Written in 1973 by Gene Czarcinski, it was      *   FILE 949
//*           recently updated for z/OS disks by a qualified        *   FILE 949
//*           updater.                                              *   FILE 949
//*                                                                 *   FILE 949
//*           I am surprised that this program never made it to     *   FILE 949
//*           the CBT Tape before.                                  *   FILE 949
//*                                                                 *   FILE 949
//*           Corrections were made by Peter Glanzmann, mostly      *   FILE 949
//*           having to do with changing halfword arithmetic        *   FILE 949
//*           to fullword arithmetic.  Older version is PDSUR00.    *   FILE 949
//*                                                                 *   FILE 949
//*           support email:   sbgolob@cbttape.org                  *   FILE 949
//*                                                                 *   FILE 949
//*                            Peter.Glanzmann@bedag.ch             *   FILE 949
//*                                                                 *   FILE 949
//*           A good use for this program is to restore IEHMOVE-    *   FILE 949
//*           unloaded pds'es from old tapes.  But it is good       *   FILE 949
//*           for unloading a pds into IEHMOVE-format quickly,      *   FILE 949
//*           and it can be used as an alternative to XMIT          *   FILE 949
//*           sequentializing of pds'es.  With this program,        *   FILE 949
//*           sequential blocksizes can be any multiple of 80,      *   FILE 949
//*           and they are not restricted to 800 as with IEHMOVE.   *   FILE 949
//*                                                                 *   FILE 949
//*           There is a bit more material included in this file:   *   FILE 949
//*                                                                 *   FILE 949
//*           PDSRUO   - The original PDSRU program before being    *   FILE 949
//*                      updated for modern devices.                *   FILE 949
//*                                                                 *   FILE 949
//*           PDSUR@   - Documentation to explain the various       *   FILE 949
//*           PDSURDOC   uses and applications of PDSUR.            *   FILE 949
//*                                                                 *   FILE 949
//*           PDSURU   - Version of PDSRU where the sequence        *   FILE 949
//*                      numbering of the output dataset is         *   FILE 949
//*                      disabled if your EXEC card has PARM=U.     *   FILE 949
//*                      Resultant output dataset is incompatible   *   FILE 949
//*                      with IEHMOVE, having all x'0000' in the    *   FILE 949
//*                      sequence number field (columns 1 and 2),   *   FILE 949
//*                      but in a case where the output dataset     *   FILE 949
//*                      is part of a JCL data stream, then         *   FILE 949
//*                      "//" and "/*"  (x'6161' or x'615C')        *   FILE 949
//*                      as sequence numbers, will not terminate    *   FILE 949
//*                      the data stream prematurely.               *   FILE 949
//*                                                                 *   FILE 949
//*           In addition: ----                                     *   FILE 949
//*                                                                 *   FILE 949
//*           I have added Gilbert Saint-flour's contribution to    *   FILE 949
//*           this area, which is his program called SYSMOVE.       *   FILE 949
//*           SYSMOVE goes only one way--from a pds to an IEHMOVE-  *   FILE 949
//*           format sequential dataset.  You can use PDSUR to      *   FILE 949
//*           restore a SYSMOVE-created sequential dataset, or      *   FILE 949
//*           you can also use IEHMOVE to restore it.  Both work.   *   FILE 949
//*                                                                 *   FILE 949
//*           SYSMOVE  - Program to produce an IEHMOVE-format       *   FILE 949
//*                      sequential file from a pds.  JCL for       *   FILE 949
//*                      assembly and linkedit is included in       *   FILE 949
//*                      this member.                               *   FILE 949
//*                                                                 *   FILE 949
//*           STRING   - Assembler macro necessary to assemble      *   FILE 949
//*                      SYSMOVE.                                   *   FILE 949
//*                                                                 *   FILE 949
//*           SAMPLE JCL MEMBERS:  - - -  marked with id RUNJCL:    *   FILE 949
//*                                                                 *   FILE 949
//*           PDSURL01 - Reload an IEHMOVE-format file to a PDS     *   FILE 949
//*                      using the PDSUR utility.                   *   FILE 949
//*                                                                 *   FILE 949
//*           PDSURN01 - Unload a PDS to an IEHMOVE-format file     *   FILE 949
//*                      using the PDSUR utility.                   *   FILE 949
//*                                                                 *   FILE 949
//*           IEHMOV01 - Real IEHMOVE JCL to unload a PDS, to       *   FILE 949
//*                      IEHMOVE format, with explanations.         *   FILE 949
//*                                                                 *   FILE 949
//*           IEHMOV02 - Real IEHMOVE JCL to reload a PDS from an   *   FILE 949
//*                      IEHMOVE-format file created by IEHMOVE.    *   FILE 949
//*                                                                 *   FILE 949
//*           IEHMOV03 - Real IEHMOVE JCL to reload a PDS from an   *   FILE 949
//*                      IEHMOVE-format file created by PDSUR.      *   FILE 949
//*                                                                 *   FILE 949
//*           (The formats of PDSUR-unloaded PDS'es and             *   FILE 949
//*            IEHMOVE-unloaded PDS'es were not quite identical,    *   FILE 949
//*            but after restoration with either utility, it        *   FILE 949
//*            doesn't seem to matter, after a preliminary test.    *   FILE 949
//*            You seem to restore the same output file in either   *   FILE 949
//*            case.)                                               *   FILE 949
//*                                                                 *   FILE 949

```
