```
//***FILE 779 is from Bill Bass, and contains a very clever COBOL   *   FILE 779
//*           program which looks at a job in SDSF and performs     *   FILE 779
//*           symbolic substitution from reading the symbolic       *   FILE 779
//*           substitutions that are shown in SDSF, which were      *   FILE 779
//*           performed by the JCL converter and interpreter.       *   FILE 779
//*                                                                 *   FILE 779
//*           email:  "Bass, Walter W" <bill_bass@uhc.com>          *   FILE 779
//*                                                                 *   FILE 779
//*     Further explanation:                                        *   FILE 779
//*                                                                 *   FILE 779
//*=================================================================*   FILE 779
//*                                                                 *   FILE 779
//*                     HOW-TO Guide for SYMBSUB                    *   FILE 779
//*                               with                              *   FILE 779
//*                       JCL Symbolic Variable                     *   FILE 779
//*                          Include Modules                        *   FILE 779
//*                                                                 *   FILE 779
//*=================================================================*   FILE 779
//*                         What is SYMBSUB?                        *   FILE 779
//*=================================================================*   FILE 779
//*                                                                 *   FILE 779
//* SYMBSUB is a tool that reads in 80 column card files and        *   FILE 779
//* performs symbolic variable substitution using the values of     *   FILE 779
//* the symbols from the JCL, then writes the cards back out.       *   FILE 779
//* Each input DD can be either instream data, a single sequential  *   FILE 779
//* file, a single PDS member or a concatenated list of PDS         *   FILE 779
//* libraries.  Each output DD can be either a single sequential    *   FILE 779
//* file, a single PDS member, or a PDS library.                    *   FILE 779
//*                                                                 *   FILE 779
//* What makes SYMBSUB unique from other tools of this type that    *   FILE 779
//* have come before it, is that it retrieves the values of the     *   FILE 779
//* symbols from the JCL on its own.  All you have to do is         *   FILE 779
//* provide it with one or more input dd cards and matching output  *   FILE 779
//* dd cards.  It will automatically find your input files, read    *   FILE 779
//* them, substitute the symbols with the values from the JCL and   *   FILE 779
//* write the modified cards out to the appropriate output files.   *   FILE 779
//*                                                                 *   FILE 779
//*=================================================================*   FILE 779
//*                        How do I use SYMBSUB?                    *   FILE 779
//*=================================================================*   FILE 779
//*                                                                 *   FILE 779
//* To use SYMBSUB, you provide it with input and output DD cards   *   FILE 779
//* that it finds and processes.  These can be of two types:        *   FILE 779
//*   1) Single file input/output pairs.                            *   FILE 779
//*   2) Multiple PDS member input/output libraries and a member    *   FILE 779
//*      selection list (wild carded member lists are supported).   *   FILE 779
//*      These are the wild characters permitted:                   *   FILE 779
//*        "*" = match zero or more of any characters.              *   FILE 779
//*        "?" = match any one single character.                    *   FILE 779
//*        "!" = match one upper case alphabet letter ("A" - "Z").  *   FILE 779
//*        "%" = match one numeric digit ("0" - "9").               *   FILE 779
//*        "~" = match one special character ("@", "#" or "$").     *   FILE 779
//*                                                                 *   FILE 779
//* One execution of SYMBSUB can have multiple occurances of type 1 *   FILE 779
//* and/or type 2 input/output sets of DD cards.                    *   FILE 779
//*                                                                 *   FILE 779
//* The easiest way to explain using SYMBSUB is to show examples.   *   FILE 779
//* Please see member $INTRO01 in this pds.....                     *   FILE 779
//*                                                                 *   FILE 779
//*=================================================================*   FILE 779
//*          How does SYMBSUB get the values of the symbols?        *   FILE 779
//*=================================================================*   FILE 779
//*                                                                 *   FILE 779
//* SYMBSUB invokes SDSF to "print" the JESJCL listing to a         *   FILE 779
//* dataset.  This is the same listing you can view in SDSF if you  *   FILE 779
//* view the JESJCL of an executing batch job.  SYMBSUB then reads  *   FILE 779
//* this dataset and parses the JCL to find the values of the       *   FILE 779
//* symbols.                                                        *   FILE 779
//*                                                                 *   FILE 779
//* SYMBSUB also has several "BUILTIN" symbols that are available   *   FILE 779
//* for substitution even when they are not defined within the JCL. *   FILE 779
//*                                                                 *   FILE 779
//*   &SYSUID                                                       *   FILE 779
//*   &JOBNAME                                                      *   FILE 779
//*   Current date and time in several formats                      *   FILE 779
//*   Century, Year, Mon, Day, Hour, Min, Sec, etc. individually    *   FILE 779
//*   Day of Week - number, full name and abbreviated name,         *   FILE 779
//*   Month - full name and abbreviated name                        *   FILE 779
//*                                                                 *   FILE 779
//* Each execution of SYMBSUB displays a complete list of all of    *   FILE 779
//* the symbols that were available for that run, including the     *   FILE 779
//* builtin ones.                                                   *   FILE 779
//*                                                                 *   FILE 779
//* You can also pass values via the parm and they will override    *   FILE 779
//* the values found in the JCL, but this is rarely needed and      *   FILE 779
//* recommended only for special situations.                        *   FILE 779
//*                                                                 *   FILE 779
//*=================================================================*   FILE 779
//*     "Special Situations"?  You sound like a politician ...      *   FILE 779
//*=================================================================*   FILE 779
//*                                                                 *   FILE 779
//* SYMBSUB is aware of which step or procstep it is executing      *   FILE 779
//* within and keeps track of the changes that take place to all of *   FILE 779
//* the symbolic variables in the JCL.  Due to limitations in the   *   FILE 779
//* way the JCL is presented in the JESJCL listing, there is one    *   FILE 779
//* rare situation where SYMBSUB may have a problem because it      *   FILE 779
//* cannot correctly determine the value of a symbol.               *   FILE 779
//*                                                                 *   FILE 779
//* That situation is when all of the following are true:           *   FILE 779
//*   1) The job executes a nested proc (i.e. a proc calls a proc). *   FILE 779
//*   2) Symbol values are changed within the nested proc or within *   FILE 779
//*      the calling proc after the nested proc.                    *   FILE 779
//*   3) SYMBSUB is executed within the nested proc or within the   *   FILE 779
//*      calling proc after the nested proc.                        *   FILE 779
//*   4) SYMBSUB needs to use one of those specific changed symbols *   FILE 779
//*      in a substitution variable assignment.                     *   FILE 779
//*                                                                 *   FILE 779
//* Complicated?  Yep, but you don't need to figure out if that     *   FILE 779
//* happens in your job, SYMBSUB will tell you, and it depends on   *   FILE 779
//* the structure of the JCL, not the current values of the         *   FILE 779
//* symbols.  This means you'll find out about it the first time    *   FILE 779
//* you test the job after making any JCL or PROC changes.          *   FILE 779
//*                                                                 *   FILE 779
//*=================================================================*   FILE 779
//*          What if I encounter this "Special Situation"?          *   FILE 779
//*=================================================================*   FILE 779
//*                                                                 *   FILE 779
//* If this does happen, SYMBSUB will issue a very detailed error   *   FILE 779
//* message and give a return code of 8.  It will tell you exactly  *   FILE 779
//* which symbols it encountered the problem on and what to do to   *   FILE 779
//* work around the problem.  The preferred solution would be to    *   FILE 779
//* change the job structure so that the SYMBSUB is executed        *   FILE 779
//* before the nested proc or to not use nested procs.  Obviously   *   FILE 779
//* this may not always be possible.  A second possible fix would   *   FILE 779
//* be to avoid changing the value of the symbolic variable within  *   FILE 779
//* the nested proc or after the beginning of the nested proc.      *   FILE 779
//* Again this may not always be possible.  The last alternative    *   FILE 779
//* will always work but is not preferred, and that is to pass the  *   FILE 779
//* specific symbols needed to SYMBSUB on the parm.  This           *   FILE 779
//* alternative will be explained in the error message and the      *   FILE 779
//* specific text needed for the parm string will even be provided  *   FILE 779
//* in the message.  It will typically be something similar to the  *   FILE 779
//* following:                                                      *   FILE 779
//*                                                                 *   FILE 779
//*     PARM=('SOMEVAR=&SOMEVAR')                                   *   FILE 779
//*                                                                 *   FILE 779
//* Where SOMEVAR would be the name of the actual symbolic          *   FILE 779
//* variable that the problem was encountered on.  This would       *   FILE 779
//* cause the actual value to be substituted by the JCL             *   FILE 779
//* interpreter and passed in through the PARM, thus overriding     *   FILE 779
//* what SYMBSUB encounters while parsing the JESJCL.               *   FILE 779
//*                                                                 *   FILE 779
//*=================================================================*   FILE 779
//*         How does SYMBSUB find my input and output dd cards?     *   FILE 779
//*=================================================================*   FILE 779
//*                                                                 *   FILE 779
//* SYMBSUB dynamically searches through the MVS TIOT entries to    *   FILE 779
//* find the allocated DD names at the time it is executing.  It    *   FILE 779
//* specifically looks for any DD cards with names beginning with   *   FILE 779
//* "CNTL" or "LIBR" and ending with "I" or "IN" (for input), "O",  *   FILE 779
//* "OT" or "OUT" (for output) and "M" (for member selection        *   FILE 779
//* lists).  Any DD cards it finds that fit this format are         *   FILE 779
//* assumed to be intended as input or output cards for             *   FILE 779
//* processing.  The input and output DD cards are matched to each  *   FILE 779
//* other by the characters found between the prefix ("CNTL") and   *   FILE 779
//* the suffix ("I", "IN", "O", "OT" or "OUT").  SYMBSUB can        *   FILE 779
//* handle up to 100 DD cards.                                      *   FILE 779
//*                                                                 *   FILE 779
//* If an input DD card is found for which no matching output DD    *   FILE 779
//* card can be found, SYMBSUB will issue a error message and       *   FILE 779
//* return code 12, and that input DD card will be ignored.         *   FILE 779
//*                                                                 *   FILE 779
//* If an output DD card is found for which no matching input DD    *   FILE 779
//* card can be found, SYMBSUB will issue a warning message and     *   FILE 779
//* return code 4, and that output DD card will be ignored.         *   FILE 779
//*                                                                 *   FILE 779
//* If more than one input or output DD card is found with the      *   FILE 779
//* same characters between the prefix and the suffix, SYMBSUB      *   FILE 779
//* will issue an error message and return code 12 and only the     *   FILE 779
//* first such DD card found will be used.                          *   FILE 779
//*                                                                 *   FILE 779

```
