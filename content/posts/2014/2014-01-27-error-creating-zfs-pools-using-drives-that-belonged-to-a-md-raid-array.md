---
title: Error creating zfs pools using drives that belonged to a md raid array
author: silviu
type: post
date: 2014-01-27T06:37:23+00:00
url: /2014/01/27/error-creating-zfs-pools-using-drives-that-belonged-to-a-md-raid-array/
categories:
  - old
tags:
  - array
  - mdadm
  - temp_on
  - zfs

---
While migrating a file server from mdadm software raid to zfs I encountered the following error while creating the pool:

```bash
zpool create -f tank mirror /dev/disk/by-id/xxx /dev/disk/by-id/yyy
the kernel failed to rescan the partition table: 16
cannot label 'sdb': try using parted(8) and then provide a specific slice: -1
```

Even if the old mdadm array was no longer being mounted (as more than one disk was missing and it was a raid5) they were still being added to md0:

```bash
cat /proc/mdstat
Personalities : [linear] [raid0] [raid1] [raid10] [raid6] [raid5] [raid4] [multipath]
md0 : inactive sdd1[4](S) sdb1[1](S)
3907025072 blocks super 1.2

unused devices:
```

The fix was easy enough:

```bash
mdadm -stop /dev/md0
mdadm: stopped /dev/md0
zpool create -f tank mirror /dev/disk/by-id/xxx /dev/disk/by-id/yyy
zpool status
pool: tank
state: ONLINE
scan: none requested
[...]
```

`zpool label clear` was mentioned as a fix for this error and I tried that without success before realizing that the drives are still added to a md array.