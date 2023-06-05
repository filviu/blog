---
title: AIX git SSL woes
author: silviu
type: post
date: 2016-02-23T09:27:39+00:00
url: /2016/02/23/aix-git-ssl-woes/
dsq_thread_id:
  - 4603713954
categories:
  - tech
tags:
  - aix
  - bundle
  - ca
  - git
  - pem
  - ssl

---
Oh joy and happiness I have to admin AIX boxes. One of the first things I hit was using git to clone some stuff from github erroring out with:

```bash
SSL certificate problem: unable to get local issuer certificate
```

Yep, simple problem, no ssl ca bundle on the system. You can use either the **bulldozer solution** and have either:

```bash
export GIT_SSL_NO_VERIFY=true
```

either:

```bash
git config http.sslVerify false  ( git config --unset http.sslVerify )
```

because who cares about MITM attacks especially to deployed software on production servers.

Or you can go to **actually fix the issue** and install a ca bundle. I downloaded mine from the curl site, here: <https://curl.haxx.se/docs/caextract.html>

I downloaded the **cacert.pem** file and configured git to use it like this:

```bash
wget --no-check-certificate  https://curl.haxx.se/ca/cacert.pem -O /var/ssl/cacert.pem
git config --system  http.sslcainfo /var/ssl/cacert.pem
```

The no-check-certificate is required because at this point wget has no way of checking the certificate either. If you want to ensure the validity of the file download it from a working system and scp it to the remote problem server.