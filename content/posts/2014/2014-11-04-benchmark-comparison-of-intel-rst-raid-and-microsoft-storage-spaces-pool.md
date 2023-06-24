---
title: Benchmark comparison of Intel RST RAID and Microsoft Storage Spaces pool
author: silviu
type: post
date: 2014-11-04T09:53:30+00:00
url: /2014/11/04/benchmark-comparison-of-intel-rst-raid-and-microsoft-storage-spaces-pool/
dsq_thread_id:
  - 3190037859
categories:
  - old
tags:
  - benchmark
  - raid
  - storage spaces
  - temp_on

---
I [posted][1] last time that I upgraded my workstation's mechanical storage. Since I had a hard time deciding between using storage spaces and my motherboard's Intel RST sollution I searched some comparisons but couldn't find any so I decided to make my own mini benchmark.

## Hardware

- Intel I7 2600k
- Gigabyte GA-Z68XP-UD3P motherboard
- 4 WD 2TB Green drives (actually 3 x 2TB WD20EARS and 1 x 2TB WD20EADX)

## Benchmarks

### Storage spaces three drive parity

Originally I was using just three of the disks (wanting to keep the fourth for offsite backups). I created a 3 disks parity pool using Storage Spaces. I quickly discovered that it's unusable (I ended up keeping my data spread on faster, smaller disks and this array only for copies and media). Unfortunately it's [acknowledged][2] that Storage Spaces Parity performance is [abysmal][3].

![CrystalDiskMark screenshot showing results for storage_spaces_parity_performance](/blog/images/2014/storage_spaces_parity_performance.png)

```shell
------------------------
CrystalDiskMark 3.0.3 x64 (C) 2007-2013 hiyohiyo
Crystal Dew World : http://crystalmark.info/
------------------------
* MB/s = 1,000,000 byte/s [SATA/300 = 300,000,000 byte/s]

Sequential Read : 179.874 MB/s
Sequential Write : 24.903 MB/s
Random Read 512KB : 41.555 MB/s
Random Write 512KB : 17.463 MB/s
Random Read 4KB (QD=1) : 0.542 MB/s [ 132.3 IOPS]
Random Write 4KB (QD=1) : 0.183 MB/s [ 44.7 IOPS]
Random Read 4KB (QD=32) : 1.827 MB/s [ 446.0 IOPS]
Random Write 4KB (QD=32) : 0.294 MB/s [ 71.8 IOPS]

Test : 1000 MB [F: 0.1% (5.0/3717.4 GB)] (x1)
Date : 2014/10/29 21:22:32
OS : Windows 8.1 Pro [6.3 Build 9600] (x64)
```

This setup proved to be unusable for me. Basically unless you would use it for bulk mostly read storage I would go with something else. As always Microsoft blogs minimize this issue blaming it on the overhead of parity. This of course completely ignores the fact that the same parity raid5 with the same disks with added overhead from ZFS performed orders of magnitude faster in a far less powerful hp microserver. But I'm going off topic here.

At this point I gave up on parity and decided a much more speedier RAID10 is in order. This should give enough performance to allow me to give up on using the faster, smaller drives.

### RAID10 using Intel RST in AHCI

