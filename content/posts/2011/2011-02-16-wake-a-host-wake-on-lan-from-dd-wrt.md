---
title: Wake a host (wake on lan) from dd-wrt
author: silviu
type: post
date: 2011-02-16T13:45:00+00:00
url: /2011/02/16/wake-a-host-wake-on-lan-from-dd-wrt/
dsq_thread_id:
  - 327220101
categories:
  - old
tags:
  - temp_on

---
## WOL through Telnet/SSH

**Note:** This is the preferred method to send WOL magic packets remotely. If you have local or remote Telnet/SSH access to your router, you can wake up a machine on the LAN by using the following command:

```bash
/usr/sbin/wol -i 192.168.1.255 -p PP AA:BB:CC:DD:EE:FF
```

Note that the full path to "/usr/sbin/wol" is important. Simply "wol" will not work.

Substitute _AA:BB:CC:DD:EE:FF_ with the actual MAC address of the computer which you wish to boot remotely. Likewise, replace _192.168.1.255_ with the actual broadcast address of the network (192.168.1.255 is the broadcast address when the machine has an IP of 192.168.1.x and subnet mask of 255.255.255.0). Replace "PP" with the port number your machine listens on (usually 7 or 9).