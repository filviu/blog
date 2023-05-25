---
title: Linux on the Acer E3-111 – Aspire E3-111-C5FN
author: silviu
type: post
date: 2014-09-05T08:39:49+00:00
url: /2014/09/05/linux-on-the-acer-e3-111-aspire-e3-111-c5fn/
dsq_thread_id:
  - 2990111432
categories:
  - old
tags:
  - acer
  - aspire
  - baytrail
  - e3-111
  - linux
  - temp_on

---
<img decoding="async" loading="lazy" class="alignleft size-medium wp-image-3034" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/09/E3111silver3-800x800-300x249.jpg" alt="E3111silver3-800x800" width="300" height="249" />I gave up on using a tablet and sold mine some time ago. My old toshiba m100 laptop was to heavy and too old to lug around when on holiday (mainly to download photos) so I decided to buy a small laptop to replace it. 10&#8242; is too small for me and so I decided on an 11&#8242; low cost system.

I bought an [Acer Aspire E3-111][1] instead of competing models from Asus and others because I found a good deal on it and because of the quad core CPU &#8211;  Intel® Celeron® N2930 &#8211; that I couldn&#8217;t find on any other machine.

It came in a 2GB RAM (I upgraded to 8GB), 500GB hdd configuration with some version of linux installed.  Following are a few tips and tricks for running linux (I chose slackware64-current but should apply to most versions)

Below are some tips and tricks on running linux on it:

**BIOS**

  * BIOS can be updated only from a Windows Only utility; I couldn&#8217;t find any alternative. Fortunately a Windows 8.1 Enterprise Evaluation can be downloaded from Microsoft and that can be installed on a USB hard disk using [this tutorial][2].

**Booting**

  * I didn&#8217;t want to bother with UEFI and so I switched to legacy in BIOS. The laptop sometimes fails to boot (kernel loading hangs at some point) and I have to powercycle. I will have to test and see if using UEFI helps
  * I cannot boot using kernel-generic, only kernel-huge
  * I added the following parameters to the kernel command line: acpi_backlight=vendor in order to get backlight shortcuts to work

**Keyboard**

  * Sometimes the arrow keys didn&#8217;t work and more the &#8220;UP&#8221; arrow would trigger the _Disable Touchpad_ shortcut. The only fix was to poweroff & boot over and over (sometimes 2-3 times) until the arrow keys worked. I added a second entry in LILO just to be able to test the arrow keys.**Update:** Bios update 1.29 from 2014/10/28 seems to fix this!

**Sleep**

  * I can get the machine to enter sleep either using the shortcut or closing the lid but I cannot get it to wake up  
    **Update**: by blacklisting **dw_dmac** and **dw\_dmac\_core** I can now enter and resume sleep without issues.

**Ethernet/WiFi**

  * Both work fine without probles, my version has an Atheros wlan card

**Sound**

  * It works out of the box

**Video**

  * I didn&#8217;t test yet how video playing works.  
    **Update:** at least normal files play well, including hd files. I tried some streams in browser from twit.tv and they were dropping frames badly, but in vlc they work fine.

**Misc**

  * The laptop is passively cooled and during heavy use (compiling, etc) it gets pretty warm
  * RAM upgrade is not that easy (motherboard has to be removed, see: http://www.myfixguide.com/manual/acer-aspire-e3-111-disassembly/
  * There is enough space between the WLAN card and the HDD to mount something there. If someone finds a free usb header on the MB I would get a blinkstick in there

**Conclusion**

Not the best laptop to be using with linux, but for the price I can live with the shortcomings. Though I was a bit disapointed as a few years ago the experience with linux on various laptops was better. I expected things to improve over time, not go sour.

I will keep updating this post as I continue using it.

 [1]: http://ark.intel.com/products/81073/Intel-Celeron-Processor-N2930-2M-Cache-up-to-2_16-GHz
 [2]: http://lifehacker.com/how-to-run-a-portable-version-of-windows-from-a-usb-dri-1565509124