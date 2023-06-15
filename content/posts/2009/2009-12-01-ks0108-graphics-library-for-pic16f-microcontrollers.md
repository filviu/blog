---
title: KS0108 Graphics Library for PIC16F microcontrollers
author: silviu
type: post
date: 2009-12-01T15:23:50+00:00
url: /2009/12/01/ks0108-graphics-library-for-pic16f-microcontrollers/
dsq_thread_id:
  - 326479233
categories:
  - old
tags:
  - easypic5
  - ks0108
  - mikroc
  - pic
  - temp_on

---
<img decoding="async" loading="lazy" class="alignleft size-full wp-image-592" title="easypic5" alt="easypic5" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/12/easypic5.jpg" width="133" height="111" />Not that I'm not happy with the default mikroC library for the KS0108 graphic displays, as I always I wanted something with the source available. Considering that I'm a beginner with microcontrolers having the source available to hack around is a very valuable learning tool.

The project is based on the source found here:

<a href="http://en.radzio.dxp.pl/ks0108/" target="_blank" rel="noopener">http://en.radzio.dxp.pl/ks0108/</a>

The source is made pretty universal, still it took some work and modifications to have it working in mikroC. The archive is a ready working project for mikroC.

I tested and developed it on the EasyPIC5 development board with a PIC16F887 microcontroller. You have to have the board  configured for the touchscreen panel and GLCD display - i suppose you know how to do that, if not you should consult the EasyPIC5 manual.

The project has everything you need:

  * a small demo program that uses text and bitmaps so you can see how the touchscreen, graphics, images and text work
  * a font file
  * a file to host your bitmap data
  * graphic functions
  * ks0108 functions
  * microcontroller dependent functions.

[Download everything HERE][1]. Or you could find the code on [GitHub][2].

 [1]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/12/ks0108_glcd.zip
 [2]: https://github.com/filviu/ks0108_lib