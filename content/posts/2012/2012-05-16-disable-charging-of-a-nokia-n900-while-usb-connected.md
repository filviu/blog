---
title: Disable charging of a Nokia N900 while USB connected.
author: silviu
type: post
date: 2012-05-16T20:45:53+00:00
url: /2012/05/16/disable-charging-of-a-nokia-n900-while-usb-connected/
dsq_thread_id:
  - 692891622
categories:
  - old
tags:
  - charging
  - galaxy
  - host
  - maemo
  - n900
  - nokia
  - samsung
  - temp_on
  - usb

---
One of the joys of having a hackable computer serving as a phone is that you can do stuff which have no &#8220;option&#8221; in &#8220;settings&#8221;.  
Recently I wanted to see if I can connect it to an Android tablet (Samsung Galaxy Tab 10.1). I couldn&#8217;t. Too bad as I could really use the extra 32Gb the n900 has to offer. It would connect but the tablet disconnects it as soon as the phone tries to start charging.  
All I had to do was issue:  
[cce_bash]  
stop bme  
[/cce_bash]  
in a root console before connecting the phone to the tablet. After finishing I ran:  
[cce_bash]  
start bme  
[/cce_bash]  
to restore everything to normal.