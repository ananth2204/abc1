```
//***FILE 748 is from Jose Neto and contains a REXX program, and    *   FILE 748
//*           also an equivalent Assembler program, to convert      *   FILE 748
//*           BASE64 encoding back to message text.                 *   FILE 748
//*                                                                 *   FILE 748
//*           Also included here is an email sending system which   *   FILE 748
//*           allows an administrator to approve system changes,    *   FILE 748
//*           using emails.  See member $$MAIL in this pds, for     *   FILE 748
//*           details.  See also, member $$README.                  *   FILE 748
//*                                                                 *   FILE 748
//*           Please see member $$NOTE2 in the pds, which           *   FILE 748
//*           (sort of) supersedes member $$NOTE1.                  *   FILE 748
//*                                                                 *   FILE 748
//*           email:  joserfneto@yahoo.co.uk                        *   FILE 748
//*                                                                 *   FILE 748
//*     Here is a summary of the members in this library:           *   FILE 748
//*                                                                 *   FILE 748
//*    1. CALLDECA   REXX sample program used to call DECODE64      *   FILE 748
//*                  (the call is external to the routine)          *   FILE 748
//*                  Note: DECODE64 may reside on LLA or LPA        *   FILE 748
//*                                                                 *   FILE 748
//*    2. CALLDECR   REXX sample program used to call DECODREX      *   FILE 748
//*                  (the call is internal to the routine; both     *   FILE 748
//*                  routines must be part of the same REXX         *   FILE 748
//*                  program)                                       *   FILE 748
//*                                                                 *   FILE 748
//*    3. CALLSEND   REXX sample program used to call MAILSEND      *   FILE 748
//*                                                                 *   FILE 748
//*    4. DECODE64   Assembler program for decoding the BASE64      *   FILE 748
//*                                                                 *   FILE 748
//*    5. DECODREX   REXX program for decoding the BASE64           *   FILE 748
//*                                                                 *   FILE 748
//*    6. MAILPARM   Parameter file pointed by SYSTSIN on the       *   FILE 748
//*                  PROCMAIL                                       *   FILE 748
//*                                                                 *   FILE 748
//*    7. MAILRECV   REXX program which is called to receive        *   FILE 748
//*                  the email at the Mainframe. At the end of      *   FILE 748
//*                  the routine we will have:                      *   FILE 748
//*                                                                 *   FILE 748
//*      Variables y.1  y.2 and y.3 have the time the email         *   FILE 748
//*      was received the sender and the plain text from the        *   FILE 748
//*      DECODE64.                                                  *   FILE 748
//*                                                                 *   FILE 748
//*      Example:                                                   *   FILE 748
//*      y.1 = Email Received at:  Sat  4 Nov 2006 21:08:27 +0300   *   FILE 748
//*      y.2 = From: "Jose Neto" <joserfneto@yahoo.co.uk>           *   FILE 748
//*      y.3 = Message Content is: group1=Approve+Order+12345       *   FILE 748
//*                                                                 *   FILE 748
//*      In our system we address a table where the key is the      *   FILE 748
//*      order number and set the approval status.                  *   FILE 748
//*                                                                 *   FILE 748
//*      Also  MAILRECV saves the log from the email in a file      *   FILE 748
//*      with a DSNAME in the format:                               *   FILE 748
//*      MAILCH.LOG.MISC.D041106.T210648 meaning it was             *   FILE 748
//*      received at 4/11/2006 at 21:06:48.                         *   FILE 748
//*                                                                 *   FILE 748
//*      Note: the base64 text will come in a file which is         *   FILE 748
//*      attached to the email with a filename="POSTDATA.ATT"       *   FILE 748
//*                                                                 *   FILE 748
//*    8. MAILSEND  REXX program which is called to send the        *   FILE 748
//*       email to the Microsoft Exchange Server The email is       *   FILE 748
//*       formatted using HTML tags.                                *   FILE 748
//*                                                                 *   FILE 748
//*       You do not need to be a expert on HTML language to        *   FILE 748
//*       code it.  The following sites were my guideline to        *   FILE 748
//*       build it:                                                 *   FILE 748
//*                                                                 *   FILE 748
//*  http://www.tizag.com/htmlT/forms.php                           *   FILE 748
//*  http://www.w3.org/TR/REC-html40/cover.html#minitoc             *   FILE 748
//*  http://www.htmlgoodies.com/tutorials/forms/article.php/3479121 *   FILE 748
//*  http://www.w3.org/TR/REC-CSS1                                  *   FILE 748
//*                                                                 *   FILE 748
//*    9. PROCMAIL   The procedure used to call MAILRECV REXX       *   FILE 748
//*                  Program                                        *   FILE 748
//*                                                                 *   FILE 748
//*       Note: the RACF User associated with the Procedure         *   FILE 748
//*       has to be the same as the one used in the MAILSEND        *   FILE 748
//*       program. In our case it was named MAILCH (check           *   FILE 748
//*       strings  MAIL FROM:  and  FROM: on the MAILSEND           *   FILE 748
//*       program)                                                  *   FILE 748
//*                                                                 *   FILE 748
//*    10. SENDMAIL   A sample JCL which you might use to           *   FILE 748
//*       build up and test your own HTML form before               *   FILE 748
//*       inserting it into the MAILLSEND program.                  *   FILE 748
//*                                                                 *   FILE 748
//*       Note: The SMTP configuration is not very difficult.       *   FILE 748
//*       You will find all the information you need in the         *   FILE 748
//*       manuals:  IP Configuration Guide at section               *   FILE 748
//*       Configuring the SMTP server, and IP Configuration         *   FILE 748
//*       Reference at chapter  SMTP Server.                        *   FILE 748
//*                                                                 *   FILE 748

```
