---
title: Missing 5Ghz WiFi settings on Cisco E3200 with Tomato Shibby
author: silviu
type: post
date: 2015-05-20T06:33:49+00:00
url: /2015/05/20/missing-5ghz-wifi-settings-on-cisco-e3200-with-tomato-shibby/
categories:
  - old
tags:
  - cisco
  - e3200
  - shibby
  - temp_on
  - tomato

---
I followed the instructions and installed Tomat on my Cisco E3200 router without issue. I chose Tomato by Shibby specifically because it supports the 5GHz radio in this particular router model. But woe and behold after I installed the settings were not there, I could only see them for the 2.4GHz WiFi.

Well it turns out instructions are made to be followed, I got curious after install and logged right in, but it turns out you really have to do the last 30-30-30 reset.

Sure enough after the final 30-30-30 hard reset the settings for the 5GHz of my Cisco 3200 appeared and were functional.