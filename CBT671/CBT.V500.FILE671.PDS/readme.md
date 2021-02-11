
## $$DOC.txt
```
//*          Contains one editmacro "ZOOM" and associated HELP file.   *
//*          This editmacro was hand copied from an article in         *
//*          the Fall 1994 TSO Times.                                  *
//*                                                                    *
//* PURPOSE: provide cursor sensitive DSN and DSNAME recognition      **
//*          allowing users to ZOOM into another dataset without      **
//*          leaving their current edit session.                      **
//*                                                                   **
//* USAGE:   place cursor anywhere within a valid DSN or DSNAME       **
//*          character and start ZOOM from the command line or a      **
//*          pre-defined PFKey.  PFKey use is recommended to minimize **
//*          cursor repositioning.  If the cursor is left on the      **
//*          line, the first data line displayed will be searched for **
//*          a valid dsn.                                             **
//*                                                                   **
//* FEATURES: - DSN syntax checking with SYSDSN                       **
//*           - Symbolic variable substitution                        **
//*           - concatenation recognition with member search option   **
//*           - automatic switch to browse mode if edit fails         **
//*           - allows edit sessions to be stacked                    **
//*           - allows modular addition of new functions              **
//*                                                                    *
//* INSTALL: Install by copying ZOOM to any concatenated SYSEXEC or    *
//*          SYSPROC library. Copy ZOOMP to a concatenated ISPPLIB     *
//*          library.                                                  *
//*                                                                    *
//*          For best results assign value "ZOOM" to a PF Key.         *
//*                                                                    *
```

