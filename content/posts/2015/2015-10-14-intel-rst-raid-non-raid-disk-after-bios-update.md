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
So, having nothing better to do and for no good reason I decided to update my workstation&#8217;s BIOS&nbsp;to the latest version released by Gigabyte. Since ignoring&nbsp;_the &#8220;__If it works don&#8217;t fix it&#8221;&nbsp;_mantra is always a&nbsp;_good_ idea. Beautiful, after update two of my disks from a four disk RAID10 array were showing as Non-RAID Disk. I had backups but shuffling 2TB+ of data is never fun.

Initial reports were all grim, the Intel RST BIOS&nbsp;does not allow repairing. Thankfully a good soul had always found the answer, source thread [here][1]&nbsp;**thank-you** _adamsap_.

_**Usual disclaimer:&nbsp;**_this worked for me, I have no guarantee it will work for you, and the method is not advertised as working and/or suported by Intel

<div class="wp-block-image">
  <figure class="aligncenter size-full"><img decoding="async" loading="lazy" width="900" height="506" src="https://www.silviuvulcan.ro/wp-content/uploads/2021/10/2015-09-13-22.27.07.jpg" alt="" class="wp-image-3841" srcset="https://www.silviuvulcan.ro/wp-content/uploads/2021/10/2015-09-13-22.27.07.jpg 900w, https://www.silviuvulcan.ro/wp-content/uploads/2021/10/2015-09-13-22.27.07-300x169.jpg 300w, https://www.silviuvulcan.ro/wp-content/uploads/2021/10/2015-09-13-22.27.07-768x432.jpg 768w, https://www.silviuvulcan.ro/wp-content/uploads/2021/10/2015-09-13-22.27.07-210x118.jpg 210w" sizes="(max-width: 900px) 100vw, 900px" /></figure>
</div>

  1. Reset the volume (all disks) as non-member from the Intel BIOS. Ignore the warning that all data will be lost. The utility only touches the metadata related to RAID membership.
  2. Create a new array with the all same disks and be sure to use&nbsp;**the same settings** related to strip size, RAID type, etc. I was in luck since my array was still visible since some disks still were attached.
  3. Download TestDisk from&nbsp;<http://www.cgsecurity.org>. I used the Windows version since my Windows install was on a different disk. I never heard of this utility but seems to be really, really useful at data recovery.
  4. Run TestDisk after reading the steps on their site. Be sure to read the documentation there to know what you are doing. In brief (so I&#8217;m sure you read the original docs) you have to: search for your partition(s) on the raid volume &#8211; if everything was recreated with the same settings it should find it quickly in a few seconds &#8211; and save the partition table.
  5. After the partition table is saved reboot.
  6. The array should be back with all the data.

I compared checksums for some of the data against backups and it turns out everything is back.

 [1]: http://forums.extremeoverclocking.com/showpost.php?p=3329132&postcount=6