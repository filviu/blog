---
title: Load cycle count of Western Digital Green Drives and how to fix it from Linux
author: silviu
type: post
date: 2012-12-20T12:17:08+00:00
url: /2012/12/20/load-cycle-count-of-western-digital-green-drives-and-how-to-fix-it-from-linux/
dsq_thread_id:
  - 984127045
categories:
  - old
tags:
  - count
  - cycle
  - eadx
  - ears
  - idle3-tools
  - linux
  - load
  - raid
  - temp_on
  - wdidle3

---
I run a NAS at home. It used to have 3x2TB WD EARS drives. At some point I saw online some remarks about increased Load Cycle Count when using these drives in a NAS/RAID setup but I didn&#8217;t have the time to check then. Modern Western Digital &#8220;Green&#8221; Drives include the Intellipark feature that stops the disk when not in use.  
Unfortunately, the default timer setting is not perfect on linux/unix systems, including many NAS, and leads to a dramatic increase of the Load Cycle Count value (SMART attribute #193). After a period of 8 seconds of inactivity, these drives heads “park” themselves, or go into standby position. This behavior is fine for desktop storage where the green drive &#8211; which should be used for storage, not OS, could stay in stand-by for hours untill required **but** a RAID will always write to all the disks due to parity ,etc. and so the drives will wake up all the time. This constant stand-by/wake-up cycles are not really a good idea. WD says the drives should be good for 300000 load cycles.

Lately I needed more space and after a failed attempt with a crappy Seagate refurbished external drive (it was the only thin affordable) I bough a new 2Tb EADX WD Green when prices came back to sanity. While installing the new drive I took the time to check the old ones and found worrying values for the load cycle count, over 80000 for the oldest of the three and over 60000 for the others. I installed the new disk, grew the RAID array and setup a cron job to monitor the value over a period of a few days. The rate it was growing proved worrisome. A 24&#215;7 running system will reach the 300000 recommended cycles as soon as 2 years. I had more time as I only run my NAS when I need it &#8211; sometimes is off for days.

Following are graphs detailing the number of loadcycles I see on my four drives. The fifth (SDE) is a WD blue which is used as a system drive, and which doesn&#8217;t use this agressive power saving method.



Values were taken on 4h intervals but are not necessarily continuous &#8211; as the NAS was off some times. Last images shows the number of Load Cycle Counts happened from the last reading.

## The Fix:

The default is to try and park every 8 seconds. Western Digital were kind enough to provide an utility to change the setting: is called “wdidle3”, and since apparently WD does not offer it directly, you have to [google it.][1] The issue is that is&#8217;s a DOS only program and WD only says it works with some drives. (my new EADX was not among them) Users report it to work ok on most drives but adding it to the fact that the NAS runs headless in a closet I would have to get it out, add a keyboard and screen, boot DOS and hope it works. Fortuantely some good sould thought otherwise: <http://idle3-tools.sourceforge.net/>

It&#8217;s an utility that sets the timeout for this  power saving feature in the same way the wdidle3 utility does. The only plus is that it runs on linux. I won&#8217;t show you how I ran it because I want you to read all the documentation the author provides not just blindly copy and paste commands that can potentially ruin your disks. What I will tell you that you need to cycle your drives in order to get the new settings into effect. A reboot is not enough. You need to power them down and back up again.

Just to be sure I continued monitoring the load cycle values for some time more.



I kept the same scale as above so the effect is obvious.

Let me end by repeating what the idle3-tools author says:

_Idle3-tools is an independant project, **unrelated in any way to Western Digital Corp.**_

**WARNING : THIS SOFTWARE IS EXPERIMENTAL AND NOT WELL TESTED. IT ACCESSES LOW LEVEL INFORMATION OF YOUR HARDDRIVE. USE AT YOUR OWN RISK.**

**This did work for me for my WD20EARS and WD20EADX drives but it might not work for you.** Be sure you understand the documentation and check your drive&#8217;s behaviour before and after.

 [1]: http://www.google.com/search?q=wdidle3