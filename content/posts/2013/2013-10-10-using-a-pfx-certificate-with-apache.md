---
title: Using a pfx certificate with Apache
author: silviu
type: post
draft: true
date: 2013-10-10T08:42:24+00:00
url: /2013/10/10/using-a-pfx-certificate-with-apache/
categories:
  - old
tags:
  - apache
  - certificate
  - pfx
  - ssl
  - temp_on

---
I had to install a certificate that came to me in pfx format. In order to use it with apache I had to convert it in a more manageable format.

With OpenSSL you can convert pfx to Apache compatible format easily with a few commands:

The first command extracts public key to example.com.crt, the second and third commands extracts the private key to example.com.key and the last one generates the Certificate Authority (CA) certificate example.com.ca file (if it cames out empty don't include it in the virtual host definition). Move all files to the apropriate locations for your distro and add them to the virtual host:


apachectl configtest and apachectl graceful restart and you are on your way!