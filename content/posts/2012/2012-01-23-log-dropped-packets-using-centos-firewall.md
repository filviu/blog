---
title: Log dropped packets using CentOS Firewall
author: silviu
type: post
date: 2012-01-23T07:16:42+00:00
url: /2012/01/23/log-dropped-packets-using-centos-firewall/
dsq_thread_id:
  - 549370020
categories:
  - old
tags:
  - centos
  - dropped
  - firewall
  - log
  - network
  - packets
  - temp_on

---
Please take care modifying your firewall. If you don't understand what's being done here you may lock yourself out of your machine. You've been warned 🙂 !

In order to log dropped packets on the INPUT chain I replaced this:  
[cceN_bash]  
-A INPUT -i eth0 -j REJECT -reject-with icmp-host-prohibited  
[/cceN_bash]  
with this  
[cce_bash]  
-N LOGDROP  
-A LOGDROP -i eth0 -j LOG  
-A LOGDROP -i eth0 -j REJECT -reject-with icmp-host-prohibited  
-A INPUT -i eth0 -j LOGDROP  
[/cce_bash]  
Of course you can use DROP instead of REJECT -reject-with icmp-host-prohibited