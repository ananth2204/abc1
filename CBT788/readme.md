```
//***FILE 788 is from Craig Schneiderwent and contains the MA1K     *   FILE 788
//*           application for MQ Series, which was authored by      *   FILE 788
//*           him.  This application used to be distributed on      *   FILE 788
//*           an IBM website, but it is now distributed here.       *   FILE 788
//*                                                                 *   FILE 788
//*           email:  cschneidpublic@yahoo.com                      *   FILE 788
//*                                                                 *   FILE 788
//*   External Information for this package :                       *   FILE 788
//*                                                                 *   FILE 788
//*    This pds contains three files.  The first is source and      *   FILE 788
//*    the second the attendant copybooks for what used to be       *   FILE 788
//*    known as the Category 4 WebSphere MQ SupportPac MA1K.        *   FILE 788
//*                                                                 *   FILE 788
//*    This supportpac used to be hosted by IBM on their            *   FILE 788
//*    website, but changes to IBM's "agreement" document           *   FILE 788
//*    governing such hosting necessitated its removal.  The        *   FILE 788
//*    MA1KSRC and MA1KCPY files are XMITted PDSs that were         *   FILE 788
//*    FTP'd in binary.  The last file is MA1KDOC which has         *   FILE 788
//*    further details about the use of the application and a       *   FILE 788
//*    contact email address.                                       *   FILE 788
//*                                                                 *   FILE 788
//*    I am the original author of the MA1K SupportPac, and         *   FILE 788
//*    would like its availability to continue.                     *   FILE 788
//*                                                                 *   FILE 788
//*   Particulars and Details about this package :                  *   FILE 788
//*                                                                 *   FILE 788
//*    MA1K Application....                                         *   FILE 788
//*                                                                 *   FILE 788
//*    The purpose of this application is to encapsulate            *   FILE 788
//*    triggered message processing for MQSeries applications       *   FILE 788
//*    triggered in CICS TS.                                        *   FILE 788
//*                                                                 *   FILE 788
//*    Applications that are triggered can call this subroutine     *   FILE 788
//*    and receive their triggering message.  If the triggering     *   FILE 788
//*    message's MQMD-BACKOUTCOUNT >= the queue's                   *   FILE 788
//*    MQIA-BACKOUT-THRESHOLD the "poison" message will be          *   FILE 788
//*    moved to the queue's MQCA-BACKOUT-REQ-Q-NAME.  If the        *   FILE 788
//*    queue has no MQCA-BACKOUT-REQ-Q-NAME the poison message      *   FILE 788
//*    will be discarded.                                           *   FILE 788
//*                                                                 *   FILE 788
//*    In any case, a message will be written to the system log     *   FILE 788
//*    indicating what action was taken.                            *   FILE 788
//*                                                                 *   FILE 788
//*    POSSIBLE USES                                                *   FILE 788
//*    This application generically encapsulates triggered          *   FILE 788
//*    message processing, backout processing and error             *   FILE 788
//*    handling for triggered queues in CICS TS.  Adopted as a      *   FILE 788
//*    standard, or used as a base and modified to create a         *   FILE 788
//*    standard, development time can be reduced and uniform        *   FILE 788
//*    error handling assured.                                      *   FILE 788
//*                                                                 *   FILE 788
//*    These source code members presume a minimum CICS TS          *   FILE 788
//*    level of 3.1 and a minimum WebSphere MQ level of 6.0.        *   FILE 788
//*                                                                 *   FILE 788

```
