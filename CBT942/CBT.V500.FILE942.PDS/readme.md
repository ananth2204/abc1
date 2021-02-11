
## @FILE942.txt
```
//***FILE 942 comes by way of John Kalinich, but is the work of     *   FILE 942
//*           several people.  The cornerstone of this file is      *   FILE 942
//*           the two REXXes called VI (alias VSAM), and VCX,       *   FILE 942
//*           together with their panels, VI#1 and VI#1H.           *   FILE 942
//*                                                                 *   FILE 942
//*           These allow you to find information about VSAM        *   FILE 942
//*           datasets, directly from an ISPF 3.4 panel.            *   FILE 942
//*                                                                 *   FILE 942
//*           VI     -  lists "LISTC-type" information, but         *   FILE 942
//*                     on a panel -- easy to read.                 *   FILE 942
//*                                                                 *   FILE 942
//*           VSAM   -  an alias for VI                             *   FILE 942
//*                                                                 *   FILE 942
//*           VCX    -  generates a DEFINE statement to             *   FILE 942
//*                     recatalog the dataset.  (valuable..!!)      *   FILE 942
//*                                                                 *   FILE 942
//*       Try them.... You'll like them.....!!                      *   FILE 942
//*                                                                 *   FILE 942
//*       In order to get VCX to work properly, you will need       *   FILE 942
//*       a TSO command to clear the screen.  It should be          *   FILE 942
//*       renamed to the name CLEAR, or you can change the name     *   FILE 942
//*       in the VCX exec.  Two of these have been supplied:        *   FILE 942
//*                                                                 *   FILE 942
//*       Members CLEAR and CLEAR$ (program and assembly JCL)       *   FILE 942
//*                                                                 *   FILE 942
//*       Member CLS (another program which does essentially        *   FILE 942
//*           the same thing).                                      *   FILE 942
//*                                                                 *   FILE 942
//*       Two other programs have also been supplied here:          *   FILE 942
//*                                                                 *   FILE 942
//*           LISTCSUM  - A REXX to break LISTC output into         *   FILE 942
//*                       parse-able chunks (also needs "CLEAR")    *   FILE 942
//*                                                                 *   FILE 942
//*           RXDATE    - A REXX subroutine to convert dates        *   FILE 942
//*                       in many ways.                             *   FILE 942
//*                                                                 *   FILE 942
//*           email:  jkalinic@outlook.com                          *   FILE 942
//*                                                                 *   FILE 942
//*           email:  sbgolob@cbttape.org                           *   FILE 942
//*                                                                 *   FILE 942
//*       28 Apr 2020                                               *   FILE 942
//*          - Jim Turner (jim_turner@triserv.com) added            *   FILE 942
//*            additional informational fields for SMS/RLS and      *   FILE 942
//*            made the VI#1 panel scrollable.                      *   FILE 942
//*                                                                 *   FILE 942
```

