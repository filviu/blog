---
title: This is how you can read your EXT2 and EXT3 partitions from Windows XP
author: silviu
type: post
date: 2009-06-14T16:15:25+00:00
url: /2009/06/14/this-is-how-you-can-read-your-ext2-and-ext3-partitions-from-windows-xp/
dsq_thread_id:
  - 48858338
categories:
  - old
tags:
  - interoperatiblity
  - temp_on

---
My main workstation has a dual (sometimes tri) boot configuration: some flavour of linux (usually slackware) and some flavour of windows (usually xp). I have small partitions for the operating systems and one &#8211; two big ones for data.

In the past, the data ones used to be FAT32 so they would be readable and writeable from both linux and windows. But FAT32 is no longer useful. It&#8217;s limitations forced me to use either NTFS either EXT2/3. I can read and write NTFS from linux using FUSE but I&#8217;d rather have my data on EXT3 partitions as I use linux way more than windows. So, I made my data partitions EXT3 and searched for a sollution that allows reading EXT2 and EXT3 partitions from Windows XP. I tried a few and settled for EXT2FSD. Good speed, no errors, and both read and write access. Works like a charm.

You can find it here:

<a href="http://ext2fsd.sourceforge.net/" target="_blank" rel="noopener">http://ext2fsd.sourceforge.net/</a>