---
title: Switched to Chrome but magnet links open with kTorrent instead of custom script
author: silviu
type: post
date: 2015-03-17T12:23:41+00:00
url: /2015/03/17/switched-to-chrome-but-magnet-links-open-with-ktorrent-instead-of-custom-script/
categories:
  - old
tags:
  - chrome
  - magnet
  - temp_on
  - torrents

---
On one of my kde workstations I switched from firefox to chrome. One issue I found was that I have a custom script that takes magnet links and [adds them to my NAS server][1] instead of opening them locally. Chrome insisted on opening them with ktorrent instead of my custom script. The fix is to create a file `torrent.sh.desktop` inside `~/.local/share/applications/` with the following content:

```ini
[Desktop Entry]
Type=Application
Exec=/usr/local/bin/torrent.sh %u
MimeType=x-scheme-handler/magnet;
Name=torrent.sh
Icon=
NoDisplay=true
```

After that run:
```bash
kbuildsycoca4
```

 [1]: http://www.sgvulcan.com/open-a-magnet-link-on-a-remote-or-local-transmission-server/