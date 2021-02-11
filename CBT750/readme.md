```
//***FILE 750 is from Ted MacNeil and contains some ISPF REXX       *   FILE 750
//*           EXECs to make your life easier.  These EXECs were     *   FILE 750
//*           written by Ted MacNeil for an IBM Systems Magazine    *   FILE 750
//*           article, and were submitted after the expiration      *   FILE 750
//*           of the 60 day intellectual property deadline.         *   FILE 750
//*                                                                 *   FILE 750
//*           email:  Ted MacNEIL <eamacneil@yahoo.ca>              *   FILE 750
//*                                                                 *   FILE 750
//*    Contents:                                                    *   FILE 750
//*      Sample REXX EXECs for/from IBM Systems Magazine Article    *   FILE 750
//*        "Digging Into the Bag of ISPF Tricks"                    *   FILE 750
//*         http://tinyurl.com/yyghzr                               *   FILE 750
//*                                                                 *   FILE 750
//*    ISPFINI -- ISPF Start Up REXX EXEC (Multiple Screens)        *   FILE 750
//*               NOTE:  For this REXX EXEC to work properly        *   FILE 750
//*               (seamlessly) you should change your ISPF          *   FILE 750
//*               SWAP key to SWAP NEXT. You should set it up       *   FILE 750
//*               that way for any time you are using more          *   FILE 750
//*               than two screens inside ISPF                      *   FILE 750
//*                                                                 *   FILE 750
//*    MULTISPF -- To allocate an ISPF Profile for which every      *   FILE 750
//*                system you are on in a multiple TSO              *   FILE 750
//*                environment.  Add to your default logon          *   FILE 750
//*                processing, before entering ISPF.                *   FILE 750
//*                                                                 *   FILE 750
//*                NOTE:  Contrary to what my article said,         *   FILE 750
//*                you can only logon once on any single z/OS       *   FILE 750
//*                image with the same USERID.  Also, the           *   FILE 750
//*                profiles will DRIFT over time, so that the       *   FILE 750
//*                contents will differ from each system you        *   FILE 750
//*                sign on to.  That never bothered me.             *   FILE 750
//*                                                                 *   FILE 750
//*    PROFSAVE -- Save your ISPF profile without exiting ISPF.     *   FILE 750
//*                                                                 *   FILE 750
//*    SPFLOGOF -- Set up a single key logoff.                      *   FILE 750
//*                You can use this REXX EXEC, or you can           *   FILE 750
//*                insert the following in the TRANS portion        *   FILE 750
//*                of the )BODY of ISR@PRIM (or whatever your       *   FILE 750
//*                Primary Panel is):                               *   FILE 750
//*                                                                 *   FILE 750
//*                     L,'CMD(TSOEXEC LOGOFF)'                     *   FILE 750
//*                                                                 *   FILE 750

```
