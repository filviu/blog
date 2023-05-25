---
title: Email a list of updates from a Debian server.
author: silviu
type: post
date: 2012-09-28T12:49:40+00:00
url: /2012/09/28/email-a-list-of-updates-from-a-debian-server/
dsq_thread_id:
  - 862899642
categories:
  - old
tags:
  - debian
  - email
  - temp_on
  - updates

---
[<img decoding="async" loading="lazy" class="alignleft size-full wp-image-2319" title="Debian" alt="" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/09/Debian1.png" width="110" height="145" />][1]Do you run remote servers? Me too.

It&#8217;s a good ideea to keep them up to date. On the other hand I don&#8217;t like automatic updates, something might break when you least want or expect it. So I prefer to be notified of updates and choose myself the moment when to apply them. Following is a nice script that sends an email of available updates on a Debian system.  
[cc_bash]  
#!/bin/bash

EMAIL=youremail@example.com

\# Only download updates.  
\# Nothing is installed.  
apt-get -dqq update  
apt-get -dyqq upgrade

upgrades=$(apt-get -s upgrade | grep ^Inst)  
if [ &#8220;$upgrades&#8221; ] ; then  
echo &#8220;$upgrades&#8221; | mail -s &#8220;Updates for $(hostname) on $(date +%Y-%m-%d)&#8221; $EMAIL  
fi  
[/cc_bash]  
Set the above script to run from cron as often as you&#8217;d like to get these notifications.

 [1]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/09/Debian1.png