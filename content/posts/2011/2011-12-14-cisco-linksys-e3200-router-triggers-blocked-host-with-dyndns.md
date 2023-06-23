---
title: Cisco (Linksys) E3200 router triggers blocked host with DynDNS
author: silviu
type: post
date: 2011-12-14T11:11:54+00:00
url: /2011/12/14/cisco-linksys-e3200-router-triggers-blocked-host-with-dyndns/
dsq_thread_id:
  - 504079131
categories:
  - old
tags:
  - abuse
  - blocked
  - cisco
  - dyndns
  - e3200
  - linksys
  - temp_on

---
![linksys_e3200](/blog/images/2011/linksys_e32001.jpg) I finally had to upgrade my home router from an aging WRT54GL and went (despite missing dd-wrt for now) with the Linksys E3200. I installed yesterday including dyndns support because I sometimes access my home network when away. I was surprised to receive an email from dyndns this morning stating that my host has been blocked because of abuse. It was strange since my connection is stable and even though some routers have flaky dyndns update clients linksys didn't disappoint me until now...

I do have the latest firmware version so no help there. I browsed a bit around and I found out that others share my issues including owners of the more expensive e4200.

Somebody was brave enough to fight tech support until escalated and got a useful [response][1] (I'm pasting the relevant part here):

> If you have the DDNS server active, every time you hit the save settings button on ANY page of the router GUI, it refreshes all of the settings - which includes re-updating DynDNS even if the IP address hasn't changed.

That's not nice of them, I really hope this will be fixed in a future firmware update. I fiddle with my configuration from time to time and I'm sure next time I'll forget to disable dyndns before changing settings.

I know that I'm just quoting from a forum but I want a copy of the sollution here, otherwise next time I change the settings I won't know why my host gets blocked 🙂

 [1]: http://homecommunity.cisco.com/t5/Wireless-Routers/E4200-causing-DynDNS-Abuse/m-p/402713#M203884