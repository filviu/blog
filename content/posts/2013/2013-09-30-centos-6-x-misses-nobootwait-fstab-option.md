---
title: CentOS 6.x misses nobootwait fstab option.
author: silviu
type: post
date: 2013-09-30T06:51:14+00:00
url: /2013/09/30/centos-6-x-misses-nobootwait-fstab-option/
dsq_thread_id:
  - 1810120626
categories:
  - tech
tags:
  - boot
  - centos
  - missing
  - nobootwait
  - usb

---
Recently I added a new storage disk to a cloud server. The issue is that this disk might not always be available at boot time. There is an easy fix for this kind of problems. The **nobootwait** mount option (like it would show in a fstab entry):

```bash
/dev/xvdd1 /storage ext4 defaults,nobootwait 0 0
```


_Note that the fsck order of 0 already ensures that fsck will not hold the boot process by complaining the disk is missing._

This is what I did, then I tried to mount my new attached disk:

```bash
mount /storage
mount: wrong fs type, bad option, bad superblock on /dev/xvdd1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so
```

I checked dmesg and this is what it spitted out:

```bash
dmesg | grep xvdd1 | tail -n1
EXT4-fs (xvdd1): Unrecognized mount option "nobootwait" or missing value
```

I'll be, CentOS never heard of it (surprise, surprise). I thought about nofailm but I was not sure it would do the trick.

This is what **fstab(5)** says about **nobootwait**

_The mountall(8) program that mounts filesystem during boot also recognises additional options that the ordinary mount(8) tool does not. These are: bootwait which can be applied to remote filesystems mounted outside of /usr or /var, without which mountall(8) would not hold up the boot for these; nobootwait which can be applied to non-remote filesystems to explicitly instruct mountall(8) not to hold up the boot for them; optional which causes the entry to be ignored if the filesystem type is not known at boot time; and showthrough which permits a mountpoint to be mounted before its parent mountpoint (this latter should be used carefully, as it can cause boot hangs)._

and this about **nofail**

_nofail do not report errors for this device if it does not exist._

So I took the hackish route of adding **noauto** instead of **nobootwait**. This way the disk is not even mounted at boot time, and so it can be missing and added a mount line in **rc.local**.

```bash
cat /etc/rc.local

#!/bin/sh
#
# This script will be executed *after* all the other init scripts.
# You can put your own initialization stuff in here if you don't
# want to do the full Sys V style init stuff.

/bin/mount /storage &amp;
```

Let me know if you know or find a better way of doing this.