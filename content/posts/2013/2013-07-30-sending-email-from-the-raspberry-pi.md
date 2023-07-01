---
title: Sending email from the Raspberry PI
author: silviu
type: post
date: 2013-07-30T11:17:32+00:00
url: /2013/07/30/sending-email-from-the-raspberry-pi/
categories:
  - old
tags:
  - email
  - mta
  - temp_on

---
I run a remote Raspberry PI gracefully hosted by the people over at [raspberrycolocatie.nl][1] Since one if it's jobs is to run a few scripts monitoring various bits and pieces I want it to be able to send emails. Since I don't want to use a full blown MTA I settled for [ssmtp][2].

_**It's worth noting that this setup applies to any debian box, not only the rPI.**_

> <p id="sSMTP_-_Simple_SMTP" style="padding-left: 30px">
>   <strong>sSMTP - Simple SMTP</strong>
> </p>
> 
> <p style="padding-left: 30px">
>   sSMTP is a simple MTA to deliver mail from a computer to a mail hub (SMTP server). sSMTP is simple and lightweight, there are no daemons or anything hogging up CPU; Just sSMTP. Unlike Exim4, sSMTP does not receive mail, expand aliases, or manage a queue.
> </p>

Here are the few, simple steps needed to get it up and running:

**Install ssmtp using apt-get (sudo or run it as root)**

```bash

sudo apt-get install ssmtp
Reading package lists... Done
Building dependency tree
Reading state information... Done

(...snip...)

Setting up libgnutls-openssl27:armhf (2.12.20-7) ...
Setting up ssmtp (2.64-7) ...
```

Configure ssmtp to use an email account. _Note that ssmtp sends mail as a client to a remote mail server (i.e. gmail) not as a traditional MTA_. Be sure to adjust ports and TLS settings according to your setup.

Edit `/etc/ssmtp/ssmtp.conf` to look like below:

```ini
#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=account@example.com

# The place where the mail goes. The actual machine name is required no
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=mail.example.com:587

# Where will the mail seem to come from?
#rewriteDomain=

# The full hostname
hostname=account@example.com

UseTLS=YES
UseSTARTTLS=YES
AuthUser=account@example.com
AuthPass=secretPassword

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
FromLineOverride=YES
```

Edit `/etc/ssmtp/revaliases`

```ini
# sSMTP aliases
#
# Format:       local_account:outgoing_address:mailhub
#
# Example: root:your_login@your.domain:mailhub.your.domain[:port]
# where [:port] is an optional port number that defaults to 25.
root:account@example.com:mail.example.com:587
```

Install mailx and test sending.

```bash
apt-get install mailutils

(... snip ...)

Setting up mailutils (1:2.99.97-3) ...
```

```bash
mailx destination@example.com
Cc:
Subject: Test Message
Enter some text here
End with CTRL+D to send
```

Simple!

 [1]: http://raspberrycolocatie.nl/
 [2]: https://wiki.debian.org/sSMTP