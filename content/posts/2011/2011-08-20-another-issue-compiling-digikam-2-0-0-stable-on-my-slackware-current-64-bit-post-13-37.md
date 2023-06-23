---
title: Another issue compiling Digikam 2.0.0 stable on my Slackware current 64 bit (post 13.37)
author: silviu
type: post
date: 2011-08-20T18:14:01+00:00
url: /2011/08/20/another-issue-compiling-digikam-2-0-0-stable-on-my-slackware-current-64-bit-post-13-37/
dsq_thread_id:
  - 391622188
categories:
  - old
tags:
  - 32bit
  - 64bit
  - digikam
  - libgl
  - temp_on

---
This error is spit after compiling:

```bash
Linking CXX shared module ../../../lib/kipiplugin_advancedslideshow.so
/usr/lib64/gcc/x86_64-slackware-linux/4.5.3/../../../../x86_64-slackware-linux/bin/ld: skipping incompatible /usr/share/opencv/../../lib/libGL.so when searching for -lGL
collect2: ld returned 1 exit status
make[2]: \*** [lib/kipiplugin_advancedslideshow.so] Error 1
make[1]: \*** [extra/kipi-plugins/advancedslideshow/CMakeFiles/kipiplugin_advancedslideshow.dir/all] Error 2
make: \*** [all] Error 2
```

For whatever reason it tries to use the 32 bit version of libGL.so from /usr/lib Since I was annoyed at this point so **I simply renamed `/usr/lib` to `/usr/lib.old` and compiled digikam than reverted.**