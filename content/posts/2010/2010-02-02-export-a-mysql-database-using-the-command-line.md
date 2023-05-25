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
<img decoding="async" loading="lazy" class="alignleft size-full wp-image-711" title="logo-mysql-110x57" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/02/logo-mysql-110x57.png" alt="" width="110" height="57" />Sometimes it&#8217;s easier to just drop to the command line then browse for fancy tools like phpMyAdmin. This is useful, especially for quick jobs.  
[ccNe_bash]  
mysqldump -u user -ppassword your\_database > database\_backup.sql  
[/ccNe_bash]  
Of course you need to replace:

  * user &#8211; mysql username
  * password &#8211; the password
  * your_database &#8211; the database you want to backup

Adding -h host.domain.com would allow to backup a remote mysql database from YOUR shell, something like this:  
[ccNe_bash]  
mysqldump -u user -h host.domain.com -ppassword your\_database > database\_backup.sql  
[/ccNe_bash]