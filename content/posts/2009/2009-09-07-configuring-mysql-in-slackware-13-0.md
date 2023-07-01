---
title: Configuring Mysql in Slackware 13.0
author: silviu
type: post
date: 2009-09-07T16:46:12+00:00
url: /2009/09/07/configuring-mysql-in-slackware-13-0/
categories:
  - old
tags:
  - mysql
  - slackware
  - temp_on

---
Slackware 13 has still the same unintuitive style with some things - i.e. akonadi doesn't start in kde and it doesn't say why, and so on.

One of the problems you will encounter is that Mysql doesn't start. Yes, if you look in /usr/doc/mysql... you will find the reason.

Here's what you have to do:

Run

```bash
mysql_install_db
```

This will configure the default databases mysql needs to function. Now, this is where you would normally start mysql using /etc/rc.d/rc.mysqld start right? Wrong !

If you try you will get:

```bash
/etc/rc.d/rc.mysqld start
nohup: redirecting stderr to stdout
Starting mysqld daemon with databases from /var/lib/mysql
STOPPING server from pid file /var/run/mysql/mysql.pid
090907 19:35:24  mysqld ended
```

There's one more step to take:

```bash
chown -R mysql:mysql /var/lib/mysql
```

This gives mysql rights to use it's own folder and files.

Now you can start mysql

```bash
/etc/rc.d/rc.mysqld start
```

And follow the instructions given by mysql_install_db in setting up the root mysql password.

An article explaining why the heck after installing the ATI Proprietary drivers my resolution is stuck in 1600&#215;1200 as opposed to 1680&#215;1050 will follow as soon as I figure it out.