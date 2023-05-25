---
title: Make sensors report temperature on slackware64-current with an Intel I7 2600k
author: silviu
type: post
date: 2012-01-27T20:01:49+00:00
url: /2012/01/27/make-sensors-report-temperature-on-slackware64-current-with-an-intel-i7-2600k/
dsq_thread_id:
  - 554948999
categories:
  - old
tags:
  - 2600k
  - i7
  - linux
  - slackware
  - temp_on
  - temperature

---
For some reasons the required modules don&#8217;t get loaded. Add the following to /etc/rc.d/rc.modules right above the line reading ### Mouse support:

[CCE_BASH]  
\### by SV for i2600k temperature  
/sbin/modprobe coretemp  
/sbin/modprobe pkgtemp  
[/CCE_BASH]

Now sensors report the temperatures.