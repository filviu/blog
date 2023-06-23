---
title: Running 16 bit apps in Windows 7 64 bit
author: silviu
type: post
date: 2010-04-03T10:17:50+00:00
url: /2010/04/03/running-16-bit-apps-in-windows-7-64-bit/
dsq_thread_id:
  - 326479311
categories:
  - old
tags:
  - 64 bit
  - compatibility
  - dos
  - dosbox
  - oxford
  - superlex
  - temp_on
  - win311

---
We got for my wife a much needed upgrade for her aging Toshiba laptop. The new one came with Windows 7  64 bit. I managed to get all her old software working with the exception of Oxford Superlex. This one is a dictionary from the Windows 3.11 ages. It worked fine in all windowses we had (98, 2000, XP) but having a 64 bit Windows killed it because the support for 16 bits apps is dropped in 64 bits versions of Vista and 7.

My wife likes this dictionary a lot, and as far as I can tell there are no upgrades available for it. One option would have been to have a copy of 32 bit XP or 2000 running as a virtual machine. Since the laptop only had windows 7 home installed it wasn't elligible to run XP mode. A full blown virtual machine would also tax a lot the laptop.

**Sollution:** I grabbed a copy of Windows 3.11 I still had around, installed <a href="http://www.dosbox.com/" target="_blank" rel="noopener">dosbox</a> with freedos, set up windows 3.11 inside it. I gave some old graphic drivers a shot in order to get more than a 640&#215;480 windows but gave up, it's pretty usefull like this too. _If someone knows how to get 3.11 inside dosbox to run at more than 640&#215;480 please let me know._

![oxford_windows7_64bit](/blog/images/2010/oxford_windows7_64bit.jpg)

_
I also set dosbox to launch **win /s c:oxfordsuperlex.exe** at start and created an icon for it. So, it's possible to directly call the wanted 16 bit app, without having my wife to remember how to launch windows 3.11 from dos.

