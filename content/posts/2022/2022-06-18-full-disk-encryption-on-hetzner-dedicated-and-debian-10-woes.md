---
title: Full Disk Encryption on Hetzner Dedicated and Debian 10 Woes
author: silviu
type: post
date: 2022-06-18T13:41:37+00:00
url: /2022/06/18/full-disk-encryption-on-hetzner-dedicated-and-debian-10-woes/
categories:
  - tech
tags:
  - debian
  - full disk encryption
  - hetzner
  - linux
  - ssh

---
As absolutely nobody knows or uses I maintain an [ansible role](https://github.com/filviu/ansible-role-hetzner_installimage) that can setup a Debian or Ubuntu machine with full disk encryption on Hetzner Robot (baremetal dedicated machines).
But wait, you shout, Hetzner usually runs consumer grade stuff without kvm's - how do you enter your password at bootime. Easy, the role sets up a minimal boot environment with a dropbear ssh server where you can login and do `cryptroot-unlock`.

While developing the role I realised that it was impossible to unlock a Debian 10 machine, even though I was 100% sure ansible was adding the proper key logging in to the boot envirnment was impossible, I kept getting

```bash
Permission denied (publickey).
```

I lost some good hours troubleshooting being sure ansible was somehow not adding the proper key. Until I searched the web and realised the version of dropbear shipped with Debian 10 does not support the ed25519 keys I so cheerfully use for the added security and elegant shortness.

So the fix was, for Debian 10 machines, to maintain a rsa key to use when logging in to boot the machines.