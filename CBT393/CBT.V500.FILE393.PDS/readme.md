
## $$$DOC1.txt
```
Date:    Wed, 1 Sep 1999 09:09:12 -0600
From:    "Lamerand, Robert A" <LamerRA@LOUISVILLE.STORTEK.COM>
Subject: Re: RACF Inquiry

Here's a simple REXX exec that allows a user to see what groups he
is connected to.  We run with "list-of-groups" active.  I'm not sure
what this will report on a system if it is inactive.

Date:    Mon, 6 Sep 1999 15:33:28 +0100
From:    Ken MacKenzie <Ken.MacKenzie@NATWEST.COM>
Subject: RACF Group Enquiry


Hi,

I was sent the following REXX exec the other day.  I made a slight
modification from the original (to pick up the correct area length).
The exec lists the groups that a user belongs to or returns YES or NO
to indicate that he belongs to a specific group.

The exec works fine but, on browsing the RACF documentation, I get
the impression that the list of groups will not be updated should
the user be added to a new group.

Can anyone confirm that this is true?  And, if so, can anyone
suggest a way of having the group list updated (without logging off
then logging on)?

Thanks-in-advance,

Ken MacKenzie









```

