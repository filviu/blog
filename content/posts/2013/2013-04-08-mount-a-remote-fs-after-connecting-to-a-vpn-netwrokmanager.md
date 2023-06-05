---
title: Mount a remote fs after connecting to a vpn. (NetwrokManager)
author: silviu
type: post
date: 2013-04-08T07:12:18+00:00
url: /2013/04/08/mount-a-remote-fs-after-connecting-to-a-vpn-netwrokmanager/
dsq_thread_id:
  - 1195534990
categories:
  - old
tags:
  - auto
  - mount
  - network manager
  - sshfs
  - temp_on
  - vpn

---
When away I use a vpn connection to connect to my home server. The first thing after connecting is usually mounting some resources using sshfs (yes I know, not very efficient but for personal use is more than enough). I wanted to automate that and so I dug a bit around NetworkManager.

Apparently all you have to do is drop a script similar to this in **/etc/NetworkManager/dispatcher.d/**

[cce_bash]

#!/bin/bash  
interface=$1  
status=$2

LOG="/var/log/network\_manager\_custom.log"

if [ "$CONNECTION_UUID" = "xxx-xxx-xxx" ]; then  
case $status in  
vpn-up)  
mount /mnt/something >> $LOG 2>&1  
;;  
vpn-down)  
umount /mnt/something >> $LOG 2>&1  
;;  
esac  
fi  
[/cce_bash]

Make it executable and be sure it is not world writeable.