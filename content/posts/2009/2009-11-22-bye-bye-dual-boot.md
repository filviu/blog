---
title: Bye, bye, dual boot
author: silviu
type: post
date: 2009-11-22T19:10:32+00:00
url: /2009/11/22/bye-bye-dual-boot/
dsq_thread_id:
  - 48858523
categories:
  - old
tags:
  - boot
  - Dual
  - temp_on
  - virtualization

---
Ever since I discovered linux I ran a dual boot system. Linux (usually slackware) + windows (first '98 than, as soon as it was available XP). Windows 98 was problematic because it needed frequent reinstalling, pleasently overwriting the boot sector everytime requiring in turn to reinstall lilo.

Than XP solved this problem (not that it didn't quietly overwrite the boot sector) by needing far less frequent reinstalls. When I found out about vmware I was very happy, dual boot seemed a thing of the past. I don't play games so missing 3d performance was not an issue, the occasional Counter Strike with the friends work's fine on my wife's laptop or in wine. (I was not about to use xp as the host). Well it was not that simple. Performance was sketchy at best, issues and so on made me abandon the idea.  
Recently I ran into the isuee of needing windows 7 and XP besides linux. I was not about to tripleboot and anyway I found myself running wiondows more than linux just because I needed frequent access to some peace of software. So, after a recent upgrade to my main machine I decided to give virtualization another spin. Virtualbox caught my attention because of it's open source nature. I read a few comparative reviews of it compared with vmware and seemed pretty much the same for me so I went with it.  
Between the new processor I have, the sufficent ram and modern virtualizatin software I can safely say that I won't be dual booting anytime soon. Windows 7 seemed to take less time to install under virtualbox than it took live, I also can test new ideeas quickly - it took a whole 10 minutes to test Chrome OS, well the new great revolution from Google seems a whole 10 minutes for me but that's another story. XP runs smoothly, 7 runs smoothly, heck I have Freedos running smoothly. Also now I have no more excuses to postpone playing with open solaris and other systems.  
Conclusion: virtualization has finally got to the point where it is good enough for me. It had it's uses before and I'm sure there are some that still have no use for it yet.  
But if you found yourself rebooting too often lately you might want to decide for a host os (where you need maximum performance) and try to use your other os's as virtual machines. You might find out, just like I did, that given enough RAM virtualization is sufficent. And nothing beats having everything readily available in windows side by side.