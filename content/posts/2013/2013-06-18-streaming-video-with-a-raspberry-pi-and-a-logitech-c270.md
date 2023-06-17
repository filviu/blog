---
title: Streaming video with a Raspberry PI and a Logitech C270
author: silviu
type: post
date: 2013-06-18T18:31:57+00:00
url: /2013/06/18/streaming-video-with-a-raspberry-pi-and-a-logitech-c270/
dsq_thread_id:
  - 1410419391
categories:
  - old
tags:
  - gstreamer
  - raspberry pi
  - stream
  - temp_on
  - webcam

---
Hi,

I wanted to setup a live webcam using a Raspberry Pi (model B, first rev. with 256M RAM) so after checking and happily finding out that my camera is suported I went along. First I installed the support packages:

```bash
sudo apt-get install gstreamer-tools gstreamer0.10-plugins-bad gstreamer0.10-plugins-good v4l-utils
```

After that I wrote a small script that would start the stream:

```bash
#!/bin/bash
# set below your Raspberry PI IP address
myip="192.168.xxx.xxx"
port="5000"

gst-launch -v v4l2src ! "image/jpeg,width=1280,height=720,framerate=30/1" ! multipartmux ! tcpserversink host=$myip port=$port sync=false
```

Save this to a script and set it to start on boot (if you want).

After the stream is running you could check it with VLC for example:

```bash
vlc tcp://192.168.xxx.xxx:5000
```

_**Notes:**_

  * I got my inspiration [from here][1] (the author also has a simple android app for viewing the stream)
  * Yes, I can stream HD with low CPU usage (it starts to hickup after running 7 clients)
  * I couldn't get audio to work. Maybe it has something to do with this camera as CPU usage is very low. The source blog has details on how to enable audio but I couldn't get it to work
  * I tried using ffmpeg (if you want audio support remember to install libasound2-dev before compiling ffmpeg) but audio still didn't work
  * The camera would randomly fail after a few minutes and gstreamer would crash. Because I didn't want to use a powered USB hub I bridged the polyfuses as [described here][2]. If you have the newer rev. 2 (with 512M RAM) that might not be necessary. Do note that this PI has no keyboard, wi-fi dongle or video out and uses a 2A power supply. Now the stream remains stable.

 [1]: http://sanjosetech.blogspot.ro/2013/05/raspberry-pi-streaming-video-and.html
 [2]: http://theiopage.blogspot.ro/2012/06/increasing-raspberry-pis-usb-host.html