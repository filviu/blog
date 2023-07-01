---
title: Oracle complains about long identifier on simple operations.
author: silviu
type: post
date: 2016-03-25T12:16:52+00:00
url: /2016/03/25/oracle-complains-about-long-identifier-on-simple-operations/
categories:
  - tech
tags:
  - oracle
  - pfile
  - spfile
  - sql

---
Soo,

I'm going head first into the oracle db world. I was trying to create an spfile from the pfile and of course it didn't work:

```sql
SQL> create spfile from pfile="/oracle/app/product/12.1.0/dbhome_1/dbs/initORCL.ora";
create spfile from pfile="/oracle/app/product/12.1.0/dbhome_1/dbs/initORCL.ora"
*
ERROR at line 1:
ORA-00972: identifier is too long
```

The reason is simple enough, you have to use single quotes instead of double quotes. But it took me a while to find out this so here it is for all other beginners.

```sql
SQL> create spfile from pfile='/oracle/app/product/12.1.0/dbhome_1/dbs/initORCL.ora';

File created.

SQL>
```