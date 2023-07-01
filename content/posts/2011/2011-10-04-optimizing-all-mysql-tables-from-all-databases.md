---
title: Optimizing all mysql tables (from all databases)
author: silviu
type: post
date: 2011-10-04T06:44:55+00:00
url: /2011/10/04/optimizing-all-mysql-tables-from-all-databases/
categories:
  - old
tags:
  - automatically
  - databases
  - mysql
  - optimize
  - tables
  - temp_on

---
You want to optimize mysql tables from time to time in order to reduce fragmentation. Here's an easy way to do it automatically (put it in a script and run it from cron for example)

```bash
mysqlcheck -Aop -h hostname -u user -pPASSWORD
```

What all those mean:

- `-all-databases, -A`; Check all tables in all databases. This is the same as using the -databases option and naming all the databases on the command line.
- `-optimize, -o` Optimize the tables.
- `-h` host to optimize (you can skip if it's the localhost)
- `-u` mysql user
- `-p` the password