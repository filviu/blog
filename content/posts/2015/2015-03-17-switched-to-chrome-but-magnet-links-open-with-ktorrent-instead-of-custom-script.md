---
title: Switched to chrome but magnet links open with kTorrent instead of custom script
author: silviu
type: post
date: 2015-03-17T12:23:41+00:00
url: /2015/03/17/switched-to-chrome-but-magnet-links-open-with-ktorrent-instead-of-custom-script/
dsq_thread_id:
  - 3623393324
categories:
  - old
tags:
  - chrome
  - magnet
  - temp_on
  - torrents

---
On one of my kde workstations I switched from firefox to chrome. One issue I found was that I have a custom script that takes magnet links and [adds them to my NAS server][1] instead of opening them locally. Chrome insisted on opening them with ktorrent instead of my custom script. The fix is to create a file [cci\_bash]torrent.sh.desktop[/cci\_bash] inside [cci\_bash]~/.local/share/applications/[/cci\_bash] with the following content:

[ccNe_bash]  
[Desktop Entry]  
Type=Application  
Exec=/usr/local/bin/torrent.sh %u  
MimeType=x-scheme-handler/magnet;  
Name=torrent.sh  
Icon=  
NoDisplay=true  
[/ccNe_bash]

After that run [cci\_bash]kbuildsycoca4[/cci\_bash]

 [1]: http://www.sgvulcan.com/open-a-magnet-link-on-a-remote-or-local-transmission-server/