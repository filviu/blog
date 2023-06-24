---
title: Nagios Grapher fun
author: silviu
type: post
date: 2010-10-06T15:52:38+00:00
url: /2010/10/06/nagios-grapher-fun/
dsq_thread_id:
  - 327439427
categories:
  - old
tags:
  - grapher
  - nagios
  - nagiosgraph
  - perl
  - rrdtool
  - temp_on

---
![NagiosMonitorIcon](/blog/images/2010/NagiosMonitorIcon.png) I was struggling with Nagios Grapher (or was it nagiosgraph - I tested both)  in Slackware 13.1 After installing all dependencies it would still refuse to work. I tracked the problem pretty easy to be related to Perl not being able to load the **librrd.so.4** library.

That was funny as I was sure that I did configure, make and make install the latest version. Well, by default, on slackware at least rrdtool installs in `/opt` !
I added `/opt/rrdtool-x.x/lib` in `/etc/ld.so.conf`  (check to see what is the exact path in your case) and re-ran ldconfig. Sure enough everything worked fine.

This is the error log I received:

```apacheconf
[Tue Oct 05 14:24:11 2010] [error] [client 127.0.0.1] Premature end of
script headers: show.cgi
[Tue Oct 05 14:28:04 2010] [error] [client 127.0.0.1] Can't load
'/usr/lib64/perl5/site_perl/5.10.1/x86_64-linux-thread-multi/auto/RRDs/RRDs.so'
for module RRDs: librrd.so.4: cannot open shared object file: No such
file or directory at
/usr/lib64/perl5/5.10.1/x86_64-linux-thread-multi/DynaLoader.pm line
200.
[Tue Oct 05 14:28:04 2010] [error] [client 127.0.0.1] at
/usr/local/nagiosgraph/etc/ngshared.pm line 27
[Tue Oct 05 14:28:04 2010] [error] [client 127.0.0.1] Compilation
failed in require at /usr/local/nagiosgraph/etc/ngshared.pm line 27.
[Tue Oct 05 14:28:04 2010] [error] [client 127.0.0.1] BEGIN
failed-compilation aborted at /usr/local/nagiosgraph/etc/ngshared.pm
line 27.
[Tue Oct 05 14:28:04 2010] [error] [client 127.0.0.1] Compilation
failed in require at /usr/local/nagios/sbin/show.cgi line 13.
[Tue Oct 05 14:28:04 2010] [error] [client 127.0.0.1] BEGIN
failed-compilation aborted at /usr/local/nagios/sbin/show.cgi line
13.
[Tue Oct 05 14:28:04 2010] [error] [client 127.0.0.1] Premature end of
script headers: show.cgi
[Tue Oct 05 14:28:06 2010] [error] [client 127.0.0.1] Can't load
'/usr/lib64/perl5/site_perl/5.10.1/x86_64-linux-thread-multi/auto/RRDs/RRDs.so'
for module RRDs: librrd.so.4: cannot open shared object file: No such
file or directory at
/usr/lib64/perl5/5.10.1/x86_64-linux-thread-multi/DynaLoader.pm line
200.
[Tue Oct 05 14:28:06 2010] [error] [client 127.0.0.1] at
/usr/local/nagiosgraph/etc/ngshared.pm line 27
[Tue Oct 05 14:28:06 2010] [error] [client 127.0.0.1] Compilation
failed in require at /usr/local/nagiosgraph/etc/ngshared.pm line 27.
[Tue Oct 05 14:28:06 2010] [error] [client 127.0.0.1] BEGIN
failed-compilation aborted at /usr/local/nagiosgraph/etc/ngshared.pm
line 27.
[Tue Oct 05 14:28:06 2010] [error] [client 127.0.0.1] Compilation
failed in require at /usr/local/nagios/sbin/show.cgi line 13.
[Tue Oct 05 14:28:06 2010] [error] [client 127.0.0.1] BEGIN
failed-compilation aborted at /usr/local/nagios/sbin/show.cgi line
13.
[Tue Oct 05 14:28:06 2010] [error] [client 127.0.0.1] Premature end of
script headers: show.cgi
```