
## $$$$$DOC.txt
```
-----------------------------------------------------------------------
-----------------------------------------------------------------------
RACF INTEGRITY PACKAGE.  FOR AUTHORIZED SYSTEMS USE ONLY.
I AM NOT GOING TO TELL YOU HOW TO USE IT.
-----------------------------------------------------------------------
-----------------------------------------------------------------------
LSLT - FILL IN PROGRAM NAME IN LAST SLOT OF PARMLIB-MANUFACTURED
       TSO/E AUTH TABLES, OR BLANK THE LAST SLOT ENTRY
ASUB - SUBSTITUTE ANY PROGRAM NAME INTO ANY SLOT OF ANY TSO/E
       PARMLIB-MANUFACTURED AUTH TABLE.  BUT ONLY BLANK THE LAST
       SLOT, BECAUSE BLANKING AN ARBITRARY SLOT IS TOO RISKY, SINCE
       ALL SUBSEQUENT SLOTS WILL THEREFORE BE INVALIDATED, AND THEIR
       ENTRIES WILL NOT BE HONORED BY THE SYSTEM.
TSUB - SUBSTITUTE ANY PROGRAM NAME INTO ANY SLOT OF ANY TSO/E
       AUTH TABLE POINTED TO BY THE LWA.  CAN FLIP STEPLIB BITS
       AND CHANGE LENGTHS AND OTHER STUFF.
-----------------------------------------------------------------------
-----------------------------------------------------------------------
```

