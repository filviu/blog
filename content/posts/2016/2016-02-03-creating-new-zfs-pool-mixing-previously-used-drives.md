---
title: Creating new zfs pool mixing previously used drives
author: silviu
type: post
date: 2016-02-03T11:51:03+00:00
url: /2016/02/03/creating-new-zfs-pool-mixing-previously-used-drives/
dsq_thread_id:
  - 4548264489
categories:
  - old
tags:
  - existing
  - freenas
  - temp_on
  - zfs

---

I am building a new homelab for myself using Intel NUCs. I need a NAS so I can test live migration and I was set to buy 2 bay synology. But when a 140$ HP Gen8 Microserver was on offer I couldn't say no. FreeNAS might not be as polished as Synology but I would be getting 4 bays, two gigabit ports and iLO at a third of the price. Also it would offer the possibility of learning FreeNAS (my other, longtime NAS is slackware + zfs on linux).

Since this server is not going to hold any important data (I'll be sure to backup anything important on my <em>production NAS </em>- i.e. the one I don't mess with) I wanted to reuse three old 2TB drives left from upgrading my main NAS to 3TB reds.

When creating the volume in FreeNAS I would be getting the following error:

Creating GPT partition scheme on ada2gpart: geom 'ada2': File exists

I imediately realized that this is because some of the disks used to be in a zfs pool in the past. The suggestion was to clear the begging of the disk but that didn't help. The only fix that worked from the ones proposed [here][1] was:

```bash
# destroy ALL DATA on disk /dev/ada2
sysctl kern.geom.debugflags=0x10
dd if=/dev/zero of=/dev/ada2 bs=1m
# now reboot!
```

I don't remember if I zeroed the entire 2TB disk or just left it fot ~10 mins to ensure most of the zfs metadata is gone.

After running the above in the command line I was able to create the volume just fine.

[1]: http://zfsguru.com/forum/zfsgurusupport/494