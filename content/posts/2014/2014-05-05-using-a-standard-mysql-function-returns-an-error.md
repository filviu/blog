---
title: Using a standard mysql function returns an error
author: silviu
type: post
date: 2014-05-05T05:44:19+00:00
url: /2014/05/05/using-a-standard-mysql-function-returns-an-error/
categories:
  - old
tags:
  - error
  - function
  - import
  - mysq
  - temp_on

---
While running some mysql scripts I suddenly hit the following error:

```sql
ERROR 1305 (42000) at line 1: FUNCTION somedatabase.find_in_set does not exist
```

Since find_in_set is a standard function I was kind of puzzled, especially since I ran the same script before on some other servers without error.  Checking the SQL script I found the issue:

I had
```sql
update [blah blah] where find_in_set (id,(select [more blah[)) from [rest of blag];
```
and it has to be
```sql
update [blah blah] where find_in_set(id,(select [more blah[)) from [rest of blag];
```
Notice the space between the function and the opening parenthesis. At least this was the issue on the mysql version shipping with the latest CentOS 5.x; the same query worked on a CentOS 6.x mysql returning only a warning.