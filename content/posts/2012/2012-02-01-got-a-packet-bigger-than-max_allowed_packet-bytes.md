---
title: Got a packet bigger than ‘max_allowed_packet’ bytes
author: silviu
type: post
date: 2012-02-01T09:02:49+00:00
url: /2012/02/01/got-a-packet-bigger-than-max_allowed_packet-bytes/
dsq_thread_id:
  - 559980019
categories:
  - old
tags:
  - database
  - error
  - import
  - mysq
  - temp_on

---
I got this on a newly installed server when I tried to import a database:
```bash
[root@host ~]# mysql -u user -pPassword database < database.sql
Enter password:
ERROR 1153 (08S01) at line 53: Got a packet bigger than 'max_allowed_packet' bytes
```

It's easily fixable. The default is probably 16M, I added the following in /etc/my.cnf
[cceN_bash]
max_allowed_packet=32M
[/cceN_bash]

And restarted mysql (depending on your distro you will do this differently):
[cceN_bash]
service mysqld restart
[/cceN_bash]