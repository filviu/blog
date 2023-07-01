---
title: Force fsck on next reboot
author: silviu
type: post
date: 2010-07-19T08:07:25+00:00
url: /2010/07/19/force-fsck-on-next-reboot/
categories:
  - old
tags:
  - bash
  - force
  - fsck
  - temp_on
  - touch

---
![fsck](/blog/images/2010/fsck1-150x150.jpg) Let's say you run a headless server and you want to fsck the main partition. The easy solution in this case is (if possible) to force fsck to run on the next boot.

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