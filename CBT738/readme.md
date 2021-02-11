```
//***FILE 738 is from Terry Miller and contains a facility to       *   FILE 738
//*           reorganize VSAM clusters without having to code any   *   FILE 738
//*           of the IDCAMS DEFINE statements.  The facility        *   FILE 738
//*           parses out the Re-allocation information from IDCAMS  *   FILE 738
//*           reports and reallocates and EXPORTS/IMPORTS the data  *   FILE 738
//*           to reorg the file.  The facility also reallocates and *   FILE 738
//*           re-populates any alternate indexes associated to the  *   FILE 738
//*           base cluster and rebuilds any Racf Discrete profiles  *   FILE 738
//*           which existed before the reorganization.              *   FILE 738
//*                                                                 *   FILE 738
//*                                                                 *   FILE 738
//*           email:  tkmille@conocophillips.com                    *   FILE 738
//*                                                                 *   FILE 738
//*           Last Revision: 06/02/2009 V01.02.02                   *   FILE 738
//*                                                                 *   FILE 738
//*> * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * <*   FILE 738
//*                                                                 *   FILE 738
//*                     Important note  !!!!                        *   FILE 738
//*                     --------- ----  ----                        *   FILE 738
//*                                                                 *   FILE 738
//*  This facility assumes the use of IBM'S RACF product as a       *   FILE 738
//*  security product.                                              *   FILE 738
//*  If your installation uses another security product, this       *   FILE 738
//*  facility will need to be modified to work.  The RACF security  *   FILE 738
//*  is used only to re-create RACF DISCRETE DATASET CLASS profiles.*   FILE 738
//*  If discrete (DISCRET TO A VOLSER) profiles are not being used, *   FILE 738
//*  then the following nine steps can be omitted frm the REORG jcl *   FILE 738
//*  stream in skeleton member "REORGVSS":                          *   FILE 738
//*                                                                 *   FILE 738
//*    GETRACF, CHK500, ABEND500, BLDRACF, CHK700, ABEND700,        *   FILE 738
//*    GENPROF, CHK750, ABEND750.                                   *   FILE 738
//*                                                                 *   FILE 738
//*  Also, the following REXX exec can be discarded:  REORGVS4      *   FILE 738
//*                                                                 *   FILE 738

```
