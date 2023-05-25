---
title: Drop all databases from mysql
author: silviu
type: post
date: 2012-03-21T09:25:16+00:00
url: /2012/03/21/drop-all-databases-from-mysql/
dsq_thread_id:
  - 619466543
categories:
  - old
tags:
  - databases
  - drop
  - mysql
  - temp_on

---
Sometimes I need to clean a mysql server so I can re-import it clean from the backups. A DROP ALL DATABASES; would have been nice, but the following does the trick. It will drop all databases except for mysql, test and information_schema  
[cce_bash]  
mysql -uroot -pPASS  -e &#8220;show databases&#8221; | grep -v Database | grep -v mysql| grep -v information_schema| grep -v test | gawk &#8216;{print &#8220;drop database &#8221; $1 &#8220;;&#8221;}&#8217; | mysql -uroot -pPASS</pre> 

[/cce_bash]

**Warning:**  
It does what it says on the tin. It will DROP all your databases, no warnings, no confirmations!

&nbsp;