---
title: Secondary DNS cannot transfer zone
author: silviu
type: post
date: 2011-11-03T16:14:24+00:00
url: /2011/11/03/secondary-dns-cannot-transfer-zone/
dsq_thread_id:
  - 461078471
categories:
  - old
tags:
  - bind
  - master
  - named
  - secondary
  - slave
  - temp_on

---
I'm no Bind expert but I'm not a beginner either. I was configuring a secondary backup DNS for a master server and I noticed that after configuring everything the zones didn't get replicated on the slave DNS. I checked the logs and saw the following:

First I thought there was a mistake related to a missing permission on the master configuration
```bash
allow-transfer { aaa.bbb.ccc.ddd; };
```
I double checked but the permissions were set correctly. The solution was easier (after finding it) than expected. The folder where the zones would have landed was not writable by the Bind user (**named** in my case)

[cce]
Oct 31 01:43:33 ZAC1A81MGL named[26208]: 31-Oct-2011 01:43:33.167 xfer-in: info: transfer of 'openfreeway.com/IN/internal' from 10.106.178.57#53: Transfer completed: 0 messages, 20 records, 0 bytes, 0.001 secs (0 bytes/sec)
Oct 31 01:43:33 ZAC1A81MGL named[26208]: 31-Oct-2011 01:43:33.168 general: error: dumping master file: internal/tmp-Si8sPK3ZVU: open: permission denied
```
```