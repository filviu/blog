---
title: bmp2h converter for ks0108 GLCD
author: silviu
type: post
date: 2009-12-01T15:41:43+00:00
url: /2009/12/01/bmp2h-converter-for-ks0108-glcd/
dsq_thread_id:
  - 326479252
categories:
  - old
tags:
  - ks0108
  - temp_on

---
This is a converter I wrote with the graphics library for the PIC16F microcontrollers. Others work but this one works for sure.

If you want to see the source code (I&#8217;m not particulary proud of it 🙂 )  drop a comment and I&#8217;ll send it to you.

If the bitmap is smaller than 128&#215;64 it will be left as is, if not it will be resized proportionally to 128&#215;64.

[<img decoding="async" loading="lazy" class="aligncenter size-full wp-image-596" title="bmp2ks0108" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/12/bmp2ks0108.jpg" alt="bmp2ks0108" width="618" height="485" />][1]

You can set the name you want your variable to have and you can also set if you want the picture inverted or not. Depending on your lcd colors you might want to invert the result.

You can download the converter here: [glcd_convert][2].

 [1]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/12/bmp2ks0108.jpg
 [2]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/12/glcd_convert.zip