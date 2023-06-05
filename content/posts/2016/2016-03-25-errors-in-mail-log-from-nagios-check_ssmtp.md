---
title: Errors in mail.log from nagios check_ssmtp
author: silviu
type: post
date: 2016-03-25T11:47:38+00:00
url: /2016/03/25/errors-in-mail-log-from-nagios-check_ssmtp/
dsq_thread_id:
  - 4692143174
categories:
  - tech
tags:
  - command
  - fail2ban
  - improper
  - nagios
  - pipelining
  - postfix

---
I got my nagios server banned by fail2ban because of errors in the postfix mail.log log. I know that I can simply whitelist the nagios server but I prefer it working perfectly.

Checking the logs I could see this error repeating itself on each check:

```bash
Mar 25 13:01:13 xxx-123 postfix/smtpd[17065]: connect from nagios.example.com[1.2.3.4]
Mar 25 13:01:13 xxx-123 postfix/smtpd[17065]: improper command pipelining after QUIT from nagios.example.com[1.2.3.4]:
Mar 25 13:01:13 xxx-123 postfix/smtpd[17065]: disconnect from nagios.example.com[1.2.3.4]
```

Apparently postfix is picky about having extra input after a QUIT or DATA command, see details [here][1].

It turns out that I haven't updated nagios plugins in a while. Even if I kept nagios up-to-date the plugins were at 2.0.3. Updating to 2.1.1 fixed the issue and now I simply see a connect/disconnect in the postfix logs when nagios performs a check.

 [1]: http://de.postfix.org/pipermail/postfix-users/2012-February/003165.html