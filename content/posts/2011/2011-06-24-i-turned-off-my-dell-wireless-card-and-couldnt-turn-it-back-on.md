---
title: I turned off my dell wireless card and couldn’t turn it back on
author: silviu
type: post
date: 2011-06-24T08:48:30+00:00
url: /2011/06/24/i-turned-off-my-dell-wireless-card-and-couldnt-turn-it-back-on/
categories:
  - old
tags:
  - atheros
  - dell
  - disabled
  - enabled
  - off
  - on
  - rfkill
  - temp_on
  - wi-fi

---
Among others I work on a Dell Vostro A860 Laptop. It's running Slackware 64 Current. Yesterday I wanted to watch a movie while waiting at the airport for my wife so I turned off Wi-Fi using FN+11 (pressed a few times until both Bluetooth and wi-fi were disabled).

Today when I booted wi-fi was not working. I kept pressing FN+11 (as the laptop toggles trough combination of bluetooth off/on, wi-fi off/on, and any other possible combination). I used `rfkill list all` to check their status. I got to the point when both radios were reporting `Hard blocked : no` but Soft Blocked for wi-fi was still on. I tried restarting Network Monitor, removing the Atheros kernel module and everything else that came to mind. Than I remembered that documentation could be something useful. So I found that I need to run:

```bash
rfkill unblock wifi
```

Easy enough, wi-fi connected properly again.