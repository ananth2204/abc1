
## $$DOC1.txt
```
 This is a modification of the IBM supplied RACSEQ program.  It has
 been modified to be able to write its output in XML format. It has
 also been extended to write to a specified DDName, DSName, Sysout
 class, or UNIX Path.When writing to a DSName, it can either be an
 existing DSName, or a new one. If it is a new one, the DSName will be
 allocated with either the system defaults, the SMS defaults as
 assigned by the ACS routines, or with the characteristics specified
 via a USING() and/or LIKE() parameter.

 Command format:

 RACSEQ CLASS(classname) PROFILE(profilename)
    NONXML | XML
    Terminal | DDName(ddname) | DSName(dsname) | Sysout(class) | Path(path)
    USING(attr-list-name)
    LIKE(existing.dataset.name)

 The defaults are NONXML and Terminal, which results in the same output as
 the code distributed by IBM.

 The attr-list-name is the name previously established by a ATTRIB command.

 The "dsname" honors the normal TSO standard of prepending the name
 specified by the PREFIX unless it is enclosed in apostrophes.

 The class in the Sysout parameter must be exactly one character in
 the set A..Z0..9. You cannot specify other SYSOUT characteristics
 such as FORM or DEST. If you need this type of support, then use an
 ALLOCATE command to allocate the SYSOUT dataset, and reference the
 allocated DDName in the DDName() parameter.

 The value in the Path() parameter must start at the root. That is
 because I don't have an easy way to determine any relative path
 names. So this is easier for me than fielding questions. Again, I'm
 being a bit lazy.

 This code is being distributed in source form only. You must assemble
 it into an appropriate library.
```

