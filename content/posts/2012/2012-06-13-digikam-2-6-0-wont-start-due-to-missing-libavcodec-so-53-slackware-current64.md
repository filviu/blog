---
title: digikam 2.6.0 won’t start due to missing libavcodec.so.53 (slackware current64)
author: silviu
type: post
date: 2012-06-13T19:44:01+00:00
url: /2012/06/13/digikam-2-6-0-wont-start-due-to-missing-libavcodec-so-53-slackware-current64/
dsq_thread_id:
  - 724822888
categories:
  - old
tags:
  - build
  - digikam
  - error
  - ffmpeg
  - make
  - opencv
  - rebuild
  - temp_on

---
This was pretty simple but complicated :). It turns out I updated [alien bob](http://alien.slackbook.org/blog/)'s repo to ffmpeg 0.11, thus upgrading to libavcodec.so.54. I'm sure I could have gotten away with a simple symlink but I wanted a clean install.

So I though I would simply rebuild digikam, right? Wrong. It failed, with weird errors like:

```bash
make[2]: \*** [extra/libkface/test/detect] Error 1
```

or

```bash
collect2: error: ld returned 1 exit status
make[2]: *** [extra/kipi-plugins/removeredeyes/test/testipp] Error 1
```

Face detect above sounded a lot like [digikam](http://digikam.org/) built successfully.