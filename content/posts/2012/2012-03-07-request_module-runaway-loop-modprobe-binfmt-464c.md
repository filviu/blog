---
title: 'request_module: runaway loop modprobe binfmt-464c'
author: silviu
type: post
date: 2012-03-07T13:05:52+00:00
url: /2012/03/07/request_module-runaway-loop-modprobe-binfmt-464c/
categories:
  - old
tags:
  - 32bit
  - 64bit
  - boot
  - error
  - hang
  - kernel
  - linux
  - n40l
  - nas
  - temp_on

---

I added a new disk to my HP N40L and moved the boot disk to another SATA port, which meant reconfiguring lilo. Strange enough after setting everything up I got:

```bash
request_module: runaway loop modprobe binfmt-464c
```

right after the kernel loading.

Long story short this message means you are trying to boot a 32bit system with a 64 bit kernel (maybe the other way around will spit something similar). I set the boot parameter wrong and I was actually trying to boot and old 32 bit linux install that was still around on one of the drives in the NAS