
## $$$DOC.txt
```
Note for GBHABEND.  01/16/95

This is a program that I've used over the years, to produce any
conceivable abend code, system or user.  The author is Gordon Hampton.
Gordon has included a large collection of macros inline, some of which
he uses in the program.  However, the program is basically very simple,
and is a frontend to the ABEND macro.

Gordon used to use this program to follow ABENDAID from release to
release, to see how they were improving.  One of my previous shops
used it to stop VSAM jobstreams which produced a condition code of
12 instead of abending.  After the IDCAMS step produced its code of 12,
a jobstep with this program produced the necessary user abend under
"cond" control, so the jobstream would not continue in error.

Please direct inquiries to:

        Sam Golob    P.O. Box 906     Tallman, NY 10982-0906
                         sbgolob@attglobal.net




        NaSPA  414-768-8000   7044 S. 13th Street
                              Oak Creek, WI 53154-1429


I'll refer your inquiries to Gordon.  Good luck.

```

