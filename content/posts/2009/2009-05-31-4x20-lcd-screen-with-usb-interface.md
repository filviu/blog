---
title: 4×20 LCD screen with USB interface.
author: silviu
type: post
date: 2009-05-31T15:50:54+00:00
url: /2009/05/31/4x20-lcd-screen-with-usb-interface/
dsq_thread_id:
  - 48858276
categories:
  - old
tags:
  - 18f2550
  - lcd
  - microchip
  - pic
  - temp_on
  - usb

---
Attaching an LCD screen to a pc is a pretty easy job. I am working on a jukebox that I wanted to a screen attached to. Although a HD44780 based LCD can be attached to the parallel port with almost no additional parts I wanted a more flexible solution, and I thought about microcontrollers with usb support. I found a thread <a href="http://forums.bit-tech.net/showthread.php?t=115461" target="_blank" rel="noopener">here</a>, where all the work is pretty much done. Thank you ch424. All credits for the design and firmware should go to him. I am simply documenting here my build. You can find on the thread mentioned everything you need - firmware, drivers, schematics, programmer configuration. By the way I used the Easy Pic 5 from Mikroelektronika to program my PIC and do some initial testing. The settings for Picflash were similar with the ones ch424 shows for his Winpic.  If you are having trouble programming with Picflash from mikroe drop a comment and I'll try to help you.

## The project

The design is based around a **PIC18F2550** from Microchip. You will also need an LCD screen, one that is up to 20&#215;4 and HD44780 or KS0066U compliant. The design can also accommodate some GPOs, a rotary encoder and a buzzer. I plan to add the rotary encoder soon.

<figure id="attachment_150" aria-describedby="caption-attachment-150" style="width: 300px" class="wp-caption aligncenter">[![img_7769_cnv](/blog/images/2009/img_7769_cnv-300x200.jpg) ][1]<figcaption id="caption-attachment-150" class="wp-caption-text">Just the screen</figcaption></figure>

The screen all up and running.

<figure id="attachment_153" aria-describedby="caption-attachment-153" style="width: 300px" class="wp-caption aligncenter">[![img_7767_cnv](/blog/images/2009/img_7767_cnv-300x200.jpg) ][2]<figcaption id="caption-attachment-153" class="wp-caption-text">Soldering the connector for the LCD screen</figcaption></figure>

I soldered a female connector to the LCD board so I can connect the screen both to my Easy Pic 5 development board and the USB backpack.

<figure id="attachment_156" aria-describedby="caption-attachment-156" style="width: 300px" class="wp-caption aligncenter">[![img_7775_cnv](/blog/images/2009/img_7775_cnv-300x200.jpg) ][3]<figcaption id="caption-attachment-156" class="wp-caption-text">All done and working</figcaption></figure>

<figure id="attachment_152" aria-describedby="caption-attachment-152" style="width: 300px" class="wp-caption aligncenter">[![img_7777_cnv](/blog/images/2009/img_7777_cnv-300x200.jpg) ][4]<figcaption id="caption-attachment-152" class="wp-caption-text">All done and working</figcaption></figure>

For now I tested the screen with [Lcdsmartie][5] but later on I plan to use it with lcdproc on linux.

<figure id="attachment_149" aria-describedby="caption-attachment-149" style="width: 300px" class="wp-caption aligncenter">[![img_7779_cnv](/blog/images/2009/img_7779_cnv-300x200.jpg) ][6]<figcaption id="caption-attachment-149" class="wp-caption-text">The custom made board</figcaption></figure>

<figure id="attachment_154" aria-describedby="caption-attachment-154" style="width: 300px" class="wp-caption aligncenter">[![img_7785_cnv](/blog/images/2009/img_7785_cnv-300x200.jpg) ][7]<figcaption id="caption-attachment-154" class="wp-caption-text">The board, closer</figcaption></figure>

Should the thread or the board disappear just drop a comment and I can mirror the .hex file, the schematic and the pcb layout.

 [1]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/05/img_7769_cnv.jpg
 [2]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/05/img_7767_cnv.jpg
 [3]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/05/img_7775_cnv.jpg
 [4]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/05/img_7777_cnv.jpg
 [5]: http://lcdsmartie.sourceforge.net/
 [6]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/05/img_7779_cnv.jpg
 [7]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/05/img_7785_cnv.jpg