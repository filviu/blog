---
title: Fixing a self pressing button on an Asus VW202SR monitor
author: silviu
type: post
date: 2012-01-17T18:51:16+00:00
url: /2012/01/17/fixing-a-self-pressing-button-on-an-asus-vw202sr-monitor/
dsq_thread_id:
  - 542874130
categories:
  - old
tags:
  - asus
  - brightness
  - button
  - lcd
  - monitor
  - stuck
  - temp_on

---
[<img decoding="async" loading="lazy" class="alignleft  wp-image-2016" title="Broken button Asus Monitor showing Brightness menu" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0379-300x200.jpg" alt="" width="210" height="140" />][1]

Well, today instead of working I had the pleasure of fixing the monitor 🙂 The monitor is an older Asus VW202 SR that my wife uses connected to the laptop. I tried everything else (power cycling, another signal cable, another computer) but it turns out to be really the button. The issue manifested itself by the brightness setting window appearing and going eventually all the way to 100. First I thought that the button was stuck in the frame but it was safely depressed. That means a broken button on the pcb board. I thought it would be pretty easy to solder a new one in place.

<!--more-->

But first I had to disassemble it:

[<img decoding="async" loading="lazy" class="alignnone wp-image-2007 size-medium" title="Asus monitor dissasembly step" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0366_v1-300x215.jpg" alt="Asus monitor dissasembly step" width="300" height="215" />][2]

1. Search and remove. There are 7 philips screws. 2 under rubber caps, 2 under flat foil, 2 holding the stand and 1 on the middle of the bottom frame. Make notes that the two of the stand are a different size.

[<img decoding="async" loading="lazy" class="alignnone size-500 wp-image-2008" title="Asus monitor dissasembly step" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0368_v1-500x213.jpg" alt="Asus monitor dissasembly step" width="500" height="213" />][3]

One is hidden under the warranty seal.

[<img decoding="async" loading="lazy" class="aligncenter" title="Asus monitor dissasembly step" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0369_v1.jpg" alt="Asus monitor dissasembly step" width="216" height="333" />][4]

Don&#8217;t loose the rubber caps and place the flat ones with the adhesive side facing up. This way you can reuse them.

[<img decoding="async" loading="lazy" title="Asus monitor dissasembly step" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0371_v1-500x96.jpg" alt="Asus monitor dissasembly step" width="500" height="96" />][5]

There are two openings in the frame at the bottom. Place the monitor facing up and use a plastic tool (or if, like me, you don&#8217;t care about marks you can use a flat-head screwdriver) **Pull very gently** as the frame holds a small pcb board with the buttons and the power led. Disconnect it before lifting the frame.

[<img decoding="async" loading="lazy" title="Asus monitor dissasembly step" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0372_v1.jpg" alt="Asus monitor dissasembly step" width="500" height="287" />][6]

That is the PCB that needs removing. You need to bend one of the plastic posts holding it in place. Be very careful not to snap it.

[<img decoding="async" loading="lazy" title="Asus monitor dissasembly step" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0373_v1.jpg" alt="Asus monitor dissasembly step" width="500" height="105" />][7]

Make note of the button causing you troubles. For me it was menu right (toggles brightness when not in menu)

[<img decoding="async" loading="lazy" title="Asus monitor dissasembly step" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0375_v1-500x239.jpg" alt="Asus monitor dissasembly step" width="500" height="239" />][8]

**Try not to open the wrong one** like I did!The problem was that I didn&#8217;t have buttons like this to solder in place. So I tried to see if I can fix it. Ok this is a bit tricky. Use a magnifying glass if you need to. The button has a metal casing held in place by 4 _clamps_ (clasp? &#8211; for lack of a better term). I used a snapped syringe needle to gently lift it over the four clamps. Inside you will find a dome shaped metal disk (this is the one closing the circuit) and two plastic parts. Try to lift the casing without moving them and make note (take a picture) of their arrangement. It is important that they face the same way when assembling the button.

[<img decoding="async" loading="lazy" title="Asus monitor dissasembly step" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0376_v1-500x245.jpg" alt="Asus monitor dissasembly step" width="500" height="245" />][9]

Not a good picture but enough detail on the bad button. The problem was caused by 1-2 metal particulates in the button. I cleaned it with a cotton swab. After you put the disc and the two plastic parts in place simply press the casing to snap in place.

&nbsp;

&nbsp;

[<img decoding="async" loading="lazy" title="Asus monitor dissasembly step" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0377_v1-500x227.jpg" alt="Asus monitor dissasembly step" width="500" height="227" />][10]

Don&#8217;t forget to connect the cable back to the PCB.

Do everything you did to get here in reverse to assemble the monitor!

 [1]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0379.jpg
 [2]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0366_v1.jpg
 [3]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0368_v1.jpg
 [4]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0369_v1.jpg
 [5]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0371_v1.jpg
 [6]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0372_v1.jpg
 [7]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0373_v1.jpg
 [8]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0375_v1.jpg
 [9]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0376_v1.jpg
 [10]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/01/IMG_0377_v1.jpg