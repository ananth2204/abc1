
## $DOC.txt
```
  Here's a couple of words of explanation.  REXXFORM is a VM REXX exec
  which has been written to beautify and reformat other REXX execs.  It
  is in the form of an XEDIT macro.  You XEDIT the REXX exec on VM,
  and run the XEDIT macro REXXFORM, which reformats the exec that's
  being edited (I think.  You have to try it).

  I'm putting this program here, because I'd like someone to convert
  it to an ISPF edit macro, that can be used to reformat TSO REXX
  execs that you are editing under ISPF.

  Someone who knows both VM and MVS TSO, please do this and send the
  result back to me.  Thanks.

       Sam Golob                      email:  sbgolob@attglobal.net
       P.O. Box 906                           sbgolob@aol.com
       Tallman, NY 10982-0906


  I accept contributions to the CBT Tape by email.  Create a pds
  with the software, and doc to install.  Then allocate a sequential
  output dataset in 80-byte (card image) format,
  DCB=(LRECL=80,RECFM=PS,BLKSIZE=6000), for example.  XMIT the pds to
  yourself, using the INDATASET and OUTDATASET keywords:

    XMIT yournode.yourid INDATASET(your.pds) OUTDATASET(your.seq)

  Then download the OUTDATASET in binary (no translation) to a pc
  and attach that file to an email to me.   That's all folks.

  And that's how I accept contributions.  Thanks a bunch in advance.

```

