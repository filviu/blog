---
title: Debian squeeze laptop harddisk restarts every few seconds.
author: silviu
type: post
date: 2012-12-27T11:08:25+00:00
url: /2012/12/27/debian-squeeze-laptop-harddisk-restarts-every-few-seconds/
dsq_thread_id:
  - 994918489
categories:
  - old
tags:
  - laptop drive
  - reset
  - spinup
  - temp_on
  - western digital

---
I installed a miniserver using a 2.5 WD Sata HDD. I noticed that the disk will park shutdown and restart every 10 seconds or so. This was far worse than what happened here: <http://www.sgvulcan.com/load-cycle-count-of-western-digital-green-drives-and-how-to-fix-it-from-linux/>

I'm pretty sure [this bug][1] is the cause but the only mention was that the apm value of 128 didn't work on me. Since this is an always on desktop system I just set it to 254.

For good measure I used the idle3 tools as mentioned in the first link to change that too.

 [1]: https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/952556