Yes the title is not wrong. I can set the SATA controller in RAID mode, setup the array, set the controller back as AHCI and it would still work. (As I didn't want to fumble with windows drivers - as I installed Windows with the controllersin AHCI mode)

![CrystalDiskMark screenshot showing results for intel_rst_raid10_ahci](/blog/images/2014/intel_rst_raid10_ahci.png)


```shell
------------------------
CrystalDiskMark 3.0.3 x64 (C) 2007-2013 hiyohiyo
Crystal Dew World : http://crystalmark.info/
------------------------
* MB/s = 1,000,000 byte/s [SATA/300 = 300,000,000 byte/s]

Sequential Read : 213.320 MB/s
Sequential Write : 222.675 MB/s
Random Read 512KB : 37.780 MB/s
Random Write 512KB : 82.130 MB/s
Random Read 4KB (QD=1) : 0.532 MB/s [ 130.0 IOPS]
Random Write 4KB (QD=1) : 1.917 MB/s [ 467.9 IOPS]
Random Read 4KB (QD=32) : 4.863 MB/s [ 1187.3 IOPS]
Random Write 4KB (QD=32) : 1.648 MB/s [ 402.3 IOPS]

Test : 1000 MB [F: 0.1% (5.0/3725.9 GB)] (x1)
Date : 2014/10/29 20:28:14
OS : Windows 8.1 Pro [6.3 Build 9600] (x64)
```

Yes, much better. At this point it was worth the hassle updating windows drivers to be able to set the controllers in RAID.

### RAID10 using Intel RST in RAID

I used [these instructions][4] to make windows work with the new settings. (If you just change your BIOS setting windows will get stuck in a reboot loop)

![CrystalDiskMark screenshot showing results for intel_rst_raid10_raid](/blog/images/2014/intel_rst_raid10_raid.png)

```shell
------------------------
CrystalDiskMark 3.0.3 x64 (C) 2007-2013 hiyohiyo
Crystal Dew World : http://crystalmark.info/
------------------------
* MB/s = 1,000,000 byte/s [SATA/300 = 300,000,000 byte/s]

Sequential Read : 210.431 MB/s
Sequential Write : 224.559 MB/s
Random Read 512KB : 38.569 MB/s
Random Write 512KB : 78.972 MB/s
Random Read 4KB (QD=1) : 0.524 MB/s [ 127.9 IOPS]
Random Write 4KB (QD=1) : 1.633 MB/s [ 398.6 IOPS]
Random Read 4KB (QD=32) : 4.318 MB/s [ 1054.2 IOPS]
Random Write 4KB (QD=32) : 1.480 MB/s [ 361.3 IOPS]

Test : 1000 MB [F: 0.1% (5.0/3725.9 GB)] (x1)
Date : 2014/10/29 20:57:30
OS : Windows 8.1 Pro [6.3 Build 9600] (x64)
```

No surprise here, it's basically the same. Since my machine is on a UPS I can afford to change the following performance affecting settings: write buffer disabled, write back enabled.

![CrystalDiskMark screenshot showing results for intel_rst_raid10_raid_perf](/blog/images/2014/intel_rst_raid10_raid_perf.png)

```shell
------------------------
CrystalDiskMark 3.0.3 x64 (C) 2007-2013 hiyohiyo
Crystal Dew World : http://crystalmark.info/
------------------------
* MB/s = 1,000,000 byte/s [SATA/300 = 300,000,000 byte/s]

Sequential Read : 220.266 MB/s
Sequential Write : 232.655 MB/s
Random Read 512KB : 37.304 MB/s
Random Write 512KB : 80.230 MB/s
Random Read 4KB (QD=1) : 0.541 MB/s [ 132.0 IOPS]
Random Write 4KB (QD=1) : 1.614 MB/s [ 394.0 IOPS]
Random Read 4KB (QD=32) : 3.759 MB/s [ 917.8 IOPS]
Random Write 4KB (QD=32) : 1.190 MB/s [ 290.5 IOPS]

Test : 1000 MB [F: 0.0% (0.3/3725.9 GB)] (x1)
Date : 2014/10/29 21:58:05
OS : Windows 8.1 Pro [6.3 Build 9600] (x64)
```

As expected a slight improvement of write performance. Whether these settings (be sure you understand them) are worth it it's up to you, the number of backups you have, etc. My pc is on a UPS and all my data has multiple backups so I can afford to leave them on.

### Striped mirror (using Windows 8 storage spaces)

As I posted before you can [trick Windows 8 into creating a RAID10][1] array.

![CrystalDiskMark screenshot showing results for storage_spaces_striped_mirror](/blog/images/2014/storage_spaces_striped_mirror.png)

```shell
------------------------
CrystalDiskMark 3.0.3 x64 (C) 2007-2013 hiyohiyo
Crystal Dew World : http://crystalmark.info/
------------------------
* MB/s = 1,000,000 byte/s [SATA/300 = 300,000,000 byte/s]

Sequential Read : 240.886 MB/s
Sequential Write : 150.183 MB/s
Random Read 512KB : 45.446 MB/s
Random Write 512KB : 83.722 MB/s
Random Read 4KB (QD=1) : 0.598 MB/s [ 146.1 IOPS]
Random Write 4KB (QD=1) : 1.507 MB/s [ 367.9 IOPS]
Random Read 4KB (QD=32) : 3.697 MB/s [ 902.6 IOPS]
Random Write 4KB (QD=32) : 1.244 MB/s [ 303.7 IOPS]

Test : 1000 MB [I: 0.1% (4.9/3706.7 GB)] (x1)
Date : 2014/10/29 21:09:06
OS : Windows 8.1 Pro [6.3 Build 9600] (x64)
```

Better read performance but much worse write performance.

### Comparison with an SSD, velociraptor and WD 1TB black

**SSD**

![CrystalDiskMark screenshot showing results for ssd](/blog/images/2014/ssd.png)

```shell
------------------------
CrystalDiskMark 3.0.3 x64 (C) 2007-2013 hiyohiyo
Crystal Dew World : http://crystalmark.info/
------------------------
* MB/s = 1,000,000 byte/s [SATA/300 = 300,000,000 byte/s]

Sequential Read : 492.520 MB/s
Sequential Write : 280.894 MB/s
Random Read 512KB : 444.164 MB/s
Random Write 512KB : 280.340 MB/s
Random Read 4KB (QD=1) : 29.234 MB/s [ 7137.2 IOPS]
Random Write 4KB (QD=1) : 76.510 MB/s [ 18679.1 IOPS]
Random Read 4KB (QD=32) : 356.318 MB/s [ 86991.7 IOPS]
Random Write 4KB (QD=32) : 254.365 MB/s [ 62100.8 IOPS]

Test : 1000 MB [C: 39.6% (94.4/238.1 GB)] (x1)
Date : 2014/10/29 21:11:07
OS : Windows 8.1 Pro [6.3 Build 9600] (x64)

```

**Velociraptor** (an older generation)

![CrystalDiskMark screenshot showing results for velociraptor](/blog/images/2014/ssd.png)

```shell
------------------------
CrystalDiskMark 3.0.3 x64 (C) 2007-2013 hiyohiyo
Crystal Dew World : http://crystalmark.info/
------------------------
* MB/s = 1,000,000 byte/s [SATA/300 = 300,000,000 byte/s]

Sequential Read : 111.979 MB/s
Sequential Write : 109.500 MB/s
Random Read 512KB : 54.569 MB/s
Random Write 512KB : 72.897 MB/s
Random Read 4KB (QD=1) : 0.902 MB/s [ 220.2 IOPS]
Random Write 4KB (QD=1) : 1.836 MB/s [ 448.2 IOPS]
Random Read 4KB (QD=32) : 2.069 MB/s [ 505.1 IOPS]
Random Write 4KB (QD=32) : 1.942 MB/s [ 474.1 IOPS]

Test : 1000 MB [H: 84.2% (352.9/419.2 GB)] (x1)
Date : 2014/10/29 21:13:28
OS : Windows 8.1 Pro [6.3 Build 9600] (x64)

```

**WD 1TB** (SATA2 generation)

![CrystalDiskMark screenshot showing results for wd1tbblack](/blog/images/2014/wd1tbblack.png)

```shell
------------------------
CrystalDiskMark 3.0.3 x64 (C) 2007-2013 hiyohiyo
Crystal Dew World : http://crystalmark.info/
------------------------
* MB/s = 1,000,000 byte/s [SATA/300 = 300,000,000 byte/s]

Sequential Read : 99.212 MB/s
Sequential Write : 94.971 MB/s
Random Read 512KB : 24.519 MB/s
Random Write 512KB : 49.434 MB/s
Random Read 4KB (QD=1) : 0.343 MB/s [ 83.8 IOPS]
Random Write 4KB (QD=1) : 0.772 MB/s [ 188.5 IOPS]
Random Read 4KB (QD=32) : 0.515 MB/s [ 125.8 IOPS]
Random Write 4KB (QD=32) : 0.708 MB/s [ 172.9 IOPS]

Test : 1000 MB [E: 56.9% (530.0/931.5 GB)] (x1)
Date : 2014/10/29 21:16:12
OS : Windows 8.1 Pro [6.3 Build 9600] (x64)

```

## Conclusion

If you don't have a lot of data use SSDs. Faster, more expensive mechanical drives are no match to a RAID10 array made using cheaper drives. I still keep virtual machines on the Velociraptor drive because of slightly better seek and 4k performance. In the end I went with Intel RST for the better write performance and also because I was not ok using something that Microsoft might break one day since it's not standard functionality.

 [1]: http://www.sgvulcan.com/trick-windows-8-into-creating-a-raid10-stripped-mirrors-array/
 [2]: https://social.technet.microsoft.com/Forums/windowsserver/en-US/64aff15f-2e34-40c6-a873-2e0da5a355d2/parity-storage-space-so-slow-that-its-unusable
 [3]: http://blogs.technet.com/b/mspfe/archive/2013/02/25/why-windows-server-2012-parity-storage-spaces-might-perform-slowly.aspx
 [4]: http://answers.microsoft.com/en-us/windows/forum/windows_8-hardware/how-to-windows-8-ahci-to-raid-wo-reinstall-of-win8/e55afe47-fdad-47b4-af29-de5af179a076