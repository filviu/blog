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
Ever happened to you that you create a user with privileges to connect from any host but it won't connect from the localhost?

Like this:

```bash
[root@18969_1_490528 tmp]# mysql -u test_user -puser_pass
ERROR 1045 (28000): Access denied for user 'test_user'@'localhost' (using password: YES)

[root@18969_1_490528 tmp]# mysql -u test_user -puser_pass -h yourhost.com
Welcome to the MySQL monitor.  Commands end with ; or g.
Your MySQL connection id is 55
Server version: 5.0.77 Source distribution

Type 'help;' or 'h' for help. Type 'c' to clear the buffer.

mysql> quit
Bye
```

The problem are the anonymous users created by mysql_install_db on initial setup of mysql. Those take precedence. So either you create your user both as `'test_user'@'%'` and `'test_user'@localhost` either erase those users. I erase them like this as I don't need two set's of users for every user I need:

```sql
mysql> select Host,User from user;
+----------------+--------------+
| Host           | User         |
+----------------+--------------+
| %              | test_user    |
| 127.0.0.1      | root         |
| 18969_1_490528 |              |
| 18969_1_490528 | root         |
| localhost      |              |
| localhost      | root         |
+----------------+--------------+
6 rows in set (0.00 sec)

mysql> delete from user where User=";
Query OK, 2 rows affected (0.00 sec)

mysql> flush privileges;
Query OK, 0 rows affected (0.01 sec)

mysql> select Host,User from user;
+----------------+--------------+
| Host           | User         |
+----------------+--------------+
| %              | test_user    |
| 127.0.0.1      | root         |
| 18969_1_490528 | root         |
| localhost      | root         |
+----------------+--------------+
4 rows in set (0.00 sec)

mysql>
```