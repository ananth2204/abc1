```
//***FILE 822 is from Terry Miller, and contains code to capture    *   FILE 822
//*           cpu utilization and limit information for use as a    *   FILE 822
//*           metric in softcapping an Lpar or an Lpar group.       *   FILE 822
//*                                                                 *   FILE 822
//*             email:  tkmille@conocophillips.com                  *   FILE 822
//*                                                                 *   FILE 822
//*       LAST UPDATE: 03/09/2010  Terry Miller                     *   FILE 822
//*                                ConocoPhillips                   *   FILE 822
//*                                tkmille@ConocoPhillips.com       *   FILE 822
//*                                                                 *   FILE 822
//*       MODIFICATION LEVEL: V01.01.01                             *   FILE 822
//*                                                                 *   FILE 822
//*   * * * * * * * * * * * * * * * * * * * * * * * * * * * * *     *   FILE 822
//*                                                                 *   FILE 822
//*   This facility was written to assist in measuring Lpar cpu     *   FILE 822
//*   utilization against capacity for the purpose of Softcapping   *   FILE 822
//*   an Lpar or an Lpar group using a 4 hour rolling average with  *   FILE 822
//*   IBM's subcapacity software pricing for monthly license        *   FILE 822
//*   charges (MLC).  It can be used in conjuction with the         *   FILE 822
//*   SCPTOOL (SubCapacity Pricing Tool) that IBM provides.         *   FILE 822
//*   (http://www-03.ibm.com/systems/z/resources/swprice/subcap/    *   FILE 822
//*    scpt/instruct.html)                                          *   FILE 822
//*                                                                 *   FILE 822
//*   Program SOFTCAPI will capture cpu utilization and capacity    *   FILE 822
//*   information and issue two WTO messages to Syslog and          *   FILE 822
//*   also write the two message to a log file (OUTPUT file).       *   FILE 822
//*                                                                 *   FILE 822
//*   SOFTCAPI WTO Messages:                                        *   FILE 822
//*                                                                 *   FILE 822
//*   1) SOFTCAPI LPAR LPARX CURRENT ROLLING 4-HR AVG UTILIZATION   *   FILE 822
//*      IS 9 MSUS                                                  *   FILE 822
//*   2) SOFTCAPI SY6 CAPACITY IS 27 MSUS, LPAR CAPACITY            *   FILE 822
//*      IS 15 MSUS                                                 *   FILE 822
//*                                                                 *   FILE 822
//*   The program can be issued by automation on a time interval    *   FILE 822
//*   to capture interval metrics to be graphed.                    *   FILE 822
//*                                                                 *   FILE 822
//*   The STCJOB (started job) member is used to execute the        *   FILE 822
//*   program and capture the data into a capture log.              *   FILE 822
//*                                                                 *   FILE 822
//*   The daily capture log can then be used to graph daily         *   FILE 822
//*   cpu utilization.                                              *   FILE 822
//*                                                                 *   FILE 822

```
