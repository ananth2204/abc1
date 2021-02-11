```
//***FILE 866 is from Vladimir Mestovski and contains a program     *   FILE 866
//*           called BSPUFI (Batch SPUFI or C SQL-DB2-TSO           *   FILE 866
//*           Processor)                                            *   FILE 866
//*                                                                 *   FILE 866
//*   Author      :  Vladimir Mestovski, IBA, Minsk, Belarus        *   FILE 866
//*   ------      :  v2gri033@us.ibm.com  -- preferred for bugs     *   FILE 866
//*               :  mestovsky@iba.by     -- additional email       *   FILE 866
//*               :  This program is for free use, not for sale.    *   FILE 866
//*                                                                 *   FILE 866
//*   Short description:                                            *   FILE 866
//*                                                                 *   FILE 866
//*     The program reads an input file with SQL/DB2/TSO            *   FILE 866
//*     statements/ commands and executes them. After each SQL      *   FILE 866
//*     the program prints out CPU and TOTAL times what helps to    *   FILE 866
//*     create effective SQL.  You can start SQL statements with    *   FILE 866
//*     special internal commands like WRITE for a SELECT to        *   FILE 866
//*     redirect its report in different formats                    *   FILE 866
//*     (CSV,TAB,ASIS,RPT,...) to a flat file or internal data      *   FILE 866
//*     stacks, or READ for an INSERT to load input into a          *   FILE 866
//*     table.  You can program conditional execution of SQL        *   FILE 866
//*     statements using labels, special variables RCÝn¨ and        *   FILE 866
//*     commands IF,GOTO/SKIP...  See other features of "mySQL      *   FILE 866
//*     for zOS" in the program's header.                           *   FILE 866
//*                                                                 *   FILE 866
//*   List of members:                                              *   FILE 866
//*                                                                 *   FILE 866
//*     BSPUFI  -- source C code                                    *   FILE 866
//*     CBSPUFI -- compile/bind job                                 *   FILE 866
//*     DEMOJOB -- demo job                                         *   FILE 866
//*     DEMOSQL -- main input SQL for demo job                      *   FILE 866
//*     DEMOSQL1-- aux input SQL for demo job                       *   FILE 866
//*     SQL     -- ISPF Edit Macro to run the program               *   FILE 866
//*                in interactive mode                              *   FILE 866
//*                                                                 *   FILE 866

```
