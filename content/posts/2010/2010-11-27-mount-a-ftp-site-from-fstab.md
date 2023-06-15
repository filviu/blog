---
title: Mount a FTP site from fstab
author: silviu
type: post
date: 2010-11-27T18:56:47+00:00
url: /2010/11/27/mount-a-ftp-site-from-fstab/
dsq_thread_id:
  - 328202366
categories:
  - old
tags:
  - fstab
  - ftp
  - temp_on

---
I still have clients or websites where the most convenient (middle ages based) method of exchanging files is FTP.

Since I'm lazy by nature I don't like firing up a FTP client, I'd prefer to just have it available on request. For a while the KDE Network Places did the trick. But I decided I want it even easier. **Behold curlftpfs**.

One
```bash
sbopkg -ki curlftpfs
```
(replace that with apt-get, yum or compile from source depending on your distro)

later and I could do this in fstab:

```bash
curlftpfs#username:password@ftp.provider.com/folder /mnt/clientusingftp fuse rw,allow_other,noauto,user 0 0
```
I left noauto because access to this folder is slow on slower remotes hosts. Of course you can also do this at the command line:

[cceN_bash]
curlftpfs ftp://ftp.sunet.se/ sunet/
[/cceN_bash]
Cheers!