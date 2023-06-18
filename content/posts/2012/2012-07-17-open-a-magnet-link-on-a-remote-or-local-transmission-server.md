---
title: Open a magnet link on a remote (or local) transmission server.
author: silviu
type: post
date: 2012-07-17T19:37:51+00:00
url: /2012/07/17/open-a-magnet-link-on-a-remote-or-local-transmission-server/
dsq_thread_id:
  - 771163429
categories:
  - old
tags:
  - firefox
  - link
  - magnet
  - open
  - remote
  - temp_on
  - torrent

---
One of the services I run on my home server is a transmission daemon. I use it mainly to download images for my Raspberry PI, new distro iso's to play with in Virtualbox and so on. Recently there's been a move to replace torrent links with magnet links. I found a nice way to open those directly on the remote instance of the transmission daemon.

First create a script, let's call it simply `magnet.sh` and place it somewhere in your path, I chose `/usr/local/bin` but `~/bin` would work as well

```bash
#!/bin/bash
REMOTE='192.168.0.1'
ssh $REMOTE "sudo -u transmission /usr/bin/transmission-remote -add $1"
```

REMOTE is the remote host for which my workstation already has key based ssh authorization set up. Also note the sudo -u transmission. You can set up your remote directly as the use running the transmission-daemon and then this will no longer be necessary. Since I run my workstation as root and it connects to the server as root as well it is necessary for my setup.

After creating the script you will need to go in firefox to **about:config** and create a new boolean entry (New->Boolean) called `network.protocol-handler.expose.magnet` as `false`.

Next time you click a magnet link it will ask with what application to open it, navigate to your magnet script and set it.