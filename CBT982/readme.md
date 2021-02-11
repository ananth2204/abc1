```
//***FILE 982 is from Clem Clarke and is the JOL package, which     *   FILE 982
//*           allows for submission of jobs without using JCL.      *   FILE 982
//*           JOL is also a command language.  The following is     *   FILE 982
//*           an introduction to JOL, taken from the Preface of     *   FILE 982
//*           its Concepts and Facilities manual.                   *   FILE 982
//*                                                                 *   FILE 982
//*      Jol effectively replaces the JCL interpreter and quite     *   FILE 982
//*      a lot of the initiator when using Dynamic Allocation       *   FILE 982
//*      instead of JCL.  It is part compiler with PL/I style       *   FILE 982
//*      syntax, and ASM macro capabilities, and part run time      *   FILE 982
//*      monitor.                                                   *   FILE 982
//*                                                                 *   FILE 982
//*         Nothing I say here, does justice to the enormity        *   FILE 982
//*         of this great work.  Please see Clem's web site         *   FILE 982
//*         for much more detail.  But I think I've captured        *   FILE 982
//*         the guts, here, in the contents of this file pds.       *   FILE 982
//*                                                                 *   FILE 982
//*         I hope I have done some justice to this enormous        *   FILE 982
//*         and extremely significant software package by           *   FILE 982
//*         putting it on the CBT Tape.  Thank you Clem, for        *   FILE 982
//*         letting us post it.                                     *   FILE 982
//*                                                                 *   FILE 982
//*           web site:  www.oscar-jol.com                          *   FILE 982
//*                                                                 *   FILE 982
//*           email   :  clementclarke@OZEMAIL.COM.AU               *   FILE 982
//*                                                                 *   FILE 982
//*                         Introduction                            *   FILE 982
//*                                                                 *   FILE 982
//*      Jol is a high-level, English-like and Universal COMMAND    *   FILE 982
//*      LANGUAGE. A Command Language is the highest level of       *   FILE 982
//*      communication between the User and the computer. Command   *   FILE 982
//*      languages tell the computer what to do, when to do it,     *   FILE 982
//*      and what to do with the result. Programming Languages,     *   FILE 982
//*      such as PL/I and COBOL, give the computer detailed         *   FILE 982
//*      instructions on how to do it.  Use of Command Languages    *   FILE 982
//*      spreads across all areas of Data Processing.  Without      *   FILE 982
//*      them, we have no means of communicating with the           *   FILE 982
//*      Operating System.  Inefficient use of a Command Language   *   FILE 982
//*      can have disastrous effects on corporations' computing     *   FILE 982
//*      resources.                                                 *   FILE 982
//*                                                                 *   FILE 982
//*      Today, not all computer Users are Computer Technicians.    *   FILE 982
//*      Therefore, it is extremely important that the Command      *   FILE 982
//*      Language used is simple and easy to use.  Additionally,    *   FILE 982
//*      with the increasing expansion of computer resources and    *   FILE 982
//*      the growing number of software packages being acquired     *   FILE 982
//*      by each installation, the Computer Users are               *   FILE 982
//*      increasingly needing more power and flexibility in their   *   FILE 982
//*      Command languages. Jol is unique in meeting these new      *   FILE 982
//*      standards for Command Languages.                           *   FILE 982
//*                                                                 *   FILE 982
//*      Jol uses a simple, flexible, concise and English-like      *   FILE 982
//*      command structure to communicate with your operating       *   FILE 982
//*      system and to effectively control data, programs, and      *   FILE 982
//*      events. It is easy to learn, easy to use, and easy to      *   FILE 982
//*      change. With these features, Jol allows Users to better    *   FILE 982
//*      utilize their skills, experience, and creative abilities   *   FILE 982
//*      enabling them to be more proficient than was ever          *   FILE 982
//*      previously possible.                                       *   FILE 982
//*                                                                 *   FILE 982
//*      Jol is written in a procedural format that is already      *   FILE 982
//*      familiar to Programmers using programming languages such   *   FILE 982
//*      as COBOL, PASCAL or PL/I. The procedural format provides   *   FILE 982
//*      you with the flexibility to solve the most complex type    *   FILE 982
//*      of requirements in a logical straightforward manner. By    *   FILE 982
//*      combining the flexibilities of these modern procedural     *   FILE 982
//*      languages with many new features, Jol provides a simple,   *   FILE 982
//*      powerful, and flexible INTERFACE to the operating system.  *   FILE 982
//*      In addition, Jol coexists with JCL, and interfaces with    *   FILE 982
//*      contemporary development techniques, such as top down      *   FILE 982
//*      design, step level refinement, structured coding, and      *   FILE 982
//*      prototyping. Jol's many features focus on the End User,    *   FILE 982
//*      programming maintenance and development, production        *   FILE 982
//*      (e.g., operations and scheduling), management control,     *   FILE 982
//*      machine utilization, job scheduling and job networking.    *   FILE 982
//*                                                                 *   FILE 982
//*      Jol has some 40 commands. These commands can be combined   *   FILE 982
//*      with themselves and with any other program to form new     *   FILE 982
//*      commands tailored specifically to your installation.  With *   FILE 982
//*      Jol you can also execute commands from within commands,    *   FILE 982
//*      adding greatly to the flexibility and simplicity of        *   FILE 982
//*      procedures. This openendedness is one of the highlights of *   FILE 982
//*      Jol.                                                       *   FILE 982
//*                                                                 *   FILE 982
//*      Jol has many other highlights. Management can use Jol to   *   FILE 982
//*      monitor jobs and trap inefficiencies before jobs begin     *   FILE 982
//*      to execute. Systems Programmers can alter the              *   FILE 982
//*      inefficient code and make it more efficient through        *   FILE 982
//*      Exits. Data set protection facilities are also offered.    *   FILE 982
//*                                                                 *   FILE 982
//*      The data set attribute data base allows the data manager   *   FILE 982
//*      great flexibility - data set attributes can be changed     *   FILE 982
//*      without altering any of the Jol command language           *   FILE 982
//*      scripts.                                                   *   FILE 982
//*                                                                 *   FILE 982

```
