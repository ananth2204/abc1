```
//***FILE 972 is from Kenneth Tomiak and contains an EDIT macro     *   FILE 972
//*           that mimics the ISPF 'MODEL' command, but GENIE       *   FILE 972
//*           is extensible and serves up WISHes from user          *   FILE 972
//*           created templates.                                    *   FILE 972
//*                                                                 *   FILE 972
//*           If you need help information from a selected group    *   FILE 972
//*           of manuals, you can pull the information into your    *   FILE 972
//*           current ISPF EDIT session.                            *   FILE 972
//*                                                                 *   FILE 972
//*             Released 2018-02-25                                 *   FILE 972
//*                                                                 *   FILE 972
//*           Latest version:  02.24    (Also see CBT File 978)     *   FILE 972
//*                                                                 *   FILE 972
//*    ----------------------------------------------------------   *   FILE 972
//*                                                                 *   FILE 972
//*    Unfortunately, Ken has passed on, but he was working up      *   FILE 972
//*    until practically the last minute.  We have tried to         *   FILE 972
//*    preserve this work.  So to see it, this is what to do:       *   FILE 972
//*                                                                 *   FILE 972
//*    For a DFDSSdss backup of everything Ken Tomiak was working   *   FILE 972
//*    on, download from the URL:                                   *   FILE 972
//*                                                                 *   FILE 972
//*    http://www.cbttape.org/ftp/collections/ktomiak.zip           *   FILE 972
//*                                                                 *   FILE 972
//*    and for restore instruction for this file, download the JCL  *   FILE 972
//*    and other information at:                                    *   FILE 972
//*                                                                 *   FILE 972
//*    http://www.cbttape.org/ftp/collections/ktomiak.restore       *   FILE 972
//*                                                                 *   FILE 972
//*    or see the member $RESTORE in this pds.                      *   FILE 972
//*                                                                 *   FILE 972
//*    ----------------------------------------------------------   *   FILE 972
//*                                                                 *   FILE 972
//*    An updated version of this file was found among Ken's        *   FILE 972
//*    materials, which he left.  This is available temporarily     *   FILE 972
//*    on CBT File 978.  I think there's a lot of improvement       *   FILE 972
//*    there, so it's probably worth installing GENIE from          *   FILE 972
//*    File 978 for now.                                            *   FILE 972
//*                                                                 *   FILE 972
//*    Without promising, I will try and update this file later,    *   FILE 972
//*    with Ken's more recent, unpublished materials, once they've  *   FILE 972
//*    been tested.  Meanwhile, you can get them on CBT File 978,   *   FILE 972
//*    which I'm calling the "beta version" of this file.           *   FILE 972
//*                                                                 *   FILE 972
//*    ----------------------------------------------------------   *   FILE 972
//*                                                                 *   FILE 972
//*           GENIE level 01.23 now contains a full smarter SEARCH  *   FILE 972
//*           that handles line wrapping.                           *   FILE 972
//*                                                                 *   FILE 972
//*           The administrator will create one or more WISHLIST    *   FILE 972
//*           data sets refrenced by the GENIE edit macro that is   *   FILE 972
//*           placed in your SYSEXEC, or SYSPROC, concatenation.    *   FILE 972
//*                                                                 *   FILE 972
//*           The end user (developers) invokes GENIE on the        *   FILE 972
//*           command line and expands a relevant topic and chapter *   FILE 972
//*           to choose an item whose SYNTAX is shown and sample    *   FILE 972
//*           code inserted in the current EDIT session.            *   FILE 972
//*                                                                 *   FILE 972
//*             Released 2018-02-07                                 *   FILE 972
//*                                                                 *   FILE 972
//*              DASM - Data And Storage Management.                *   FILE 972
//*              DFPU - Data Facility Product User Guide.           *   FILE 972
//*              IBMK - IBM Manuals to be used for WISHes.          *   FILE 972
//*              JCLR - JCL Reference Manual.                       *   FILE 972
//*              MITR - z/OS MVS Initialiation and Tuning.          *   FILE 972
//*              PMAU - SMP/E Planning and Migration Assistant.     *   FILE 972
//*              PSFC - Print Services Facility: Customization.     *   FILE 972
//*              REXR - REXX Reference.                             *   FILE 972
//*              RXCP - REXX Compiler Presentation -George Fulk.    *   FILE 972
//*              RXCU - REXX Compiler -User's Guide and Reference.  *   FILE 972
//*              TSAD - Tools And Service Aids.                     *   FILE 972
//*                                                                 *   FILE 972
//*             Released 2018-02-12                                 *   FILE 972
//*                                                                 *   FILE 972
//*              CRDG - CICS Resource Definition Guide              *   FILE 972
//*              KETU - Kenneth Tomiak Utility.                     *   FILE 972
//*                                                                 *   FILE 972
//*             Released 2018-03-22                                 *   FILE 972
//*                                                                 *   FILE 972
//*              AMSC - Access Method Services for Catalogs         *   FILE 972
//*                                                                 *   FILE 972
//*           email:  sbgolob@cbttape.org                           *   FILE 972
//*                                                                 *   FILE 972

```
