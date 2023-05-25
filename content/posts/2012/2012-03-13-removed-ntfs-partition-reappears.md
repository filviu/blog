---
title: Removed ntfs partition reappears
author: silviu
type: post
date: 2012-03-13T08:16:28+00:00
url: /2012/03/13/removed-ntfs-partition-reappears/
dsq_thread_id:
  - 609194483
categories:
  - old
tags:
  - ext2
  - ext3
  - ext4
  - fdisk
  - linux
  - ntfs
  - partition
  - temp_on
  - type
  - Windows

---
So, I was repartitioning a harddrive that used to be a windows disk. I removed the ntfs partition that was spanning the whole drive and created a linux layout instead (two linux partitions and one swap). After writing the partition table the first partition on the disk failed to format. Returning to fdisk I saw that the first partition was still of type NTFS. So I changed the type once more and wrote the partition table to disk. I exited and returned and the type was stubbornly set to ntfs.

The fix was to **zero** the first megabyte of the partition:  
[cce_bash]  
dd if=/dev/zero of=/dev/sdx1 bs=1024k count=1  
[/cce_bash]  
If you don&#8217;t understand the above don&#8217;t run it ! You risk a lot if you mistake the target partition!