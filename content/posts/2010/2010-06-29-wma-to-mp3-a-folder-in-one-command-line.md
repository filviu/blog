---
title: Wma to Mp3 a folder in one command line
author: silviu
type: post
date: 2010-06-29T16:52:51+00:00
url: /2010/06/29/wma-to-mp3-a-folder-in-one-command-line/
dsq_thread_id:
  - 333136110
categories:
  - old
tags:
  - temp_on

---

I have some albums that were ripped in wma form (yes a shame I know) and have since lost the original CDs. I wanted them converted into mp3 so my collection remains consistent and they also could work in my car.

So this would be a command to run in a folder filled with .wma files. This keeps the names but not the tags so be sure to use something like <a href="http://easytag.sourceforge.net/" target="_blank" rel="noopener">easytag</a> to fill them after.

```bash
for i in *.wma ; do mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader "$i" && lame -m j -h -vbr-new -b 320 audiodump.wav -o "`basename "$i" .wma`.mp3"; done; rm -f audiodump.wav
```

Reencoding from a lossy to another lossy format is a bad idea. Only use it if no other option remains.