---
title: SSH key based authentication fails on a new computer
author: silviu
type: post
date: 2014-06-02T10:19:04+00:00
url: /2014/06/02/ssh-key-based-authentication-fails-on-a-new-computer/
dsq_thread_id:
  - 2737882139
categories:
  - old
tags:
  - bash
  - private key
  - ssh
  - temp_on

---
Having reinstalled one of my older laptops I noticed I cannot login using it's private key. I was sure I backed up the original and properly restored it after reinstalling. I ran ssh -v to get more information:

`Roaming not allowed by server` caught my eye. What the heck is that?

<!--more-->

```bash
root@darkstar:~/bin# ssh -v user@1.2.3.4
OpenSSH_6.6.1, OpenSSL 1.0.1g 7 Apr 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Connecting to 1.2.3.4 [1.2.3.4] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/id_rsa type 1
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: identity file /root/.ssh/id_ecdsa type -1
debug1: identity file /root/.ssh/id_ecdsa-cert type -1
debug1: identity file /root/.ssh/id_ed25519 type -1
debug1: identity file /root/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.0p1 Debian-4+deb7u1
debug1: match: OpenSSH_6.0p1 Debian-4+deb7u1 pat OpenSSH* compat 0x04000000
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx
debug1: Host '[1.2.3.4]:22' is known and matches the ECDSA host key.
debug1: Found key in /root/.ssh/known_hosts:1
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /root/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Trying private key: /root/.ssh/id_ecdsa
debug1: Trying private key: /root/.ssh/id_ed25519
debug1: No more authentication methods to try.
Permission denied (publickey).
```

Than I realized that before restoring the backed-up private key I generated a pair with `ssh-keygen` as I always do when installing a new system. This meant that I had the private key I restored but the public key was the one generated beforehand. I removed `id_rsa.pub` and this fixed it.