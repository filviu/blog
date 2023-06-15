---
title: 'stdin: is not a tty'
author: silviu
type: post
date: 2011-11-18T11:22:08+00:00
url: /2011/11/18/stdin-is-not-a-tty/
dsq_thread_id:
  - 476967335
categories:
  - old
tags:
  - biff
  - interactive
  - mesg
  - temp_on
  - tty

---
This was a new one for me. Received when doing automated remote log-ins on a cPanel server. The scripts would be confused by the following message:

```bash
stdin: is not a tty
```

It was  caused by the following line in .bashrc (note that it could be in /etc/bashrc or /etc/profile, all those are on the **target** host)

```bash
mesg y
```

Often it can be caused by **biff y** as well.

Replacing the line with the following should fix it:
```bash
if \`tty -s \` && \`test -x /usr/bin/mesg\`; then
mesg y
fi
```
What happens is that some program in your bashrc (or one sourced automatically from /etc ) is expecting the shell to be interactive when it's not (for example you run commands over ssh). The fix is to find the problematic program and test for an interactive shell before calling it.