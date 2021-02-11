
## $$$DOC.txt
```
This is the documentation for the cross-memory browser (originally
called MINDRDR) from Martin Kline.

As of 08/24/2004, Martin is employed with American Century Investments
in Kansas City, MO. He can be reached for information at
martin_kline@americancentury.com

The source originated in the mid 1980's, so it could possibly use
some updates. It was written as a tool to help in the design and
implementation of several major applications, including a replacement
for TCAM TSO (without VTAM), and a complete report management
subsystem.

The tool allows a user to browse through any address space from the
convenience of their own TSO session. Obviously, this has some
security risks, and should only be used by responsible persons. When
it was first written, several major security holes were found,
including the availability of passwords in various control blocks.
Most of those security holes have since been fixed.

The XMDSMAIN program checks the logon proc name to see if the
user should be allowed to run the program. If not, it simply
exits.

Installation:

All of the source, JCL and macro members are contained in this PDS.
Determine which load library is to receive the XMDSMAIN module.
Member $$ASM is the JCL to assemble the source members and to build
an authorized load module. Add a job card. Change the input and output
datasets, and run it.

Move the resulting load module to an authorized linklist library.
(You really didn't think you could do this without some sort of
authorization, did you?) If you prefer to use a user SVC to change
the APF authorization dynamically, then find all of the @AUTH macro
references in the source, and change them to call your SVC.

Add the XMDSMAIN program to the IKJTSOxx member of SYS1.PARMLIB as
an authorized command.

You have to customize and run the ZAPPROC job, or else you have to
alter the source code to not check for your logon proc.

Usage:

Invoke the program from anywhere in TSO/ISPF. ISPF is not required.

Assigned keys are:

  PF1  - Help
  PF3  - End
  PF5  - Repeat find
  PF7  - Scroll backward
  PF8  - Scroll forward
  PF11 - Pick up address from cursor and show that storage

  FIND command - FIND or F  'string' or x'string'
                 Searches up to 16 meg of storage
                 Can take a long time if storage not allocated.

  LOCATE command - LOCATE or L   block-name
                   Locates and displays various control blocks.
                   Use PF1 to see a list of supported blocks.

Fields:

  ADDRESS   - Current address. Overtype to show a specific location
  MODE      - Addressing mode. D = 24-bit mode, X = 31-bit mode
  ASID      - Decimal ASID of displayed address space. Overtype
              to change ASIDs
  JOBNAME   - Job name of displayed address space. Overtype to change.

Displayed storage cannot be altered. Use TAB key to move to a field
before pressing PF11 to link to that address.


```

