---
title: Trick Windows 8 into creating a RAID10 (striped mirrors) array
author: silviu
type: post
date: 2014-10-31T13:00:35+00:00
url: /2014/10/31/trick-windows-8-into-creating-a-raid10-striped-mirrors-array/
dsq_thread_id:
  - 3176265803
categories:
  - old
tags:
  - raid
  - raid10
  - software
  - temp_on
  - Windows

---
I recently had to upgrade the storage for my desktop and I thought that since I have a few left-over disks I'd try to build a RAID10 array - RAID10 is very cool because it gives performance close to striped arrays but enjoys the reliability of mirrored arrays. Wikipedia has a [nice write-up][1] if you want it.

I had two options - using the motherboard's Intel controller or software RAID. Coming from the Linux world I was expecting software raid to be easy enough to configure - I was wrong apparently in the Windows world options are more limited (mirrors and stripes) with only recently in Windows 8 Storage Spaces offering more options.

In a word Storage Spaces allow building standard (jbod), mirrored (raid1) or parity (raid5) pools and Disk Management allows, using Dynamic Discs allows for the creation of striped or mirrored volumes.

And idea sprang immediately to mind, I fired up a VM to test and it worked, so here they are the full steps to create a striped mirrors array on Windows 8(.1):

1. Go to storage spaces and create a mirrored pool using two of the disks.
![Stoarge Spaces Mirrored Pool](/blog/images/2014/Image.png)
![Stoarge Spaces Creating a  Mirrored Pool](/blog/images/2014/Image-1.png)

2. Repeat using the other disks for another mirror
![Stoarge Spaces Creating a Mirrored Pool](/blog/images/2014/Image-2.png)
![Stoarge Spaces Creating a Mirrored Pool](/blog/images/2014/Image-3.png)

3. You should have now two virtual disks each being essentially a RAID1 array of two drives.
![Storage spaces two mirrored pools](/blog/images/2014/Image-4.png)

4. Go to Disk Management and remove the volumes on each of the virtual disks
![Create](/blog/images/2014/Image-51.png)
![Delete volume on virtual disk](/blog/images/2014/Image-6.png)

5. Create a striped volume using the two, now free. virtual disks.
![Striped volume from mirror pools](/blog/images/2014/Image-7.png)
![Image 8](/blog/images/2014/Image-8.png)
![Image 9](/blog/images/2014/Image-9.png)

6. Done !
![Image 10](/blog/images/2014/Image-10.png)

_**Warning:**_ I didn't test this on the long run, as following some performance tests I decided to go with my motherboard's RAID option. I did test in the virtual machine how it fails when disks are missing and everything appeared to work fine. Though, since I bet this usage scenario is not certified by Microsoft you might encounter issues after updating Windows. As always backup, backup, backup!

[1]: http://en.wikipedia.org/wiki/Nested_RAID_levels
