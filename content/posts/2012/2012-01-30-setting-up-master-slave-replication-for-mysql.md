---
title: Setting up master-slave replication for mysql
author: silviu
type: post
date: 2012-01-30T19:27:08+00:00
url: /2012/01/30/setting-up-master-slave-replication-for-mysql/
dsq_thread_id:
  - 558066582
categories:
  - old
tags:
  - backup
  - master
  - mysql
  - replication
  - slave
  - slow
  - temp_on

---
&nbsp;

So, I had to set-up master-slave replication. Here&#8217;s how you do it:

Why would one want to set-up this? Easy.

1)Spread the read load across multiple servers:  you can use the MySQL master for writing (inserts, updates) and the slave(s) for reading (SELECT) This should speed up things nicely for your application.

2)Do the backups from the slave. You might have noticed that backing-up, especially big databases, slows things down. That happens because mysqldump locks tables as it reads them. This can slow a big site or even takes it down from a few seconds to a few minute. Reading from the slave affects nothing. You can even stop the slave, read the /var/lib/mysql folder and start it back.

Following are the steps on how to set it up, but first let&#8217;s not a few assumptions. Also please note that this sets up only the basic things. Many more settings can be tweaked to improve MySQL performance.

> Master server ip: 192.168.0.1  
> Slave server ip: 192.168.0.2  
> Slave username: slaveusr  
> Slave pw: slavepass  
> Your data directory is: /var/lib/mysql

Add the following lines in your master my.cnf file under [mysqld] section:

[cce]  
\# master my.cnf  
server-id = 1  
relay-log = /var/lib/mysql/mysql-relay-bin  
relay-log-index = /var/lib/mysql/mysql-relay-bin.index  
log-error = /var/lib/mysql/mysql.err  
master-info-file = /var/lib/mysql/mysql-master.info  
relay-log-info-file = /var/lib/mysql/mysql-relay-log.info  
datadir = /var/lib/mysql  
log-bin = /var/lib/mysql/mysql-bin  
\# end master   
[/cce]

The following settings are for the slave’s my.cnf under the same [mysqld] section:  
[cce]  
\# slave&#8217;s my.cnf  
server-id = 2  
relay-log = /var/lib/mysql/mysql-relay-bin  
relay-log-index = /var/lib/mysql/mysql-relay-bin.index  
log-error = /var/lib/mysql/mysql.err  
master-info-file = /var/lib/mysql/mysql-master.info  
relay-log-info-file = /var/lib/mysql/mysql-relay-log.info  
datadir = /var/lib/mysql  
\# end slave settings  
[/cce]  
Restart both mysql instances after changing the settings in my.cnf

Create the slave user on master server:  
[cceN]  
mysql> grant replication slave on \*.\* to slaveusr@&#8217;10.0.0.2&#8242; identified by &#8216;slavepass&#8217;;  
[/cceN]  
Dump the full data and copy it (scp, etc.) to the slave

[cceN]  
mysqldump -u root -pROOTPASS &#8211;all-databases &#8211;single-transaction &#8211;master-data=1 > masterdump.sql  
[/cceN]

import this dump on the slave server:

[cceN]  
mysql -u root -pROOTPASS < masterdump.sql  
[/cceN]

After dump is imported go in to mysql client by typing mysql. Let us tell the slave which master to connect to and what login/password to use:  
[cceN]  
mysql> CHANGE MASTER TO MASTER\_HOST=&#8217;192.168.0.1&#8242;, MASTER\_USER=&#8217;slaveusr&#8217;, MASTER_PASSWORD=&#8217;slavepass&#8217;;  
[/cceN]

Start the slave:  
[cceN]  
mysql> start slave;  
[/cceN]  
&nbsp;

Check the status on the slave:  
[cceN]  
mysql> show slave statusG  
[/cceN]  
The last row will tell how many seconds the slave runs behind the master. No worries if it&#8217;s not 0, it should catch up quickly (at that time it will show Seconds\_Behind\_Master: 0) If it reads NULL, maybe the slave is not started (you can start by typing: start slave) or it could be that there is a problem(shows up in Last\_errno: and Last\_error under show slave status).