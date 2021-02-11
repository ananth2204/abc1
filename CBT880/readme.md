```
//***FILE 880 is from Miklos Szigetvari, and contains a product     *   FILE 880
//*           called MVSDSSN, which is an extension of ADRDSSU,     *   FILE 880
//*           and which is used to manage the dumps in a network.   *   FILE 880
//*                                                                 *   FILE 880
//*           email:   miklos.szigetvari@isis-papyrus.com           *   FILE 880
//*                                                                 *   FILE 880
//*     Full documentation for this product is contained, as a      *   FILE 880
//*     PDF file, in member #DOCPDF.                                *   FILE 880
//*                                                                 *   FILE 880
//*     Introduction                                                *   FILE 880
//*                                                                 *   FILE 880
//*     The MVSDSSN is an extension of the standard ADRDSSU         *   FILE 880
//*     utility, to manage the dumps in the network.  We have       *   FILE 880
//*     here (ISIS Information System) two very old tape units,     *   FILE 880
//*     but "nearly" unlimited storage capacity on the local        *   FILE 880
//*     network.  We extended the ADRDSSU utility via UIM (User     *   FILE 880
//*     Interaction Module) exits to write dumps to HFS             *   FILE 880
//*     (Hierarchical File System) files, and store the dump        *   FILE 880
//*     information in a DB2 database.  This modification is        *   FILE 880
//*     running here for several years, maybe smaller shops can     *   FILE 880
//*     use this.  A large part of the modification was written     *   FILE 880
//*     in C/C++, we provide the complete source code, and the      *   FILE 880
//*     necessary definitions for DB2.  The code uses the open      *   FILE 880
//*     source "zlib" general purpose compress library,             *   FILE 880
//*     Copyright (C) 1995-2002 Jean-loup Gailly and Mark           *   FILE 880
//*     Adler.                                                      *   FILE 880
//*                                                                 *   FILE 880
//*     Miklos Szigetvari  November 2012                            *   FILE 880
//*                                                                 *   FILE 880

```
