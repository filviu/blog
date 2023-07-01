---
title: cPanel IP migration
author: silviu
type: post
date: 2013-03-02T08:25:04+00:00
url: /2013/03/02/cpanel-ip-migration/
categories:
  - old
tags:
  - temp_on

---
I had to switch the main IP address of a cPanel server. Basically you follow the IP Migration Wizard steps, but when I was done the A records for the main hostname were wrong (still having the old IP). If I went to edit the main DNS entry the IP was shown to be correct. What I had to do was to edit `/var/cpanel/mainip`

Also I searched in /etc and found one more refference to the old IP, I replaced that as well.