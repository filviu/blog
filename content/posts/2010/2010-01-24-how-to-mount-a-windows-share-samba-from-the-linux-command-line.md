---
title: How to mount a windows share (samba) from the linux command line
author: silviu
type: post
date: 2010-01-24T18:03:08+00:00
url: /2010/01/24/how-to-mount-a-windows-share-samba-from-the-linux-command-line/
dsq_thread_id:
  - 327237811
categories:
  - old
tags:
  - linux
  - mount
  - samba
  - share
  - temp_on
  - Windows

---
As you know Linux does not use drive letters like Windows does. All files are organized under a big tree hierarchy. We use the mount command to mount partitions and this is the same command used to mount remote windows partition or windows shares.

Please note that you'll need to know the following:

  * Windows username and password (the ones needed to access the share)
  * The machine and share name. Something like //xpdesktop/pictures
  * Have root access on the linux machine

Login on your linux machine as root. Type the following command to mount your remote windows share:
```bash
mkdir /mnt/share_name
mount -t cifs //xpdesktop/pictures -o username=john, password=johnspass /mnt/share_name
```
Where:

  * xpdesktop is the network name of the Windows machine
  * john is the username on  the windows machine
  * johnspass is the password used to access the windows share
  * /mnt/share_name is the target folder where the partition will be mounted (the folder you just created above)

You can now cd and ls the remote windows share as any other folder on the linux machine:
```bash
cd /mnt/share_name
ls  -l
```
I'll show you in a following article how you can automatically mount a remote Windows share at boot time.