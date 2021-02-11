```
//***FILE 484 is from Chuck Baumann and contains a utility he       *   FILE 484
//*           developed to display cache information and to         *   FILE 484
//*           manage cache.  A description of the utility follows:  *   FILE 484
//*                                                                 *   FILE 484
//*    ---------------------------------------------------------    *   FILE 484
//*                                                                 *   FILE 484
//*       Since Amdahl is no longer in the S390 market  I           *   FILE 484
//*       thought I would get around to contributing a utility      *   FILE 484
//*       program I developed for Amdahl customers at no charge.    *   FILE 484
//*                                                                 *   FILE 484
//*       I call this program Cacheman.  It is an ISPF dialog       *   FILE 484
//*       that displays and modifies 3990 (and 3880) cache          *   FILE 484
//*       statuses at both the controller and device level.  It     *   FILE 484
//*       has been in use since 1994 at over 200 sites              *   FILE 484
//*       worldwide.   I am including a small portion of the        *   FILE 484
//*       documentation file here to give you a better idea what    *   FILE 484
//*       this utility does.                                        *   FILE 484
//*                                                                 *   FILE 484
//*                Cacheman (Amdahl Cache Utility)                  *   FILE 484
//*                                                                 *   FILE 484
//*       This document contains a description of the tool          *   FILE 484
//*       Cacheman, a brief history of the product,  a sample of    *   FILE 484
//*       the ISPF panels and output from an actual session, and    *   FILE 484
//*       the instructions for installing on a host MVS system.     *   FILE 484
//*                                                                 *   FILE 484
//*       Description:  Cacheman is a software tool that allows     *   FILE 484
//*       the user to display the cacheing status of DASD           *   FILE 484
//*       controllers and devices connected to cached               *   FILE 484
//*       controllers.  This dialog is much easier to use than      *   FILE 484
//*       the ISMF panels but is NOT a replacement for ISMF.        *   FILE 484
//*       The dialog features a user customizable options panel,    *   FILE 484
//*       logging, and field level help.                            *   FILE 484
//*                                                                 *   FILE 484
//*       Cacheman is an ISPF dialog that formats the output from   *   FILE 484
//*       the LISTDATA and SETCACHE commands and displays the       *   FILE 484
//*       results in a tabular format.  The status of devices and   *   FILE 484
//*       controllers can be easily monitored and modified from     *   FILE 484
//*       these panels.  An options panel allows the user to        *   FILE 484
//*       easily 'tailor' certain aspects of this dialog.  Help     *   FILE 484
//*       panels and field level help are both available in this    *   FILE 484
//*       dialog. It will work for 3990, 3880-11,13,21,23, and      *   FILE 484
//*       3rd party 3990 compatible controllers (Amdahl, Hitachi,   *   FILE 484
//*       EMC, etc)                                                 *   FILE 484
//*                                                                 *   FILE 484
//*       Cacheman is coded in TSO/E REXX.  There are three small   *   FILE 484
//*       assembler routines which scan the UCB chains and return   *   FILE 484
//*       information. No modules require APF authorization. RACF   *   FILE 484
//*       or ACF/2 authorizations will be required to allow users   *   FILE 484
//*       to issue the LISTDATA and SETCACHE commands.              *   FILE 484
//*                                                                 *   FILE 484
//*       I am currently still at Amdahl and my phone number at     *   FILE 484
//*       work is (408) 746-4784.                                   *   FILE 484
//*       email:  chuck_baumann@amdahl.com                          *   FILE 484
//*                                                                 *   FILE 484

```
