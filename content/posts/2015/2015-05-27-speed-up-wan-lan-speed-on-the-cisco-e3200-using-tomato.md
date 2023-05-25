---
title: Speed-up WAN-LAN speed on the Cisco E3200 using Tomato
author: silviu
type: post
date: 2015-05-27T10:15:43+00:00
url: /2015/05/27/speed-up-wan-lan-speed-on-the-cisco-e3200-using-tomato/
dsq_thread_id:
  - 3797364768
categories:
  - old
tags:
  - bcm_nat
  - cisco
  - fastnat
  - temp_on
  - tomato

---
There&#8217;s a really long discussion on bcm_nat and fastnat on the various forums like [linksysinfo][1]. The short version of this is:

  1. fastnat and bcm_nat are disabled by default because they break QOS and access restrictions. If you use any of those you&#8217;re done, you have to choose features or speed or another router.
  2. If you, like me, don&#8217;t use those you can do the following:  
    ssh into your router and try: [cci\_bash]modprobe bcm\_nat[/cci\_bash] than speedtest your connection a few times you should see some improvement. Than run [cci\_bash]echo &#8220;1&#8221;> /proc/sys/net/ipv4/netfilter/ip\_conntrack\_fastnat[/cci_bash] you shold see an even better improvement. If any of those give you issues simply reboot your router, nothing is permanent at this time.
  3. Add the commands to Administration->Scripts->Init.

The instructions are deliberately scarce, if you don&#8217;t understand them it&#8217;s better not to mess with your router. Check the tomato forums and the linux documentation about those commands until you&#8217;re sure you know what they are doing.

 [1]: http://www.linksysinfo.org/