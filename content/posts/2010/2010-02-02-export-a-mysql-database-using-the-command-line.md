---
title: Export a MySQL database using the command line.
author: silviu
type: post
date: 2010-02-02T07:16:55+00:00
url: /2010/02/02/export-a-mysql-database-using-the-command-line/
dsq_thread_id:
  - 338476766
categories:
  - old
tags:
  - command
  - export
  - mysql
  - script
  - temp_on

---
<img decoding="async" loading="lazy" class="alignleft size-full wp-image-711" title="logo-mysql-110x57" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/02/logo-mysql-110x57.png" alt="" width="110" height="57" />Sometimes it's easier to just drop to the command line then browse for fancy tools like phpMyAdmin. This is useful, especially for quick jobs.
```bash
mysqldump -u user -ppassword your_database > database_backup.sql
```
Of course you need to replace:

  * user - mysql username
  * password - the password
  * your_database - the database you want to backup

Adding -h host.domain.com would allow to backup a remote mysql database from YOUR shell, something like this:
```bash
mysqldump -u user -h host.domain.com -ppassword your_database > database_backup.sql
```