```
//***FILE 666 is from Jay Moseley and contains his random number    *   FILE 666
//*           generator for generating test data, and his           *   FILE 666
//*           implementation of the COMBSORT extended bubble sort   *   FILE 666
//*           algorithm.                                            *   FILE 666
//*                                                                 *   FILE 666
//*           email:     jay@jaymoseley.com                         *   FILE 666
//*           web site:  www.jaymoseley.com                         *   FILE 666
//*                                                                 *   FILE 666
//*     Pseudo-Random Number Generator                              *   FILE 666
//*                                                                 *   FILE 666
//*         (Assembler)  I recently decided to try                  *   FILE 666
//*         consolidating some programs I use to generate test      *   FILE 666
//*         data into a single run unit.  The first hurdle was      *   FILE 666
//*         finding a suitable random number generator that I       *   FILE 666
//*         could implement under MVS 3.8.  Unfortunately, the      *   FILE 666
//*         COBOL compiler we have available to us lacks those      *   FILE 666
//*         handy intrinsic functions, including RANDOM.  I         *   FILE 666
//*         also found that there are not many solutions            *   FILE 666
//*         available in Assembler or COBOL.  And those few I       *   FILE 666
//*         found (well, actually only a couple and they were       *   FILE 666
//*         very old) failed to built very random sets of           *   FILE 666
//*         numbers.  I came up with a subroutine, written in       *   FILE 666
//*         Assembler, based on the Linear Congruential method      *   FILE 666
//*         (described in Knuth, Sedgewick, and in many places      *   FILE 666
//*         on the 'net).  It isn't cryptographic quality, but      *   FILE 666
//*         will do for simulation and ad hoc sets of test          *   FILE 666
//*         numbers.  I also wrote a COBOL program to do some       *   FILE 666
//*         analysis on the generated number sets.  The             *   FILE 666
//*         jobstream contained in member RANDOM will run the       *   FILE 666
//*         analysis program and illustrates how to link the        *   FILE 666
//*         Assembler routine to your own programs.                 *   FILE 666
//*                                                                 *   FILE 666
//*     Comb Sort                                                   *   FILE 666
//*                                                                 *   FILE 666
//*         (COBOL)  The comb sort algorithm is an extended         *   FILE 666
//*         bubble sort that outperforms the basic bubble sort      *   FILE 666
//*         and is very simple to implement.  This program          *   FILE 666
//*         reads in 10,000 records from SYSIN, sorts them, and     *   FILE 666
//*         prints the sort time and sorted records on SYSOUT.      *   FILE 666
//*         Under Hercules the times I saw were around 5/100ths     *   FILE 666
//*         of a second to sort the 10,000 randomly generated       *   FILE 666
//*         test records.  The COBOL source is in member            *   FILE 666
//*         COMBSORT.  (A slightly cleaner implementation with      *   FILE 666
//*         inline perform statements is also included as           *   FILE 666
//*         member COMBSRTC, but of course it will not compile      *   FILE 666
//*         with the MVT compiler).                                 *   FILE 666
//*                                                                 *   FILE 666

```
