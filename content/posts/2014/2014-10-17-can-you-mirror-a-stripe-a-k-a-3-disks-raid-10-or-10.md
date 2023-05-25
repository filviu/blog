---
title: Can you mirror a stripe? (a.k.a. 3 disks raid 10 or 1+0)
author: silviu
type: post
date: 2014-10-17T12:38:52+00:00
url: /2014/10/17/can-you-mirror-a-stripe-a-k-a-3-disks-raid-10-or-10/
dsq_thread_id:
  - 3126606775
categories:
  - old
tags:
  - linux
  - mirror
  - raid
  - stripe
  - temp_on

---
TL;DR Yes you can assemble a md device from a stripe and a disk.

**Please don&#8217;t shoot! 🙂** I&#8217;m doing this on a testing server, I don&#8217;t have any idea about the long term stability and/or reliability and I don&#8217;t care this is a personal testing server. I wouldn&#8217;t do this (at least yet) on a production server.

The why, what and how below:

I am looking to assemble a &#8220;Frankenstein&#8221; virtualization server (i.e. use various existing devices). Among many issues to regard is the fact that I will be using multiple size drives, and some of the times these would be old and not that fast.

I thought of using a RAID0 to speed-up VMs but this means it would have to be backed up and it would add complexity. I don&#8217;t have enough same size disks to create a RAID10 and I don&#8217;t want to manage sync scripts for a testing server. By chance I have two 320G disks and one 640G and two 500GB disks and one 1TB. So I thought of the following. Create a RAID0 and mirror that with a double-the-size disk. I tested that in a virtual machine and it turns out it works just fine:

[cce_bash]  
root@v_slackware64c:~# mdadm &#8211;create &#8211;verbose /dev/md0 &#8211;level=stripe &#8211;raid-devices=2 /dev/sdb /dev/sdc  
mdadm: chunk size defaults to 512K  
mdadm: Defaulting to version 1.2 metadata  
mdadm: array /dev/md0 started.  
root@v_slackware64c:~#  mdadm &#8211;create &#8211;verbose /dev/md1 &#8211;level=mirror &#8211;raid-devices=2 &#8211;bitmap=internal &#8211;write-behind /dev/md0 &#8211;write-mostly /dev/sdd  
mdadm: /dev/md0 appears to be part of a raid array:  
level=raid1 devices=2 ctime=Fri Oct 17 11:26:15 2014  
mdadm: Note: this array has metadata at the start and  
may not be suitable as a boot device.  If you plan to  
store &#8216;/boot&#8217; on this device please ensure that  
your boot-loader understands md/v1.x metadata, or use  
&#8211;metadata=0.90  
mdadm: size set to 8383424K  
Continue creating array? y  
mdadm: Defaulting to version 1.2 metadata  
mdadm: array /dev/md1 started.  
root@v_slackware64c:~# cat /proc/mdstat  
Personalities : \[linear\] \[raid0\] \[raid1\] \[raid10\] \[raid6\] \[raid5\] \[raid4\] \[multipath\]  
md1 : active raid1 sdd\[1\](W) md0[0]  
8383424 blocks super 1.2 \[2/2\] \[UU\]  
[==========>&#8230;&#8230;&#8230;.]  resync = 51.2% (4296704/8383424) finish=0.3min speed=204604K/sec  
bitmap: 1/1 pages [4KB], 65536KB chunk

md0 : active raid0 sdc[1] sdb[0]  
8387584 blocks super 1.2 512k chunks

unused devices: <none>

[/cce_bash]

Let&#8217;s see what I did above:

 **mdadm &#8211;create &#8211;verbose /dev/md0 &#8211;level=stripe &#8211;raid-devices=2 /dev/sdb /dev/sdc**

<p style="padding-left: 30px">
  Creates the md0 stripe (raid 0) device using whole disks sdb and sdc
</p>

**mdadm &#8211;create &#8211;verbose /dev/md1 &#8211;level=mirror &#8211;raid-devices=2 &#8211;bitmap=internal &#8211;write-behind /dev/md0 &#8211;write-mostly /dev/sdd**

<p style="padding-left: 30px">
  Creates the md1 mirror (raid 1) device using the md0 array created before and the whole disk sdd.
</p>

<p style="padding-left: 30px">
  <strong>&#8211;bitmap=internal</strong> &#8211; creates an internal (stored with the metadata) write intent bitmap
</p>

<p style="padding-left: 30px">
  <strong>&#8211;write-behind</strong> &#8211; specify that write-behind mode should be enabled (valid for RAID1 only).
</p>

<p style="padding-left: 30px">
  <strong>&#8211;write-mostly</strong> &#8211; yhis is only valid for RAID1 and means that the &#8216;md&#8217; driver will avoid reading from these devices if possible; i.e. try to use the raid0 stripe for reading (faster) as much as possible
</p>

I will let you know how secure/robust this proves in the end. Considering this is a testing server I&#8217;m not that worried.