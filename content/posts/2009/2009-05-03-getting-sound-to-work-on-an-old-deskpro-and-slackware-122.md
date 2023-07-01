---
title: Getting sound to work on an old Deskpro EN and Slackware 12.2
author: silviu
type: post
date: 2009-05-03T14:08:05+00:00
excerpt: I was trying to get rid of the separate sound card in an old Compaq Deskpro En (Pentium III) I use on a jukebox project. Easy job when you have the needed settings.
url: /2009/05/03/getting-sound-to-work-on-an-old-deskpro-and-slackware-122/
categories:
  - tech
tags:
  - alsa
  - slackware

---
I was trying to get rid of the separate sound card in an old Compaq Deskpro En (Pentium III) I use on a jukebox project. Alsa-conf would only detect some weird isa-pnp card that did not work. After searching a bit I found out that the card is an ESS 1869 and is not autodetected. Reading on the alsa website I found that these are the settings that work:

(set in `/etc/modprobe.d/sound`)

```bash
# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0

# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0

# card #1

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
```