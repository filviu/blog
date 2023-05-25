---
title: Slow ZFS write performance
author: silviu
type: post
date: 2014-01-30T10:26:22+00:00
url: /2014/01/30/slow-zfs-write-performance/
dsq_thread_id:
  - 2200448623
categories:
  - old
tags:
  - bios
  - microserver
  - temp_on
  - write

---
A note to self more than anything.

While I was rebuilding my HP N40L Microserver storage to use new drives and ZFS I experienced very slow (<20MB/s ) First I thought that it was because the source was a degraded RAID5 and performance was lost due to parity. But when the target was a network share instead of the local ZFS pool write speeds went to a more respectable 60-70MB/s.

Since I use more than 4 drives I used the modified BIOS available for this machine that enables lots of extra options, including switching the ODD SATA port to enhanced. I entered the bios and **enabled write caching**.

Sure enough speeds went to ~100MB/s