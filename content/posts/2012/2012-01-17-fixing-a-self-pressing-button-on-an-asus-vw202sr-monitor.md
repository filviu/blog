---
title: Fixing a self pressing button on an Asus VW202SR monitor
author: silviu
type: post
date: 2012-01-17T18:51:16+00:00
url: /2012/01/17/fixing-a-self-pressing-button-on-an-asus-vw202sr-monitor/
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
![](/blog/images/2012/)


![Broken button Asus Monitor showing Brightness menu](/blog/images/2012/IMG_0379.jpg)

Well, today instead of working I had the pleasure of fixing the monitor 🙂 The monitor is an older Asus VW202 SR that my wife uses connected to the laptop. I tried everything else (power cycling, another signal cable, another computer) but it turns out to be really the button. The issue manifested itself by the brightness setting window appearing and going eventually all the way to 100. First I thought that the button was stuck in the frame but it was safely depressed. That means a broken button on the pcb board. I thought it would be pretty easy to solder a new one in place.

<!--more-->

But first I had to disassemble it:

![Asus monitor dissasembly step](/blog/images/2012/IMG_0366_v1.jpg)

1. Search and remove. There are 7 philips screws. 2 under rubber caps, 2 under flat foil, 2 holding the stand and 1 on the middle of the bottom frame. Make notes that the two of the stand are a different size.
![Asus monitor dissasembly step](/blog/images/2012/IMG_0368_v1.jpg)

One is hidden under the warranty seal.
![Asus monitor dissasembly step](/blog/images/2012/IMG_0369_v1.jpg")


Don't loose the rubber caps and place the flat ones with the adhesive side facing up. This way you can reuse them.
![Asus monitor dissasembly step](/blog/images/2012/IMG_0371_v1.jpg)

There are two openings in the frame at the bottom. Place the monitor facing up and use a plastic tool (or if, like me, you don't care about marks you can use a flat-head screwdriver) **Pull very gently** as the frame holds a small pcb board with the buttons and the power led. Disconnect it before lifting the frame.
![Asus monitor dissasembly step](/blog/images/2012/IMG_0372_v1.jpg)

That is the PCB that needs removing. You need to bend one of the plastic posts holding it in place. Be very careful not to snap it.
![Asus monitor dissasembly step](/blog/images/2012/IMG_0373_v1.jpg)

Make note of the button causing you troubles. For me it was menu right (toggles brightness when not in menu)
![Asus monitor dissasembly step](/blog/images/2012/IMG_0375_v1.jpg)

**Try not to open the wrong one** like I did! The problem was that I didn't have buttons like this to solder in place. So I tried to see if I can fix it. Ok this is a bit tricky. Use a magnifying glass if you need to. The button has a metal casing held in place by 4 _clamps_ (clasps? - for lack of a better term). I used a snapped syringe needle to gently lift it over the four clamps. Inside you will find a dome shaped metal disk (this is the one closing the circuit) and two plastic parts. Try to lift the casing without moving them and make note (take a picture) of their arrangement. It is important that they face the same way when assembling the button.

![Asus monitor dissasembly step](/blog/images/2012/IMG_0376_v1.jpg)

Not a good picture but enough detail on the bad button. The problem was caused by 1-2 metal particulates in the button. I cleaned it with a cotton swab. After you put the disc and the two plastic parts in place simply press the casing to snap in place.

![Asus monitor dissasembly step](/blog/images/2012/IMG_0377_v1.jpg)

Don't forget to connect the cable back to the PCB.

Do everything you did to get here in reverse to assemble the monitor!
