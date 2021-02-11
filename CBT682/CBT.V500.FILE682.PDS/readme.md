
## $DOC.txt
```
TSOESO = DISPLAY System ESOTERICS

> Members are :
 TSOESO     = Assembler program
 ESOPAN2    = ISPF panel
 ESO        = REXX
 ASMESO     = JCL to ASMLK TSOESO

> Usage instructions :
 1. Install REXX, PANEL in ISPF accessible datasets.
 2. ASMLK TSOESO into your LNKLST (REXX is set up for this).
 3. "TSO ESO" - Select 1 or MORE entries with "S" or "/".

> Notes on modifying TSOESO :
 1. Base regs are almost full.
 2. To add more esoteric capacity one must program more entries
    in TSOESO and expand the panel. The panel is already scrollable.
 3. IMPORTANT ! You may have to modify the following statement in the
    =========   source (its near the top of the pgm) :
                     " &STK     SETC  'YES' <=== 'YES' OR 'NO' "
    "YES" if you have STK SILOs, "NO" if you do not. "YES" includes
    STK HSC macros. Specifying "YES" and not having the STK macros will
    cause the assembly to fail.
    Additionally, if "NO" is used, comment out the JCL DD override
    "SYSLIB3" in the ASMESO JCL.
```

