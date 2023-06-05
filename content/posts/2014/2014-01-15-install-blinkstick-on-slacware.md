---
title: Install blinkstick on Slacware
author: silviu
type: post
date: 2014-01-15T07:46:46+00:00
url: /2014/01/15/install-blinkstick-on-slacware/
dsq_thread_id:
  - 2124382177
categories:
  - old
tags:
  - blinkstick
  - pip
  - python
  - temp_on

---
I recently built a [blinkstick][1], a cool little device. Using it under linux is very easy using the command line, but I had some issues installing it under Slackware:  
[cce_bash]  
pip install blinkstick  
Downloading/unpacking blinkstick  
Downloading BlinkStick-0.7.0.tar.gz  
Running setup.py egg_info for package blinkstick

Requirement already satisfied (use -upgrade to upgrade): grapefruit==0.1a3 in /usr/lib64/python2.7/site-packages (from blinkstick)  
Requirement already satisfied (use -upgrade to upgrade): webcolors in /usr/lib64/python2.7/site-packages (from blinkstick)  
Downloading/unpacking pyusb (from blinkstick)  
Could not find a version that satisfies the requirement pyusb (from blinkstick) (from versions: 1.0.0a2, 1.0.0a2, 1.0.0a3, 1.0.0a3, 1.0.0b1)  
Cleaning up&#8230;  
No distributions matching the version for pyusb (from blinkstick)  
Storing complete log in /root/.pip/pip.log  
[/cce_bash]

Checking the log shed some light:  
[cce_bash]  
Downloading/unpacking pyusb (from blinkstick)

Getting page https://pypi.python.org/simple/pyusb/  
URLs to search for versions for pyusb (from blinkstick):  
* https://pypi.python.org/simple/pyusb/  
Analyzing links from page https://pypi.python.org/simple/pyusb/  
Found link https://pypi.python.org/packages/source/p/pyusb/pyusb-1.0.0a2.tar.gz#md5=f6bed3e9b8a869a0043c36366ff28a14 (from https://pypi.python.org/simple/pyusb/), version: 1.0.0a2  
Found link https://pypi.python.org/packages/source/p/pyusb/pyusb-1.0.0a2.zip#md5=530240f21aabf1fa9a69739a1e0c9389 (from https://pypi.python.org/simple/pyusb/), version: 1.0.0a2  
Found link https://pypi.python.org/packages/source/p/pyusb/pyusb-1.0.0a3.tar.gz#md5=28f72453a7c0562cb8bd572758f6f7e1 (from https://pypi.python.org/simple/pyusb/), version: 1.0.0a3  
Found link https://pypi.python.org/packages/source/p/pyusb/pyusb-1.0.0a3.zip#md5=45a5ba190ca7a86fe71cfe9f6fb3065e (from https://pypi.python.org/simple/pyusb/), version: 1.0.0a3  
Found link https://pypi.python.org/packages/source/p/pyusb/pyusb-1.0.0b1.tar.gz#md5=5cc9c7dd77b4d12fcc22fee3b39844bc (from https://pypi.python.org/simple/pyusb/), version: 1.0.0b1  
Ignoring link https://pypi.python.org/packages/source/p/pyusb/pyusb-1.0.0a2.tar.gz#md5=f6bed3e9b8a869a0043c36366ff28a14 (from https://pypi.python.org/simple/pyusb/), version 1.0.0a2 is a pre-release (use -pre to allow).  
Ignoring link https://pypi.python.org/packages/source/p/pyusb/pyusb-1.0.0a2.zip#md5=530240f21aabf1fa9a69739a1e0c9389 (from https://pypi.python.org/simple/pyusb/), version 1.0.0a2 is a pre-release (use -pre to allow).  
Ignoring link https://pypi.python.org/packages/source/p/pyusb/pyusb-1.0.0a3.tar.gz#md5=28f72453a7c0562cb8bd572758f6f7e1 (from https://pypi.python.org/simple/pyusb/), version 1.0.0a3 is a pre-release (use -pre to allow).  
Ignoring link https://pypi.python.org/packages/source/p/pyusb/pyusb-1.0.0a3.zip#md5=45a5ba190ca7a86fe71cfe9f6fb3065e (from https://pypi.python.org/simple/pyusb/), version 1.0.0a3 is a pre-release (use -pre to allow).  
Ignoring link https://pypi.python.org/packages/source/p/pyusb/pyusb-1.0.0b1.tar.gz#md5=5cc9c7dd77b4d12fcc22fee3b39844bc (from https://pypi.python.org/simple/pyusb/), version 1.0.0b1 is a pre-release (use -pre to allow).  
Could not find a version that satisfies the requirement pyusb (from blinkstick) (from versions: 1.0.0a2, 1.0.0a2, 1.0.0a3, 1.0.0a3, 1.0.0b1)  
[/cce_bash]

Apparently my version of pip would not install pyusb by default, so I had to do:  
[cce_bash]  
pip install -pre blinkstick  
[/cce_bash]  
I plan to use it in my hp microserver behind the logo so I can glance server and raid status, as the default rgb led broke in mine and it also only turned red for fan or other hardware issues. What for would you use yours?

http://blinkstick.com/

 [1]: http://blinkstick.com/