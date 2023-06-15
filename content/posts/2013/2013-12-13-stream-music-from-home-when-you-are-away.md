---
title: Stream music from home when you are away
author: silviu
type: post
date: 2013-12-13T07:03:11+00:00
url: /2013/12/13/stream-music-from-home-when-you-are-away/
dsq_thread_id:
  - 2047448326
categories:
  - old
tags:
  - home server
  - linux
  - music
  - stream
  - temp_on

---
I run a pretty powerful microitx system as my home router. Since it's always on (as oposed to my nas) I decided to add some storage so I can host my music and some tv shows. I checked some projects and stopped to test [Sockso][1].The site is simple and doesn't really scream "open source project" but sockso seems really good at what it does. It works both as a gui and as a server tool and is available for windows, linux and mac.

Site-ul nu arata foarte minunat dar programelul merge excelent. Eu l-am instalat in modul server (fara gui) dar merge si cu interfata grafica (evident mai usor de folosit) si pe windows si mac nu doar linux. (e scris in java dar merge surprinzator de bine in ciuda acestui fapt)

It's really easy to install:

  1. Go to <a href="http://sockso.pu-gh.com/" target="_blank" rel="noopener">http://sockso.pu-gh.com</a> and download the latest version
  2. unzip it – **unzip sockso-1.5.x.zip**
  3. Move it somewhere, I used /opt – **mv sockso-1.5.3  /opt**
  4. Install java jre if needed. **sudo apt-get installopenjdk-7-jre-headless**
  5. Now you can launch  **cd /opt/sockso-1.5.3 && java -jar sockso.jar –nogui**
  6. I don't use ssl because I only allow local access to socks (and use openvpn when I'm away from home as I trust it a lot more than securing each of those little applications)
  7. If you type **‘help’** you'll get a short usage list
  8. Add your first music folder – **coladd /home/myuser/music
** 
  9. Wait...
 10. Set it up so it will start on boot, I used  **/usr/bin/screen -dmS sockso /opt/sockso/sockso-start.sh** in **rc.local** (ugly, I know 🙂 ) **sockso-start.sh** is a small script that launches **java -jar sockso.jar –nogui –datadir /var/lib/sockso –ip=192.168.0.1 –locale=en**
 11. [Read the documentation][2] (there are more options than help will show), i.e. I disabled cover art, disabled user registration and set it up so it will work without a password.

 [1]: http://sockso.pu-gh.com/
 [2]: http://sockso.pu-gh.com/manual.html