---
title: Mysql authentication issues
author: silviu
type: post
date: 2011-01-12T12:57:47+00:00
url: /2011/01/12/mysql-authentication-issues/
dsq_thread_id:
  - 330841120
categories:
  - old
tags:
  - anonymous
  - localhost
  - mysql
  - remote
  - temp_on

---
Ever happened to you that you create a user with privileges to connect from any host but it won&#8217;t connect from the localhost?

Like this:  
[cceN_bash]  
[root@18969\_1\_490528 tmp]# mysql -u test\_user -puser\_pass  
ERROR 1045 (28000): Access denied for user &#8216;test_user&#8217;@&#8217;localhost&#8217; (using password: YES)

[root@18969\_1\_490528 tmp]# mysql -u test\_user -puser\_pass -h yourhost.com  
Welcome to the MySQL monitor.  Commands end with ; or g.  
Your MySQL connection id is 55  
Server version: 5.0.77 Source distribution

Type &#8216;help;&#8217; or &#8216;h&#8217; for help. Type &#8216;c&#8217; to clear the buffer.

mysql> quit  
Bye  
[/cceN_bash]  
The problem are the anonymous users created by mysql\_install\_db on initial setup of mysql. Those take precedence. So either you create your user both as &#8216;test\_user&#8217;@&#8217;%&#8217; and &#8216;test\_user&#8217;@localhost either erase those users. I erase them like this as I don&#8217;t need two set&#8217;s of users for every user I need:

[cceN_mysql]  
mysql> select Host,User from user;  
+&#8212;&#8212;&#8212;&#8212;&#8212;-+&#8212;&#8212;&#8212;&#8212;&#8211;+  
| Host           | User         |  
+&#8212;&#8212;&#8212;&#8212;&#8212;-+&#8212;&#8212;&#8212;&#8212;&#8211;+  
| %              | test_user  |  
| 127.0.0.1      | root         |  
| 18969\_1\_490528 |              |  
| 18969\_1\_490528 | root         |  
| localhost      |              |  
| localhost      | root         |  
+&#8212;&#8212;&#8212;&#8212;&#8212;-+&#8212;&#8212;&#8212;&#8212;&#8211;+  
6 rows in set (0.00 sec)

mysql> delete from user where User=&#8221;;  
Query OK, 2 rows affected (0.00 sec)

mysql> flush privileges;  
Query OK, 0 rows affected (0.01 sec)

mysql> select Host,User from user;  
+&#8212;&#8212;&#8212;&#8212;&#8212;-+&#8212;&#8212;&#8212;&#8212;&#8211;+  
| Host           | User         |  
+&#8212;&#8212;&#8212;&#8212;&#8212;-+&#8212;&#8212;&#8212;&#8212;&#8211;+  
| %              | test_user  |  
| 127.0.0.1      | root         |  
| 18969\_1\_490528 | root         |  
| localhost      | root         |  
+&#8212;&#8212;&#8212;&#8212;&#8212;-+&#8212;&#8212;&#8212;&#8212;&#8211;+  
4 rows in set (0.00 sec)

mysql>  
[/cceN_mysql]