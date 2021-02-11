```
//***FILE 991 is from John Hamlet and contains programs that are    *   FILE 991
//*           useful.  Currently it contains a program to           *   FILE 991
//*           temporarily install an SVC.                           *   FILE 991
//*                                                                 *   FILE 991
//*           email:  jrhamlet@bellsouth.net                        *   FILE 991
//*                                                                 *   FILE 991
//*           email:  sbgolob@cbttape.org    (alternate support)    *   FILE 991
//*                                                                 *   FILE 991
//*       Description of members:                                   *   FILE 991
//*                                                                 *   FILE 991
//*       SVCUPDTE - Temporarily install an SVC while this job is   *   FILE 991
//*                  running.  It runs and waits.                   *   FILE 991
//*                  Then it undoes itself, and the SVC install,    *   FILE 991
//*                  when you cancel or stop the job.  You should   *   FILE 991
//*                  use an unused jobname when running this batch  *   FILE 991
//*                  job, so you don't get a "duplicate jobname"    *   FILE 991
//*                  situation.                                     *   FILE 991
//*                                                                 *   FILE 991
//*                  Stopping the job with a P jobname is           *   FILE 991
//*                  the preferred method of ending the install.    *   FILE 991
//*                  Cancel will work, but you will get a S522      *   FILE 991
//*                  instead of a RC = 0.                           *   FILE 991
//*                                                                 *   FILE 991
//*                  This version requires some special RACF        *   FILE 991
//*                  profiles to be in place, to restrict users.    *   FILE 991
//*                  Otherwise it won't run.                        *   FILE 991
//*                                                                 *   FILE 991
//*       SVCUPDTX - Temporarily install an SVC while this job is   *   FILE 991
//*                  running.  It runs and waits.                   *   FILE 991
//*                  Then it undoes itself, and the SVC install,    *   FILE 991
//*                  when you cancel or stop the job.  This         *   FILE 991
//*                  version bypasses some RACF checks, so you      *   FILE 991
//*                  can run it if your id is SPECIAL, and you      *   FILE 991
//*                  didn't install any of the RACF profiles it     *   FILE 991
//*                  normally needs.                                *   FILE 991
//*                                                                 *   FILE 991

```
