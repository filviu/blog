---
title: Configuring Mysql in Slackware 13.0
author: silviu
type: post
date: 2009-09-07T16:46:12+00:00
url: /2009/09/07/configuring-mysql-in-slackware-13-0/
dsq_thread_id:
  - 48856805
categories:
  - old
tags:
  - mysql
  - slackware
  - temp_on

---
Slackware 13 has still the same unintuitive style with some things &#8211; i.e. akonadi doesn&#8217;t start in kde and it doesn&#8217;t say why, and so on.

One of the problems you will encounter is that Mysql doesn&#8217;t start. Yes, if you look in /usr/doc/mysql&#8230; you will find the reason.

Here&#8217;s what you have to do:

Run

[ccNe_bash]  
mysql\_install\_db  
[/ccNe_bash]

This will configure the default databases mysql needs to function. Now, this is where you would normally start mysql using /etc/rc.d/rc.mysqld start right? Wrong !

If you try you will get:

[ccNe_bash]  
/etc/rc.d/rc.mysqld start  
nohup: redirecting stderr to stdout  
Starting mysqld daemon with databases from /var/lib/mysql  
STOPPING server from pid file /var/run/mysql/mysql.pid  
090907 19:35:24  mysqld ended  
[/ccNe_bash]

There&#8217;s one more step to take:

[ccNe_bash]  
chown -R mysql:mysql /var/lib/mysql  
[/ccNe_bash]

This gives mysql rights to use it&#8217;s own folder and files.

Now you can start mysql

[ccNe_bash]  
/etc/rc.d/rc.mysqld start  
[/ccNe_bash]

And follow the instructions given by mysql\_install\_db in setting up the root mysql password.

An article explaining why the heck after installing the ATI Proprietary drivers my resolution is stuck in 1600&#215;1200 as opposed to 1680&#215;1050 will follow as soon as I figure it out.