---
title: Apache 2.2 will not serve corectly from CIFS mounted share
author: silviu
type: post
date: 2010-07-27T09:09:40+00:00
url: /2010/07/27/apache-2-2-will-not-serve-corectly-from-cifs-mounted-share/
dsq_thread_id:
  - 326479366
categories:
  - old
tags:
  - apache
  - cifs
  - mount
  - network
  - share
  - smbfs
  - symlink
  - temp_on

---
I have a home server I use for all kinds of stuff when I&#8217;m away. I have set it up recently so that it can serve a folder mounted over the network from a Windows machine.

_And this is where the fun started!_

The folders and files appear correctly, I can navigate and I can download them. Only that the files, even if apparently having the same size are corrupted. I checked the **_FollowSymLinks_** and as expected was set as required. I tried wget in the command prompt to see if I could find some enlightment but I got the following errors:  
[ccNe_bash]  
wget http://192.xxx.xxx.xxx/windowsshare/folder/file.jpg  
&#8211;09:18:00&#8211; http://192.xxx.xxx.xxx/windowsshare/folder/file.jpg  
=> \`file.jpg&#8217;  
Connecting to 127.0.0.1:80&#8230; connected.  
HTTP request sent, awaiting response&#8230; 200 OK  
Length: 763,685 (746K) [image/jpeg]

0%  
[ ]  
0 &#8211;.&#8211;K/s

09:18:00 (0.00 B/s) &#8211; Connection closed at byte 0. Retrying.

&#8211;09:18:01&#8211; http://192.xxx.xxx.xxx/windowsshare/folder/file.jpg  
(try: 2) => \`file.jpg&#8217;  
Connecting to 127.0.0.1:80&#8230; connected.  
HTTP request sent, awaiting response&#8230; 200 OK  
Length: 763,685 (746K) [image/jpeg]  
file.jpg has sprung into existence.  
Retrying.

&#8211;09:18:03&#8211; http://192.xxx.xxx.xxx/windowsshare/folder/file.jpg  
(try: 3) => \`file.jpg.1&#8242;  
Connecting to 127.0.0.1:80&#8230; connected.  
HTTP request sent, awaiting response&#8230; 200 OK  
Length: 763,685 (746K) [image/jpeg]

0%  
[ ]  
0 &#8211;.&#8211;K/s  
[/ccNe_bash]  
and it will continue like this creating empty files.

Especial the **has sprung into existence** baffled me. Also note that symlinking any other folder, even mounted as **smbfs** instead of **cifs** worked perfectly. At this point changing the mount to smbfs would have solved my problem but curiosity was stronger.

As it turns either apache or (more likely) the cifs driver has a bug. You can work around it by setting the following inside your apache configuration.  
[ccNe_apache]  
EnableSendfile off  
[/ccNe_apache]  
Further upgrades will probably eradicate this problem.