```
//***FILE 929 is from somitcw and contains a program called         *   FILE 929
//*           REALNAME, which is a REXX function that returns       *   FILE 929
//*           the actual file name of a gdg dataset, or the         *   FILE 929
//*           actual name of an alias in a catalog.                 *   FILE 929
//*                                                                 *   FILE 929
//*           The original version of REALNAME was written by       *   FILE 929
//*           Doug Nadel.                                           *   FILE 929
//*                                                                 *   FILE 929
//*           email:  somitcw@yahoo.com                             *   FILE 929
//*                                                                 *   FILE 929
//*       REALNAME is used to:                                      *   FILE 929
//*                                                                 *   FILE 929
//*       1. Translate an alias in a catalog to a real name.        *   FILE 929
//*          (Which includes finding a usercatalog name from        *   FILE 929
//*          a hlq.)                                                *   FILE 929
//*                                                                 *   FILE 929
//*       2. Resolve a relative Generation Data Set name to an      *   FILE 929
//*          absolute one.                                          *   FILE 929
//*                                                                 *   FILE 929
//*       If the input name is already a real name, it will be      *   FILE 929
//*       returned.                                                 *   FILE 929
//*                                                                 *   FILE 929
//*       If the input name is not cataloged and an absolute        *   FILE 929
//*       Generation Data Set name cannot be calculated within      *   FILE 929
//*       a Generation Data Group, then 'UNKNOWN' will be           *   FILE 929
//*       returned.                                                 *   FILE 929
//*                                                                 *   FILE 929
//*          Sample REXX calls:                                     *   FILE 929
//*                                                                 *   FILE 929
//*       gds = REALNAME(the.gdg.name(+1))                          *   FILE 929
//*                                                                 *   FILE 929
//*       SAY REALNAME(hlq)                                         *   FILE 929
//*                                                                 *   FILE 929

```
