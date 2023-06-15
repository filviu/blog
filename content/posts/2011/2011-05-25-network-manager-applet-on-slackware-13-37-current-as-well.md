---
title: network-manager-applet on Slackware 13.37 (current too) compile error
author: silviu
type: post
date: 2011-05-25T08:27:01+00:00
url: /2011/05/25/network-manager-applet-on-slackware-13-37-current-as-well/
dsq_thread_id:
  - 326907998
categories:
  - old
tags:
  - compile
  - error
  - network-manager-applet
  - networkmanager
  - temp_on

---
I took the time today to bring Network Manager and network-manager-applet (both very useful on my laptop where I have VPN's, 3G modems and various networks I connect to) First I brought all the dependencies up to date but network-manager-applet still refused to compile:
```bash
checking for GOBJECT... yes
checking for NMA... no
configure: error: Package requirements (dbus-glib-1 >= 0.74
glib-2.0 >= 2.16
NetworkManager >= 0.8.4
libnm-glib >= 0.8.4
libnm-util >= 0.8.4
libnm-glib-vpn >= 0.8.4
gtk+-2.0 >= 2.14
gmodule-export-2.0
gconf-2.0
gnome-keyring-1
libnotify >= 0.4.3) were not met:

No package 'gnome-keyring-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables NMA_CFLAGS
and NMA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```
Annoying as I had gnome-keyring installed and up to date. After a bit of poking around I realized that the missing dependency is in fact libgnome-keyring (alsa available at slackbuilds so easy enough to install as well)

**_Update:_** as the network-manager-applet package mantainer was so kind to reply to me the dependency is mentioned in gnome-keyring's README:

> gnome-keyring's README states that libgnome-keyring is required:
> <a href="http://slackbuilds.org/repository/13.37/misc/gnome-keyring/" target="_blank" rel="noopener">http://slackbuilds.org/repository/13.37/misc/gnome-keyring/</a>

<span style="color: #888888">I'll leave the post here in case you pay as much attention as I did.<br /> </span>