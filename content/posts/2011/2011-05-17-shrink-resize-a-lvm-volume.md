---
title: Shrink (resize) a LVM volume
author: silviu
type: post
date: 2011-05-17T09:11:18+00:00
url: /2011/05/17/shrink-resize-a-lvm-volume/
categories:
  - old
tags:
  - linux
  - logical
  - lvm
  - resize
  - root
  - server
  - shrink
  - temp_on
  - ubuntu
  - volume

---
I found a lot of resources on resizing LVM volumes or volume groups. But resources on shrinking were a little scarce and I couldn't easily find a simple step by step method listed, so here you go. Please note that the volume you intend to shrink must be unmounted. If you want to resize the root partition (because like me you didn't noticed that the ubuntu server installer will alocate the full 500Gb HDD for the root) you will have to boot off a LiveCD. I used the ubuntu server install cd and booted in _Rescue Mode_.

After it boots press ALT+F2 to move to a console.

Let's see first the layout:

```bash
lvdisplay
```

Let's try and see if the volumes are there:

```bash
ls /dev/vgname/volume
```

On the first try I got nothing so we must enable them:

```bash
vgchange -a y
ls /dev/vgname/volume
```

Yep, they are all there.

Before anything else we need to check the volume for errors (resize2fs will not work if you don't)

```bash
e2fsck -f /dev/vgname/volume
```

After that we resize the filesystem:

```bash
resize2fs /dev/vgname/volume 15G
```

**Note that if you resize the volume to a size smaller than the file system it will trim it (the file system) and probably destroy it**
Above, I reduced the filesystem from 453 to 15gb. That is a 438Gb gain.  Just to be on the safe side I will resize the volume only with 435Gb (leaving play room of over 3Gb which is plenty enough, 1Gb should be sufficient).

_E.g. if you want your final size to be 15Gb than resize the fs to 14Gb, shrink the logical volume to 15Gb and then grow the file system back._

```bash
lvreduce -L -435G /dev/vgname/volume
```

Let's put whatever was left for safety to use (grow back the file system to the full volume size):

```bash
resize2fs /dev/vgname/volume
```

Just to be on the safe side let's check the filesystem for errors.

```bash
e2fsck -f /dev/vgname/volume
```

If you, like me, have resized the root than now you should reboot, otherwise simply mount back the volume and enjoy the free space by creating new volumes.

**Remember! I resized a test environment, which didn't matter if it went away. If you resize a production system (or anything else with useful data on it) remeber to BACKUP!**