---
title: Latest openssh disables arcfour and blowfish-cbc
author: silviu
type: post
date: 2014-10-21T10:01:26+00:00
url: /2014/10/21/latest-openssh-disables-arcfour-and-blowfish-cbc/
dsq_thread_id:
  - 3139756499
categories:
  - old
tags:
  - arcfour
  - openssh
  - Security
  - temp_on

---
If you move a lot of data using rsync/scp/ssh you probably found out by now that arcfour or blowfish ciphers are a lot faster than others. A comparison is found in [this thread][1]. (TL;DR arcfou256 is the fastest cipher).

Today I updated openssh on my slackware servers only to be greeted by this error from scripts doing rsync to my backup server:

[cce_bash]  
no matching cipher found: client arcfour server aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com  
rsync: connection unexpectedly closed (0 bytes received so far) [Receiver]  
rsync error: unexplained error (code 255) at io.c(226) [Receiver=3.1.0]  
[/cce_bash]

The openssh [release notes][2] are clear about this:

> Potentially-incompatible changes
> 
> \* sshd(8): The default set of ciphers and MACs has been altered to remove unsafe algorithms. In particular, CBC ciphers and arcfour\* are disabled by default.

I added arcfour256 besides the default ciphers in /etc/ssh/sshd_config in order to fix this:

[cce_bash]  
ciphers arcfour256,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com  
[/cce_bash]

**Warning** as I understand it  arcfour is not as secure as aes ciphers. On modern machines that support hw based aes instructions in theory you shouldn&#8217;t see differences. But I do. For example at home the machine that pushes the most data is an I7 and arcfour is still twice as fast (maybe the windows version of ssh doesn&#8217;t use hw aes acceleration). Since access to the servers where I push this data is limited to the local LAN and VPN I considered acceptable to use a lower quality cipher. It might not be the same for you.

 [1]: https://bbs.archlinux.org/viewtopic.php?id=136713
 [2]: http://www.openssh.com/txt/release-6.7