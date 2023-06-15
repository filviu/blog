---
title: Akonadi is not starting, refuses to run as root (Slackware 13.0/13.1/13.37/current installation).
author: silviu
type: post
date: 2009-09-08T18:10:04+00:00
url: /2009/09/08/akonadi-is-not-starting-refuses-to-run-as-root-slackware-13-013-113-37current-installation/
dsq_thread_id:
  - 48856682
categories:
  - old
tags:
  - akonadi
  - mysql
  - slackware
  - temp_on

---
Well, I am having fun lately with the latest incarnation of the Slackware Linux distribution. Like I said before I am a slacker, and I like Slackware a lot. In a way it's nice that some things don't work out of the box. You get to know how they work.

Well, after my first startx I was greeted by a message stating that Akonadi failed to start / Akonadi fails to start. I had a hunch that it's missing his Mysql friend. **I configured mysql as explained [here][1]** and restarted KDE. It still didn't work, but I was on the right track.

I opened an xterm and ran:

```bash
mysqladmin create akonadi -p
```

hoping that it will help. Well, it didn't fix it either. The message informing that Akonadi fails to start also has an error log. Clicking on it I discovered that the problems were still Mysql related. So I went into Akonadi configuration, **changed the setting from local mysql (accessed through a socket) to server mode, typing in localhost, and an user and a password**.

**That fixed it !**

**UPDATE:**

**Akonadi**, in it's default configuration runs an internal **mysql** server which by default does not allow to be ran as root. Now this is all nice and well but I run my workstation as root. Yes, yes I know, but I still want to, my workstation, my rules. So here's how:

<div>
  <p>
    Edit<br /> ~/.local/share/akonadi/mysql.conf and add
  </p>

  <p>
    ```bash<br /> user=root<br /> ```
  </p>

  <p>
    to it. (you can choose any user as which this mysql instance will run but I really lost too much time with this nonsense already to bother)
  </p>

  <p>
    I know, I know, you should not run as root and everything but it’s my machine and I’ll run as whatever damn user I want.
  </p>
</div>

I also think that typing the correct path to the mysql socket would help too.

Have fun

 [1]: http://www.sgvulcan.com/configuring-mysql-in-slackware-13-0/