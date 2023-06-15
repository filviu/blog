---
title: Recover your lost linux slackware root password
author: silviu
type: post
date: 2009-05-28T13:31:13+00:00
url: /2009/05/28/recover-your-lost-linux-slackware-root-password/
dsq_thread_id:
  - 48858274
categories:
  - old
tags:
  - linux
  - password
  - root
  - slackware
  - temp_on

---
I'm an avid Slackware user. It was the distro I started using back in '98 and, even if I tried and used many others I still like it the most. Anyways these rules apply to many other flavours of linux.

One of the problems I faced is needing to make changes on inherited machines that nobody knew the passwords for. So, if you face the same problem, or you simply forgot the root password because you usually use a normal user account here's what you have to do to reset the password.

What you need: a bootable linux cd or flash usb drive. (You could use the slackware install disk, but any bootable, or Live CD should do as long as it has drivers for your filesystem and basic hardware)

You need to reboot the machine and boot it of the CD/USB stick. For the sake of the demonstration I will asume you use the slackware 12.2 install disk. If you use another just boot it and open a shell/console.

Log in as root.

Create a temporary directory to mount your / (root) partition where Slackware Linux is installed:
```bash
mkdir /tmppart
```
Mount your partition there:
```bash
mount /dev/hda1 /tmppart
```
Of course you need to replace hda1 with the partition where / is on your drive. Next you need to edit /etc/shadow to remove the root password.
```bash
vi /tmppart/etc/shadow
```
Locate the line starting with root: followed by letters and numbers. It's easy, it's usually the first line in the file. Remove everything between the first two **:** . Alternatively, if you know the password of another user copy everything from between the first two **:** to the root user.  Save the file and reboot.

Root should now have no password / a password identical with the one of the user you copied it from.

Easy. Useless to say that you must understand that if you don't own the system / don't have express permission from the owner you are doing something illegal. If you get arrested/fired it's your problem.