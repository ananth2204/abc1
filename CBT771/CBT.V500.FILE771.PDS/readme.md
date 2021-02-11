
## @FILE771.txt
```
//***FILE 771 is from Karl-Heinz Doppelfeld and contains an         *   FILE 771
//*           ICSF (cryptographic service facility) monitor that    *   FILE 771
//*           is written in REXX.  A short description is found     *   FILE 771
//*           below.  Necessary panels are imbedded in the REXX     *   FILE 771
//*           code.                                                 *   FILE 771
//*                                                                 *   FILE 771
//*     email:  Karl-Heinz.Doppelfeld@Sparkassen-Informatik.de      *   FILE 771
//*                                                                 *   FILE 771
//*     Utility to display ICSF Statistics.                         *   FILE 771
//*                                                                 *   FILE 771
//*  History:                                                       *   FILE 771
//*  lvl 001 : base version                             01.01.2002  *   FILE 771
//*  lvl 002 : update to new CSFDACC with 10 services   14.05.2008  *   FILE 771
//*            some doc updates and implementation of               *   FILE 771
//*            LUSER to show all users which are using              *   FILE 771
//*            crypto operations.                                   *   FILE 771
//*                                                                 *   FILE 771
//*     More description found in SYS1.MODGEN member CSFCCVT        *   FILE 771
//*     and CSFDACC.                                                *   FILE 771
//*                                                                 *   FILE 771
//*     CCVT:                                                       *   FILE 771
//*     The CCVT is the base control block for ICSF/MVS. The        *   FILE 771
//*     CCVT contains addresses of common areas for use by          *   FILE 771
//*     ICSF/MVS components.  Indicators in the CCVT provide        *   FILE 771
//*     status of ICSF/MVS.                                         *   FILE 771
//*                                                                 *   FILE 771
//*     DACC:                                                       *   FILE 771
//*     The DACC is the base control block for ICSF to collect      *   FILE 771
//*     Performance measurements for RMF to report on. This         *   FILE 771
//*     control block is the programming interface.  The count      *   FILE 771
//*     fields are double-word length.                              *   FILE 771
//*                                                                 *   FILE 771
//*     The following services will have data collected:            *   FILE 771
//*                                                                 *   FILE 771
//*     CSNBENC - Encipher:                                         *   FILE 771
//*     - This will be done for single DES separately.              *   FILE 771
//*       Collect number of service calls, number of bytes of       *   FILE 771
//*       data enciphered, number of CMD instructions used to       *   FILE 771
//*       encipher the data.                                        *   FILE 771
//*     - Double and triple DES will be counted together.           *   FILE 771
//*       collect number of service calls, number of bytes of       *   FILE 771
//*       data enciphered, number of CMD instructions used to       *   FILE 771
//*       encipher the data.                                        *   FILE 771
//*     CSNBDEC - Decipher:                                         *   FILE 771
//*     CSNBDEC - Decipher:                                         *   FILE 771
//*     - This will be done for single DES separately.              *   FILE 771
//*       Collect number of service calls, number of bytes of       *   FILE 771
//*         data deciphered, number of CMD instructions used        *   FILE 771
//*         to decipher the data.                                   *   FILE 771
//*       - Double and triple DES will be counted together.         *   FILE 771
//*         collect number of service calls, number of bytes        *   FILE 771
//*         of data deciphered, number of CMD instructions          *   FILE 771
//*         used to decipher the data.                              *   FILE 771
//*       CSNBMGN - MAC_Generate:                                   *   FILE 771
//*       - Single and varous double key MAC will be                *   FILE 771
//*         gathered together.                                      *   FILE 771
//*         Collect number of service calls, number of              *   FILE 771
//*         bytes of data MACd, number of PCMF instructions.        *   FILE 771
//*       CSNBMVR - MAC_Verify:                                     *   FILE 771
//*       - Single and varous double key MAC will be                *   FILE 771
//*         gathered together.                                      *   FILE 771
//*         Collect number of service calls, number of              *   FILE 771
//*         bytes of data MACd, number of PCMF instructions.        *   FILE 771
//*       CSNBOWH - One_Way_Hash:                                   *   FILE 771
//*       - For SHA-1,                                              *   FILE 771
//*         Collect number of service calls, number of              *   FILE 771
//*         bytes of data hashed, number of PCMF instructions       *   FILE 771
//*         for SHA-1.                                              *   FILE 771
//*         CSNBPTR - PIN_Translate:                                *   FILE 771
//*         - Collect number of service calls only.                 *   FILE 771
//*         CSNBPVR - PIN_Verify:                                   *   FILE 771
//*         - Collect number of service calls only.                 *   FILE 771
//*                                                                 *   FILE 771
//*     Author: Karl-Heinz Doppelfeld                               *   FILE 771
//*        Karl-Heinz.Doppelfeld§Sparkassen-Informatik.de           *   FILE 771
//*                                                                 *   FILE 771
```

