---
title: You’ll want to archive your joomla site using .tar.gz
author: silviu
type: post
date: 2010-11-30T13:26:22+00:00
url: /2010/11/30/youll-want-to-archive-your-joomla-site-using-tar-gz/
dsq_thread_id:
  - 333392836
categories:
  - old
tags:
  - bzip2
  - gzip
  - joomla. archive
  - tar
  - temp_on

---
I was building a script to archive my joomla folders on a linux server. I noticed it takes a lot of time to complete so I've run  a few tests on one website. Here are the results:
```bash
[root@host]# time tar cjf /backup/2010-11-30/test.tar.bz2 -C /var/www/site .
real    0m55.299s
user    0m53.929s
sys     0m1.314s

[root@host]# time tar czf /backup/2010-11-30/test.tar.gz -C /var/www/site .
real    0m15.545s
user    0m12.311s
sys     0m0.947s

[root@host]# time tar cf /backup/2010-11-30/test.tar -C /var/www/site .
real    0m1.609s
user    0m0.081s
sys     0m0.915s

[root@host]# ls -l /backup/2010-11-30/
total 672980
-rw-r-r- 1 root root 287815680 Nov 30 05:17 test.tar
-rw-r-r- 1 root root 197970835 Nov 30 05:17 test.tar.bz2
-rw-r-r- 1 root root 202647314 Nov 30 05:17 test.tar.gz
```
You can see that if we use tar we finish very fast but since there's no compression we loose a lot of space. Gzip on the other hand looses only 4 Mb to Bzip2 but gains us 40 seconds. So gzip is what I will use from now on.

_Update: I forgot to mention in the original article that the site was already archived a few times before this test so the files were probably already cached. Running the same script on my webserver (for all the sites installed) with bzip2 was way slower in total than being run with gzip compression a few days later (so under similar conditions) - and the space lost was not worth mentioning._

Also this is probably not limited to joomla - anything would archive slower with bzip2 but with better compresion.