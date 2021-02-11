
## @FILE676.txt
```
//***FILE 676 contains updated batch utilities, VPS EXITS, and      *   FILE 676
//*           code, updated to work in z/OS.  This file is from     *   FILE 676
//*           Jim Marshall.                                         *   FILE 676
//*                                                                 *   FILE 676
//*           Jim's current address is:                             *   FILE 676
//*                                                                 *   FILE 676
//*                 Jim Marshall                                    *   FILE 676
//*                 Office of Personnel Management                  *   FILE 676
//*                 CIO/WTC - Room BH04                             *   FILE 676
//*                 1900 E Street NW                                *   FILE 676
//*                 Washington DC   20415-0001                      *   FILE 676
//*                 w - 202-606-1261                                *   FILE 676
//*                 f - 202-606-2092                                *   FILE 676
//*                 Jim.Marshall@opm.gov                            *   FILE 676
//*                                                                 *   FILE 676
//*   Member $$ZDOC now replaced by member @FILEnnn.  (SBG - 08/03) *   FILE 676
//*                                                                 *   FILE 676
//*       RELEASE 01  -  May 2004                                   *   FILE 676
//*                                                                 *   FILE 676
//*       SUMMARY OF THE MODULES CONTAINED.                         *   FILE 676
//*                                                                 *   FILE 676
//*       Code     REL          DESCRIPTION                         *   FILE 676
//*                                                                 *   FILE 676
//*       GDGCPY   1.0  GDGCOPY utility found in File 482.          *   FILE 676
//*                     Changed code from copying all GDG's found   *   FILE 676
//*                     to only copy the oldest one.  Customers     *   FILE 676
//*                     wanted to process only the file as          *   FILE 676
//*                     "FIFO".  Thanks to Eric Bielefeld for the   *   FILE 676
//*                     code he got.  Cleaned up the code, added    *   FILE 676
//*                     documentation for the future.               *   FILE 676
//*                                                                 *   FILE 676
//*       OPMIUE01 1.0  VPS EXIT01 which will simulate              *   FILE 676
//*                     overstriking when an application codes a    *   FILE 676
//*                     "+" carriage control character on Laser     *   FILE 676
//*                     printers. This EXIT  used only for those    *   FILE 676
//*                     printers needing it. The EXIT is            *   FILE 676
//*                     scheduled for every print line. Thanks to   *   FILE 676
//*                     LRS for having it in their closet.          *   FILE 676
//*                                                                 *   FILE 676
//*       OPMSUE08 1.0  VPS EXIT08 for ERROR Retry of SNA and IP    *   FILE 676
//*                     printers. I expanded the number of IP       *   FILE 676
//*                     error codes handled and adjusted the        *   FILE 676
//*                     times. It will retry for many times as      *   FILE 676
//*                     it's the nature of the beast.               *   FILE 676
//*                                                                 *   FILE 676
//*       OPMSUX14 1.0  VPS EXIT14 expanded by me to perform many   *   FILE 676
//*                     needed functions to be able to convert      *   FILE 676
//*                     absolutely tranparent:                      *   FILE 676
//*                                                                 *   FILE 676
//*                     1) Convert from IBM's InfoPrint where       *   FILE 676
//*                        the module name is specified in the      *   FILE 676
//*                        "PRTOPTNS" field of an OUTPUT statement. *   FILE 676
//*                                                                 *   FILE 676
//*                     2) Convert from another implemenation of    *   FILE 676
//*                        VPS where WRITER name was used.          *   FILE 676
//*                                                                 *   FILE 676
//*                     3) Implement FORM name as the preferred     *   FILE 676
//*                        way of specifing how the HP printers     *   FILE 676
//*                        will print.                              *   FILE 676
//*                                                                 *   FILE 676
//*                     4) "Wire in" a check (BLDL) for the name    *   FILE 676
//*                        used to get the FORMAT module of         *   FILE 676
//*                        Postscript or PCL commands.  If the      *   FILE 676
//*                        module is not found substitute SSTD as   *   FILE 676
//*                        the one.                                 *   FILE 676
//*                                                                 *   FILE 676
```

