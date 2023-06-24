---
title: Whitelist a host when using denyhosts
author: silviu
type: post
date: 2010-03-26T16:55:02+00:00
url: /2010/03/26/whitelist-a-host-when-using-denyhosts/
dsq_thread_id:
  - 326525521
categories:
  - old
tags:
  - temp_on

---
![denyhosts](/blog/images/2010/denyhosts.jpg) I'm using this excellent tool on my hosting server called [denyhosts](http://denyhosts.sourceforge.net/). It basically scans trough auth.log for repeated failed attempts to login in order to block brute force attackers. It can also get a list of offending ip-s from other usesrs of DenyHosts who configured their instalation to share attacker ip's. All nice and well until you mistype your password one to many times. Or 127.0.0.1 gets added to the list like it happened today for me. So, you need to add a few ip's to a whitelist.

It's easy. Create a file called `allowed-hosts` in `/var/lib/denyhosts` or whatever you set your work dir for. Inside this file you can list ip's that should be whitelisted.
