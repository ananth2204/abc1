
## @FILE883.txt
```
//***FILE 883 is from Miklos Szigetvari, and contains his package   *   FILE 883
//*           of exits and programs to help manage DFHSM.           *   FILE 883
//*                                                                 *   FILE 883
//*  email:  Miklos Szigetvari <miklos.szigetvari@isis-papyrus.com> *   FILE 883
//*                                                                 *   FILE 883
//*     Introduction                                                *   FILE 883
//*                                                                 *   FILE 883
//*     This MVSHSM pachage is an extension of the Hierarchical     *   FILE 883
//*     Storage Manager (HSM), to manage the secondary migration    *   FILE 883
//*     level data (ML2) on the network.                            *   FILE 883
//*                                                                 *   FILE 883
//*     Here, in the ISIS Papyrus Software, we have 2 very old      *   FILE 883
//*     tape drives, no operators, we are 5 kilometers from the     *   FILE 883
//*     machine location, and we have 500 Gigabyte online           *   FILE 883
//*     storage, but practically "unlimited" storage on the         *   FILE 883
//*     network. We extended the HSM, via standard exits, to        *   FILE 883
//*     store the ML2 data on the network. We have been using       *   FILE 883
//*     this modification since 2005; maybe some other small        *   FILE 883
//*     installations can take advantage of this.                   *   FILE 883
//*                                                                 *   FILE 883
//*     We define an ML2 disk volume, and via the HSM migration     *   FILE 883
//*     exits, we move everything from this volume to a Network     *   FILE 883
//*     File System (NFS) directory. Before a recall, the proper    *   FILE 883
//*     HSM exit moves the requested dataset back to our ML2        *   FILE 883
//*     disk volume, and the HSM can finish the restore.            *   FILE 883
//*                                                                 *   FILE 883
//*     The exit routines are called by the HSM before the          *   FILE 883
//*     proper HSM action. It is good for the "recall", but for     *   FILE 883
//*     the "migrate" we can just move everything from the ML2      *   FILE 883
//*     disk drive to the NFS directory, and the last migrated      *   FILE 883
//*     dataset will reside on the ML2 disk volume.                 *   FILE 883
//*                                                                 *   FILE 883
//*     We are using:                                               *   FILE 883
//*      * MM Second Level Migration Dataset exit                   *   FILE 883
//*      * MD Dataset Migration exit                                *   FILE 883
//*      * RD Recall exit.                                          *   FILE 883
//*                                                                 *   FILE 883
//*     The exit routines were written in C++, we provide the       *   FILE 883
//*     complete source code and a load library. As sample, we      *   FILE 883
//*     modified the HSM installation STARTUP, and we provide       *   FILE 883
//*     also our current, running HSM configuration by ISIS, as     *   FILE 883
//*     it is.                                                      *   FILE 883
//*                                                                 *   FILE 883
//*     Warning                                                     *   FILE 883
//*                                                                 *   FILE 883
//*     This is a limited HSM setup, with some simple               *   FILE 883
//*     functionality; it is working here in this way for           *   FILE 883
//*     several years, but has never been tested with a complex     *   FILE 883
//*     HSM configuration. We can handle securely only one ML2      *   FILE 883
//*     recall or one ML2 migration request. It works only with     *   FILE 883
//*     non SMS volumes.                                            *   FILE 883
//*                                                                 *   FILE 883
```

