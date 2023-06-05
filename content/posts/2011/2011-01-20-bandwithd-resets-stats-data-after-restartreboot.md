---
title: BandwithD resets stats data after restart/reboot
author: silviu
type: post
date: 2011-01-20T11:49:51+00:00
url: /2011/01/20/bandwithd-resets-stats-data-after-restartreboot/
dsq_thread_id:
  - 330916469
categories:
  - old
tags:
  - across
  - bandwidthd
  - persist
  - reboot
  - restart
  - temp_on

---
This was a funny one:

I have installed the <a target="_blank" href="http://sourceforge.net/projects/bandwidthd/" rel="noopener">Bandwithd</a> monitoring software on a machine. I noticed that the monitoring data kept being erased between start/stop or reboot. There actually are two configuration settings which are false by default that allows BandwidthD to keep it's data across restart's (or system reboots) and those are

(in /etc/bandwidthd.conf)  
[ccNe_bash]  
#Log data to cdf file htdocs/log.cdf  
output_cdf true

#Read back the cdf file on startup  
recover_cdf true  
[/ccNe_bash]  
  
(they are false by default, you need to set them true like above)