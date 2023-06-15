---
title: N800/N810 tablet as a Canon camera remote
author: silviu
type: post
date: 2009-05-27T09:37:46+00:00
excerpt: I found a way to use a Nokia N800/N810 tablet as a Canon camera remote control. You can shoot, download and view your pictures on the big screen.
url: /2009/05/27/n800n810-tablet-as-a-canon-camera-remote/
dsq_thread_id:
  - 48858232
categories:
  - tech
tags:
  - 10d
  - canon
  - eos
  - n800
  - remote
  - s10h

---
This post is also on the talk.maemo.org forum, but I decided to host it here too.<figure class="wp-block-image">

<img decoding="async" src="https://talk.maemo.org/attachment.php?attachmentid=1198&stc=1&d=1206045723" alt="" /> <figcaption>N800 camera remote control</figcaption></figure>
I followed a thread regarding the port of gphoto for the Nokia Internet Tablets. Unfortunately gphoto
never got me further than list the photos in the camera and then hang and reboot.

Well then I noticed [Eostimesync][1].

Eostimesync is a nice utility that syncs the time of your camera to the time of the n800. I liked it because I could sync my tablet to ntp and switch between host and client usb mode all from one applet. The camera sync was pretty much useless to me. But I wanted to know how it works. To make a long story short eostimesync uses a command line program named s10sh which is an userspace usb driver for canon cameras (many of them if I'm corect).

First thing linux taught me in 1998 was to type at the prompt:

`command --help`

So as root s10sh has the ability to:

  * Get ALL/ALL NEW images
  * List ALL/ALL NEW images
  * Set camera to computer time

and many more. The above are non interactive and are the ones useful for me. If you run simply s10sh it will give you an interactive shell similar to a DOS prompt. Of course your camera has to be connected by usb and your tablet must be in HOST mode. Oh and my camera has two usb modes "normal" - which is the canon proprietary format and the one that works with all the above and PTP which is only for image download. On your camera the modes could be labeled differently.

So, running `s10sh -c` does, according to the -help:

capture an image with the current camera settings (that's your remote)
`<br>s10sh -c (capture)<br>s10sh -n (get all new images, non-interactive)<br>`

quiver imagename.jpg (see what you shot on the big screen)

See why I'm so excited about?

Oh and the camera is completely functional even when connected. I can shoot, change settings anything. I do landscapes a lot so I could imagine myself leaving the camera on the tripod and the n800 connected to use as trigger or big screen for more detail. also it would be helpful when doing macro. And of course it's a LOT of FUN !

I also think you can change camera settings but I didn't explore that.

A nice gui for s10h would be great, with buttons for settings, shoot, view last shot. Maybe someday...

Let me know what you think.You can also follow the discussion [here][2] (talk.maemo.org).

 [1]: https://garage.maemo.org/projects/eostimesync/
 [2]: http://talk.maemo.org/showthread.php?t=18143