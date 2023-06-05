---
title: FreePBX fails uploading mp3’s for music on hold
author: silviu
type: post
date: 2010-11-26T14:41:03+00:00
url: /2010/11/26/freepbx-fails-uploading-mp3s-for-music-on-hold/
dsq_thread_id:
  - 326848565
categories:
  - old
tags:
  - asterisk
  - freepbx
  - mpg123
  - sox
  - temp_on

---
[<img decoding="async" loading="lazy" class="alignleft size-full wp-image-1124" title="logo" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/11/logo.png" alt="FreePBX logo" width="100" height="75" />][1]This is caused by a couple of problems:

1. the **/var/lib/asterisk/moh** is missing (or has the wrong permissions). Be sure it's there and has the right owner (asterix:asterix) and permissions

2. Sox has to be installed. What the error logs miss to inform at the first glance is that you also need **mpg123** otherwise you'll get this:

Error Processing: "sox failed to convert file and original could not be copied as a fall back" for Johnny Cash - Solitary Man.mp3!

##### This is not a fatal error, your Music on Hold may still work.

Have fun.

 [1]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/11/logo.png