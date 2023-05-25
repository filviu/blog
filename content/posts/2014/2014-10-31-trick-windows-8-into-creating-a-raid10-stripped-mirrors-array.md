---
title: Trick Windows 8 into creating a RAID10 (stripped mirrors) array
author: silviu
type: post
date: 2014-10-31T13:00:35+00:00
url: /2014/10/31/trick-windows-8-into-creating-a-raid10-stripped-mirrors-array/
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
I recently had to upgrade the storage for my desktop and I thought that since I have a few left-over disks I&#8217;d try to build a RAID10 array &#8211; RAID10 is very cool because it gives performance close to striped arrays but enjoys the reliability of mirrored arrays. Wikipedia has a [nice write-up][1] if you want it.

I had two options &#8211; using the motherboard&#8217;s Intel controller or software RAID. Coming from the Linux world I was expecting software raid to be easy enough to configure &#8211; I was wrong apparently in the Windows world options are more limited (mirrors and stripes) with only recently in Windows 8 Storage Spaces offering more options.

In a word Storage Spaces allow building standard (jbod), mirrored (raid1) or parity (raid5) pools and Disk Management allows, using Dynamic Discs allows for the creation of striped or mirrored volumes.

And idea sprang immediately to mind, I fired up a VM to test and it worked, so here they are the full steps to create a striped mirrors array on Windows 8(.1):

  1. Go to storage spaces and create a mirrored pool using two of the disks.[  
][2] [<img decoding="async" loading="lazy" class="aligncenter wp-image-3083 size-full" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image.png" alt="Stoarge Spaces Mirrored Pool" width="874" height="622" />][2][<img decoding="async" loading="lazy" class="aligncenter wp-image-3073 size-full" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-1.png" alt="Stoarge Spaces Creating a  Mirrored Pool" width="874" height="622" />][3]
  2. Repeat using the other disks for another mirror  
    [<img decoding="async" loading="lazy" class="aligncenter wp-image-3074 size-full" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-2.png" alt="Stoarge Spaces Creating a  Mirrored Pool" width="874" height="622" />][4][<img decoding="async" loading="lazy" class="aligncenter wp-image-3075 size-full" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-3.png" alt="Stoarge Spaces Creating a Mirrored Pool" width="874" height="622" />][5]
  3. You should have now two virtual disks each being essentially a RAID1 array of two drives.[<img decoding="async" loading="lazy" class="aligncenter wp-image-3076 size-full" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-4.png" alt="Storage spaces two mirrored pools" width="874" height="1050" />][6]
  4. Go to Disk Management and remove the volumes on each of the virtual disks  
    [<img decoding="async" loading="lazy" class="aligncenter wp-image-3084 size-full" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-51.png" alt="" width="514" height="580" />Create][7][<img decoding="async" loading="lazy" class="aligncenter size-full wp-image-3078" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-6.png" alt="Delete volume on virtual disk" width="759" height="380" />][8]
  5. Create a striped volume using the two, now free. virtual disks.  
    [<img decoding="async" loading="lazy" class="aligncenter size-full wp-image-3079" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-7.png" alt="Striped volume from mirror pools" width="744" height="368" />][9][<img decoding="async" loading="lazy" class="aligncenter size-full wp-image-3080" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-8.png" alt="Image [8]" width="513" height="416" />][10][<img decoding="async" loading="lazy" class="aligncenter size-full wp-image-3081" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-9.png" alt="Image [9]" width="513" height="416" />][11]
  6. Done ![<img decoding="async" loading="lazy" class="aligncenter size-full wp-image-3082" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-10.png" alt="Image [10]" width="268" height="65" />][12]

_**Warning:**_ I didn&#8217;t test this on the long run, as following some performance tests I decided to go with my motherboard&#8217;s RAID option. I did test in the virtual machine how it fails when disks are missing and everything appeared to work fine. Though, since I bet this usage scenario is not certified by Microsoft you might encounter issues after updating Windows. As always backup, backup, backup!

 [1]: http://en.wikipedia.org/wiki/Nested_RAID_levels
 [2]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image.png
 [3]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-1.png
 [4]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-2.png
 [5]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-3.png
 [6]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-4.png
 [7]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-51.png
 [8]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-6.png
 [9]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-7.png
 [10]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-8.png
 [11]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-9.png
 [12]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/Image-10.png