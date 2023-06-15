---
title: Intel RST RAID Non-RAID Disk after BIOS update
author: silviu
type: post
date: 2015-10-14T06:06:33+00:00
url: /2015/10/14/intel-rst-raid-non-raid-disk-after-bios-update/
dsq_thread_id:
  - 4223267651
categories:
  - tech
tags:
  - bios
  - failed
  - intel
  - raid
  - repair
  - rst

---
So, having nothing better to do and for no good reason I decided to update my workstation's BIOS to the latest version released by Gigabyte. Since ignoring _the "__If it works don't fix it" _mantra is always a _good_ idea. Beautiful, after update two of my disks from a four disk RAID10 array were showing as Non-RAID Disk. I had backups but shuffling 2TB+ of data is never fun.

Initial reports were all grim, the Intel RST BIOS does not allow repairing. Thankfully a good soul had always found the answer, source thread [here][1] **thank-you** _adamsap_.

_**Usual disclaimer: **_this worked for me, I have no guarantee it will work for you, and the method is not advertised as working and/or suported by Intel

{{< figure 
    src="/blog/images/2015/bios-non-raid.jpg"
    alt="Image of BIOS screen showing the problem disks" 
>}}
1. Reset the volume (all disks) as non-member from the Intel BIOS. Ignore the warning that all data will be lost. The utility only touches the metadata related to RAID membership.
2. Create a new array with the all same disks and be sure to use **the same settings** related to strip size, RAID type, etc. I was in luck since my array was still visible since some disks still were attached.
3. Download TestDisk from <http://www.cgsecurity.org>. I used the Windows version since my Windows install was on a different disk. I never heard of this utility but seems to be really, really useful at data recovery.
4. Run TestDisk after reading the steps on their site. Be sure to read the documentation there to know what you are doing. In brief (so I'm sure you read the original docs) you have to: search for your partition(s) on the raid volume - if everything was recreated with the same settings it should find it quickly in a few seconds - and save the partition table.
5. After the partition table is saved reboot.
6. The array should be back with all the data.

I compared checksums for some of the data against backups and it turns out everything is back.

 [1]: http://forums.extremeoverclocking.com/showpost.php?p=3329132&postcount=6