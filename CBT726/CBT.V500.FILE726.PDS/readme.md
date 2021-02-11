
## @FILE726.txt
```
//***FILE 726 is from Ted MacNeil, and contains a REXX exec to      *   FILE 726
//*           generate DEFINE statements for VSAM files, directly   *   FILE 726
//*           from the file itself.  Details are explained below.   *   FILE 726
//*                                                                 *   FILE 726
//*     This code either displays a VSAM entry or writes the        *   FILE 726
//*     IDCAMS control statement needed to define a VSAM file.      *   FILE 726
//*     (MUST run under ISPF.)                                      *   FILE 726
//*                                                                 *   FILE 726
//*     From ISPF 3.4, type VC3 next to a VSAM data set             *   FILE 726
//*                                                                 *   FILE 726
//*     Further modified by Philippe Simon.  Please see members     *   FILE 726
//*     VCP and VCP$$ for his version and explanation thereof.      *   FILE 726
//*                                                                 *   FILE 726
//*     email for Philippe Simon:  philippe_simon_55@yahoo.fr       *   FILE 726
//*                                                                 *   FILE 726
//*     Originally Written by Jim Connelley.  Jim's version is      *   FILE 726
//*     included here as member VC.                                 *   FILE 726
//*                                                                 *   FILE 726
//*     No copyright.                                               *   FILE 726
//*     If you want to, send your enhancements to                   *   FILE 726
//*                                                                 *   FILE 726
//*             email:  tedmacneil@bell.blackberry.net              *   FILE 726
//*                                                                 *   FILE 726
//*     Reason for this REXX:                                       *   FILE 726
//*             I needed a method to clean up our old               *   FILE 726
//*             VSAM with the keywords: REPLICATE, IMBED            *   FILE 726
//*             and KEYRANGE. This was the fastest way.             *   FILE 726
//*             Those parameters are caught but not                 *   FILE 726
//*             written to control cards.                           *   FILE 726
//*             I also added a few lines to do a:                   *   FILE 726
//*             DELETE ------ PURGE at the front                    *   FILE 726
//*             (Optional)                                          *   FILE 726
//*                                                                 *   FILE 726
//*     There are bugs, such as handling multi-volume files, but    *   FILE 726
//*     that's where YOU come in.                                   *   FILE 726
//*     (-- Ted MacNEIL -- I believe I fixed this bug, but I did    *   FILE 726
//*                        not have any multi-volumes to test       *   FILE 726
//*                        with.)                                   *   FILE 726
//*                                                                 *   FILE 726
//*     (-- The dependency on STEMVIEW was removed to either write  *   FILE 726
//*      -- out to a file or stay inside a loop)                    *   FILE 726
//*                                                                 *   FILE 726
//*   Syntax:                                                       *   FILE 726
//*                                                                 *   FILE 726
//*     %VC3 VSAMDSN pds member DELETE                              *   FILE 726
//*                                                                 *   FILE 726
//*       VSAMDSN -- the VSAM FILE you wish to CLONE                *   FILE 726
//*                  (if you specify quotes, they are removed)      *   FILE 726
//*                                                                 *   FILE 726
//*       pds     -- where to output the control cards (Optional)   *   FILE 726
//*                - default: <userid>.VSAM.CONTROL.CARDS           *   FILE 726
//*                                                                 *   FILE 726
//*       member  -- the member name used to output the statements  *   FILE 726
//*                  (Optional)                                     *   FILE 726
//*                                                                 *   FILE 726
//*       DELETE  -- Insert DELETE <entry> PURGE                    *   FILE 726
//*               -- (Optional)                                     *   FILE 726
//*                                                                 *   FILE 726
//*     NOTE: 1. if PDS does not exist, this outputs to the screen  *   FILE 726
//*                                                                 *   FILE 726
//*           2. The only entry types supported are:                *   FILE 726
//*              ignored and only the DEFINE ALIAS ... RELATE       *   FILE 726
//*              will be output. There is not enough information    *   FILE 726
//*              in the LISTCAT output to rebuild the catalogue.    *   FILE 726
//*                                                                 *   FILE 726
```

