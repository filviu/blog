---
title: Speed-up X over ssh
author: silviu
type: post
date: 2013-01-31T08:07:16+00:00
url: /2013/01/31/speed-up-x-over-ssh/
categories:
  - old
tags:
  - lan
  - network
  - optimize
  - speed
  - ssh
  - temp_on
  - vpn
  - x

---
Even though I run a pretty fast network and vpn at home I still have the occasional hiccup running demanding applications (i.e. [digikam][1]) at home.

A few simple options can speed up X considerably. Connecting with the following parametters will enable a fast encryption cipher and also enables compression:

```bash
ssh -X -C -c blowfish-cbc,arcfour user@host.example.com
```

Of course you can make this permanent by adding the following to `/etc/ssh/ssh_config` or even better only for the specific host in `~/.ssh/config` (might be different on your distro):

```ini
Cipher blowfish
# default line
##Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
## see man page for more info on Ciphers
Ciphers blowfish-cbc,aes128-cbc,3des-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
Compression yes
```

 [1]: http://www.digikam.org/