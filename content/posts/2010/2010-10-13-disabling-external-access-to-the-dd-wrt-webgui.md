---
title: Disabling external access to the DD-WRT WebGui
author: silviu
type: post
date: 2010-10-13T19:42:18+00:00
url: /2010/10/13/disabling-external-access-to-the-dd-wrt-webgui/
dsq_thread_id:
  - 327272333
categories:
  - old
tags:
  - dd-wrt
  - remote
  - temp_on
  - wan. dyndns
  - webgui

---
So, playing with DynDNS and DD-WRT I worryingly observed that even if I set

**Administration->Management->Remote Access->Web GUI Management**

to **off** I can still ****access my router's management WebGui via the external address. That seemed wrong, I was about to set firewall rules to block this unitl I tried from my phone using 3G. The WebGui was inaccessible.

**The WAN WebGui still works from the INSIDE!** But don't worry it won't work from outside your network.