
## $DOC.txt
```
Hi folks,

I am a Rexx lover and the RXMEM is one more function from my personal
library that I would like to share with you.
As I work with other languages, like Java, VB, Pascal and C++, sometimes
I need to use linked list, in Java for example, ArrayList class...
That is an interesting technique to manage items from a list, using to
resources like insert, add to end, count items, delete items and other.

Now I am provinding the first version of RXMEM.

The RXMEM has the following features :
  - to manage token pair service, using IEANTxx modules
  - to manage getmain and freemain memory
  - to manage linked list options

As I am working on improvements, I am not delivering the source code.
Just a rexx samples.

Please, let me know about possible abends and issues.

Gaeta, Daniel
IBM/BR

This is a summary of function/actions :

***********************************************************************
* FUNCTION  : RXMEM                                                   *
* PARAMETER : RXMEM(ACTION,LISTNAME,<..>)                             *
*                                                                     *
* ACTIONS   :                                                         *
*            TKCRT - CREATE A TOKEN PAIR                              *
*            RET=('TKCRT',PAIR1,PAIR2)                                *
*            ...                                                      *
*            TKDEL - DELETE A TOKEN PAIR                              *
*            RET=('TKDEL',PAIR1)                                      *
*            ...                                                      *
*            TKRTV - RETRIEVE A TOKEN PAIR                            *
*            RET=('TKRTV',PAIR1)                                      *
*            ...                                                      *
*            OBTAIN - OBTAIN MEMORY USING BYTES                       *
*            ADR=('OBTAIN',D2C(<BYTES>,4))                            *
*            ...                                                      *
*            RELEASE - RELEASE MEMORY OBTAINED FROM OBTAIN            *
*            RET=('RELEASE',D2C(<ADDR>,4),D2C(<LEN>,4))               *
*            ...                                                      *
*            CREATE - CREATE A NEW LINKED LIST                        *
*            RET=('CREATE',<LNAME>)                                   *
*            ...                                                      *
*            DESTROY - DESTROY PREVIOUS LINKED LIST CREATED           *
*            RET=('DESTROY',<LNAME>)                                  *
*            ...                                                      *
*            ADD - ADD AN ELEMENT INTO END OF LIST                    *
*            RET=('ADD',<LNAME>,<STR>)                                *
*            ...                                                      *
*            DEL - DELETE AN ELEMENT IN ORDINAL POSITION              *
*            RET=('DEL',<LNAME>,D2C(<POS>,4))                         *
*            ...                                                      *
*            GET - GETTING A DATA ITEM FROM ORDINAL POSITION          *
*            STR=('GET',<LNAME>,D2C(<POS>,4))                         *
*            ...                                                      *
*            SET - SETTING A DATA ITEM TO ORDINAL POSITION            *
*            STR=('SET',<LNAME>,D2C(<POS>,4),<STR>)                   *
*            ...                                                      *
*            COUNT - NUMBER ELEMENTS FROM LINKED LIST                 *
*            CNT=('COUNT',<LNAME>)                                    *
*            ...                                                      *
*            SAVESTEM - UPDATE STEM VARIABLE WITH ITEMS FROM LIST     *
*            RET=('SAVESTEM',<LNAME>)                                 *
*            ...                                                      *
*            LOADSTEM - UPDATE ITEMS FROM LIST USING STEM VARIABLE    *
*            RET=('LOADSTEM',<LNAME>,D2C(<BEGIN>,4),D2C(<END>,4))     *
*            ...                                                      *
*            INS - INSERT AN ELEMENTO IN ORDINAL POSITION             *
*            RET=('INS',<LNAME>,D2C(<POS>,4),<STR>)                   *
***********************************************************************
```

