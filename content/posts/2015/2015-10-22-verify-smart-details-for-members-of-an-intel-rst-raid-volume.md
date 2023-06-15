---
title: Verify SMART details for members of an Intel RST RAID volume
author: silviu
type: post
date: 2015-10-22T06:02:14+00:00
url: /2015/10/22/verify-smart-details-for-members-of-an-intel-rst-raid-volume/
dsq_thread_id:
  - 4247775532
categories:
  - tech
tags:
  - intel
  - raid
  - smart

---
Sooo,

Be it because of the BIOS update to a beta or because of my drives but my RAID10 keeps failing. I [documented before][1] how to repair such a broken array but I didn't want to go ahead with it too many times as data corruption is only one step away. Knowing that at least one of the disks has some minor issues (mdadm kicked it out some time ago when the disks were running under linux) I decided to check smart details and only keep only two of the disks in RAID1. I was curious if one can read SMART details when the disks are still members of the Intel RST array. Since I had all the data off the disks it was safe to test.

{{< figure 
    src="/blog/images/2015/intel_ssd_toolbox_smart_raid.png" 
    alt="screenshot of Intel SSD Drive Toolbox" 
>}}
I found out thet the [Intel SSD Toolbox][2] shows SMART data for all disks in a system, not only SSDs and not only Intel. Look at _Other Drives_ and scroll to the right as under _Intel Solid-State Drives_ it shows the RAID volumes.

 [1]: http://www.sgvulcan.com/2015/10/14/intel-rst-raid-non-raid-disk-after-bios-update/
 [2]: https://www.google.com/?gws_rd=ssl#q=Intel+SSD+toolbox