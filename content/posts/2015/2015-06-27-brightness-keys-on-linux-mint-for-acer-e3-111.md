---
title: Brightness keys on Linux Mint for Acer E3-111
author: silviu
type: post
date: 2015-06-27T09:52:41+00:00
url: /2015/06/27/brightness-keys-on-linux-mint-for-acer-e3-111/
dsq_thread_id:
  - 3883814025
categories:
  - tech
tags:
  - acer
  - acpi
  - brightness
  - mint

---
Enabling brightness control is moderately easy (I&#8217;m pretty sure they worked&nbsp;out of the box on slackware).

Go to <https://github.com/codingtony/acer-brightness-linux-acpi> and follow the instructions. Change `/etc/acpi/events/acer-tm-brightness-down` and `/etc/acpi/events/acer-tm-brightness-up` with the correct events:

event=video/brightnessdown BRTDN 00000087 00000000

and

event=video/brightnessup BRTUP 00000086 00000000

Restart&nbsp;**acpid** and the shortcuts should start working.