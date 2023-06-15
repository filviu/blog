---
title: Force fsck on next reboot
author: silviu
type: post
date: 2010-07-19T08:07:25+00:00
url: /2010/07/19/force-fsck-on-next-reboot/
dsq_thread_id:
  - 326479335
categories:
  - old
tags:
  - bash
  - force
  - fsck
  - temp_on
  - touch

---
<img decoding="async" loading="lazy" class="alignleft size-thumbnail wp-image-1046" title="fsck" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/07/fsck1-150x150.jpg" alt="fsck your main partition on the next boot" width="150" height="150" />Let's say you run a headless server and you want to fsck the main partition. The easy solution in this case is (if possible) to force fsck to run on the next boot.

If you run slackware than all you really need is to create an empty file in **/etc** called **forcefsck**

You could do this by running:
```bash
touch /etc/forcefsck
```
Other linux distributions might check for this file elsewhere, for example in the root directory so the command would be
```bash
touch /forcefsck
```
Checking the documentation will always help.