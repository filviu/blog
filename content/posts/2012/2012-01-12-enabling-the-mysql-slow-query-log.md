---
title: Enabling the MySQL slow query log
author: silviu
type: post
date: 2012-01-12T16:32:49+00:00
url: /2012/01/12/enabling-the-mysql-slow-query-log/
dsq_thread_id:
  - 536348202
categories:
  - old
tags:
  - log_slow_query
  - mysql
  - query
  - slow
  - temp_on

---
<img decoding="async" loading="lazy" class="alignleft wp-image-1996 size-medium" title="Logo-mysql" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/Logo-mysql-300x219.jpg" alt="" width="300" height="219" />If you have a slow web app or website it might be because of unoptimized sql queries. You want to track and fix those and the mysql slow query log is very helpful here.

### Enabling the slow query log

MySQL prior to 5.1.0 requires adding a setting to the MySQL my.cnf file and restart the mysql daemon in order to log slow queries; from MySQL 5.1.0 onwards you can also change this dynamically without having to restart.

To make the setting permanent every time you start MySQL (or you have a version prior to 5.1.0) add (ow uncomment) the following in my.cnf (usually /etc/my.cnf or /etc/mysql/my.cnf)
```bash
log_slow_queries = /var/log/mysql/mysql-slow.log
```
You can skip the path or leave it blank completely and mysql will create the log in the default location. The default is to log the queries into a file in the MySQL data directory.

To enable or disable the setting dynamically in MySQL 5.1.0 run the following query to enable it:
```bash
set log_slow_queries = ON;
```
and to disable it:
```bash
set log_slow_queries = OFF;
```

### Changing the long query time

You can also set how long a query needs to take before it's considered a "long" query. The default is 10 seconds. I usually like to set it lower:

To change it to 5 seconds add in my.cnf:
```bash
long_query_time = 5
```
This can be changed dynamically in MySQL 5.0.0+ (and possibly earlier versions) by running the following query:
```bash
set global long_query_time = 5;
```
This will only work for new connections; any connections which have already been established will continue to use the old setting. Once the user disconnects and reconnects their new connection will use the new setting.

### Errors you can get applying these settings dynamically

If the following error message appears when attempting to change the log_slow_queries setting dynamically means you are using a version of MySQL that does not support changing the setting dynamically:
[cceN_mysql]
ERROR 1193 (HY000): Unknown system variable 'log_slow_queries'
[/cceN_mysql]
The long_query_time value must be integer; if it's not (e.g. you set long_query_time = 2.5;) then you'll see this error:
[cceN_mysql]
#1232 - Incorrect argument type to variable 'long_query_time'
[/cceN_mysql]
Note also that if you set the long_query_time to 0 it will not fail, but the actual setting applied will be 1 and not 0.