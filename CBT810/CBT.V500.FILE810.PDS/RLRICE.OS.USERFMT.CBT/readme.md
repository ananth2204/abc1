
## $DOC.txt
```
The whole purpose for On Screen is to allow users to view data.

USERFMT allows users to do some customized data formatting
without having to do any actual programming.

USERFMT uses control statements that are a part of the format
definition (members in the OSFORMAT library).  Any control
statements that OSFORMAT does not recognize are passed through
to the 'formatter'.  This allows the same 'formatter' program
to perform mutliple functions.

USERFMT control statements are:

  FIELD statements
    1-10       literal 'FIELD'
   10-19       starting position in data record
   20-29       length in data record
   30-39       data type
   40-49       row,column for displaying in dynamic area
   50-80       data displayed for HEADING fields






  IF statements
    1-10       literal 'IF'
   10-19       starting position in data record of data to be tested
   20-29       length of data to be tested
   30-39       data type
   40-49       condition
   50-80       value used for test





  ENDIF
    1-10       literal 'IF'











Numeric fields may be either packed decimal or binary.
By default numeric fields will be displayed with all digits
(leading zeros not suppressed).  However, you may include a
"edit word" or "picture" that is much like COBOL PICTUREs.













```

