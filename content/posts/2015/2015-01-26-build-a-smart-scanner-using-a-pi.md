---
title: Build a Smart Scanner using a PI
author: silviu
type: post
date: 2015-01-26T21:44:09+00:00
url: /2015/01/26/build-a-smart-scanner-using-a-pi/
dsq_thread_id:
  - 3465903166
categories:
  - old
tags:
  - dropbox
  - evernote
  - raspberry pi
  - scanner
  - temp_on

---
I got a free all-in-one printer from a friend who didn&#8217;t need it (consumed way too much ink cartridges). Since I liked the idea of the ScanSnap Evernote scanner but not so much the 500$ sticker price I decided to build one using this all in one and a Raspberry PI.

Fortunately the model I received is supported by [SANE][1].

I needed the following pieces put together:

  1. Interface (a few buttons to take color/grayscale lowres/high res photos)
  2. A command line utility to upload scanned pages to the _cloud_
  3. A daemon to monitor and trigger everything.

**Update:** I added rudimentary support for batch scanning, see the [GitHub project page][2].

## 1. Interface

First I wanted to build a nice GPIO based interface with leds, lcd, buttons. I started testing using a USB numpad I had around and it stuck, I&#8217;m too lazy to start working on it now that I have it running.

## 2. Cloud upload

I use a [Bash Dropbox Uploader][3]. It&#8217;s very nice as it allows running as a Dropbox application, giving it access only to one folder under Dropbox/Apps/

For the evernote part I&#8217;m waiting for resources support to be merged and functional inside geeknote [[here][4] and [here][5]]. For now Dropbox has to do.

## 3. Daemon

Again I thought it would be a good python learning experience to build it myself but laziness triumphed. I used [ESE Key Daemon][6] to monitor the USB Numpad and trigger [a small BASH utility][2] that accepts various resolutions and output formats as a parameter.

 [1]: http://www.sane-project.org/
 [2]: https://github.com/silviuvulcan/pi-cloud-scanner
 [3]: https://github.com/andreafabrizi/Dropbox-Uploader
 [4]: https://github.com/VitaliyRodnenko/geeknote/issues/95
 [5]: https://github.com/VitaliyRodnenko/geeknote/pull/113
 [6]: https://sites.google.com/site/blabdupp/esekeyd