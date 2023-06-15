---
title: Ubuntu 22.04 Dislikes RSA Keys
author: silviu
type: post
date: 2022-06-18T14:01:33+00:00
url: /2022/06/18/ubuntu-22-04-dislikes-rsa-keys/
categories:
  - tech

---
I wrote in a past article about how I'm <a href="https://www.silviuvulcan.ro/2022/06/18/full-disk-encryption-on-hetzner-dedicated-and-debian-10-woes/" data-type="URL" data-id="https://www.silviuvulcan.ro/2022/06/18/full-disk-encryption-on-hetzner-dedicated-and-debian-10-woes/">setting up Hetzner dedicated servers with full disk encryption</a> even if they miss an ikvm and why Debian 10 machines require a RSA key for this.

But since I switched one of my workstations to Ubuntu 22.04 I was unable to login using this RSA key. Running ssh with debug enabled showed the likely culprit:
```bash
debug1: Offering public key: /home/user/.ssh/id_rsa
debug1: send_pubkey_test: no mutual signature algorithm
```

The message sent me on the right track, Ubuntu 22.04 has disabled RSA keys support by default. I'm not arguing with that, I don't really like using RSA since better alternatives are around so I don't want to change this default, but still I would like to be able to reboot my Debian 10 servers. So a command line option later I was able to use RSA keys only when I want them:

```bash
ssh -o PubkeyAcceptedKeyTypes=+ssh-rsa root@1.2.3.4
```