```
//***FILE 993 is from Robert Sample and contains a COBOL program    *   FILE 993
//*           to read many types of SMF records.  This is unusual   *   FILE 993
//*           in that COBOL is not usually the language of choice   *   FILE 993
//*           for this purpose, but the program works well.         *   FILE 993
//*                                                                 *   FILE 993
//*           email:  rsample636@gmail.com                          *   FILE 993
//*                                                                 *   FILE 993
//*     Program Description:                                        *   FILE 993
//*                                                                 *   FILE 993
//*     This program started in 2011 as a concept program to        *   FILE 993
//*     determine if COBOL could process SMF records.  It turns     *   FILE 993
//*     out that as of July 2019, the only data that COBOL          *   FILE 993
//*     cannot handle is the extended STCKE format 16-byte time     *   FILE 993
//*     used in the type 126 extended SMF record.  Conversion of    *   FILE 993
//*     STCKE values is done by an Assembler program CONVETOD.      *   FILE 993
//*     I could probably write COBOL to handle this field, but      *   FILE 993
//*     why bother when STCKCONV is available?                      *   FILE 993
//*                                                                 *   FILE 993
//*     There are comments in the code talking about which          *   FILE 993
//*     record types can be processed.  The DB2 record types 100    *   FILE 993
//*     and 101 have been placed into working storage but 102       *   FILE 993
//*     has not been into this program (yet).  I have not been      *   FILE 993
//*     able to write or test the DISPLAY logic for these           *   FILE 993
//*     records as I don't have access to any DB2 system on a       *   FILE 993
//*     mainframe.                                                  *   FILE 993
//*                                                                 *   FILE 993
//*     If the CICS records are compressed, they need to be         *   FILE 993
//*     uncompressed with DFH$MOLT before running them into this    *   FILE 993
//*     program as I don't have the decompression algorithm         *   FILE 993
//*     implemented at this time.  My understanding is that DB2     *   FILE 993
//*     also compresses records, so they would also need to be      *   FILE 993
//*     decompressed before processing by READSMF.                  *   FILE 993
//*                                                                 *   FILE 993
//*     Also, please note that this program is based upon my        *   FILE 993
//*     understanding of the SMF record types as presented in       *   FILE 993
//*     the System Management Facility manual for the various       *   FILE 993
//*     releases of z/OS.  Any errors in interpretation are         *   FILE 993
//*     mine.  And I haven't seen any examples of the relocation    *   FILE 993
//*     records in any SMF records so far, so I cannot state        *   FILE 993
//*     that my interpretation of them is correct.                  *   FILE 993
//*                                                                 *   FILE 993
//*     To run this program, assemble CONVETOD into a load          *   FILE 993
//*     library (either PDS or PDSE should work).  Job CONVEASM     *   FILE 993
//*     should work for this.  Then compile READSMF using           *   FILE 993
//*     READSMFC job.  I route the compiler output to a data set    *   FILE 993
//*     as it runs about 1,090,000 lines right now.  The            *   FILE 993
//*     execution JCL is in READSMFR or READSMFX -- to show         *   FILE 993
//*     different options for displaying data.  Update the job      *   FILE 993
//*     to point to your unloaded SMF data (if you use log          *   FILE 993
//*     stream use IFASMFDL to dump the SMF data into a             *   FILE 993
//*     VB,32756,32760 data set) and change the parameters to       *   FILE 993
//*     display the desired record type.  When using the display    *   FILE 993
//*     record type function, you may need to route SYSOUT to a     *   FILE 993
//*     data set since the DISPLAY output can be very lengthy.      *   FILE 993
//*     Some of the record types can generate multiple thousands    *   FILE 993
//*     of lines of display for each input record since one         *   FILE 993
//*     field is displayed per output line.  The load module is     *   FILE 993
//*     X'3D5B5C' bytes or 4,021,084 in decimal.                    *   FILE 993
//*                                                                 *   FILE 993
//*     Also, when you look through the source code you will        *   FILE 993
//*     find occasional DEBUG DISPLAY statements, generally         *   FILE 993
//*     commented out.  When debugging I'll put in extra DISPLAY    *   FILE 993
//*     statements and when the issue is resolved I'll comment      *   FILE 993
//*     them out since it is entirely possible that I'll need to    *   FILE 993
//*     revisit that section of code as testing proceeds.           *   FILE 993
//*                                                                 *   FILE 993

```
