---
title: Mini breadboard PSU
author: silviu
type: post
date: 2009-09-24T07:14:40+00:00
url: /2009/09/24/mini-breadboard-psu/
dsq_thread_id:
  - 48858504
categories:
  - old
tags:
  - breadboard
  - lm7805
  - psu
  - temp_on

---
I bet this was discussed and sampled 1000 times before but here is the mini 5V PSU I use for my microcontroler breadboard projects. Usually you will use a 5 volt DC power supply for your microcontroller projects. Since I got tired of breadboarding the power source part all the time, I built a small PSU to power up my projects. I used a screw-in terminal for power input and I simply soldered pins that stick directly into the bread board for the output part.

<p style="text-align: center">
  <a href="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/09/5v_mini_psu.png"><img decoding="async" loading="lazy" class="aligncenter size-full wp-image-507" title="5v_mini_psu" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/09/5v_mini_psu.png" alt="5v_mini_psu" width="632" height="246" /></a>
</p>

I'll follow up with pictures soon.

C1 should be at least 25V. C3 can be lower (16V, etc.) R1 should be adequate for the LED you choose at 5V - use an online led calculator for that. I sugest 480 - 1K for a red led.

You can power it up using a 9V battery or a small DC adapter depending on your projects need. If the consumption is high you'll need to use a heatsink  for the LM7805 regulator.

Have fun!