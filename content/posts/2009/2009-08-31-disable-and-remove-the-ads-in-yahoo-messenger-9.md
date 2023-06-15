---
title: Disable and Remove the ads in Yahoo! Messenger 9 or 10 beta
author: silviu
type: post
date: 2009-08-31T06:21:40+00:00
url: /2009/08/31/disable-and-remove-the-ads-in-yahoo-messenger-9/
dsq_thread_id:
  - 48858471
categories:
  - old
tags:
  - disable ads
  - temp_on
  - yahoo messenger

---
Yahoo! Messenger 9.0 is the current stable messenger version (Yahoo messenger 10 is in beta). As with any previous versions of Yahoo Messenger, there are various ads displayed in the bottom of the contacts list or inside message and chat windows. These ads can be disabled using a simple registry hack:

  1. Start regedit. (Run -> regedit.exe)
  2. Go to this registry key: HKEY_CURRENT_USERSoftwareYahoopagerLocale
  3. On the right you should see a Value called **Enable Messenger Ad**. Change it's value from **1** to ****.

Restart Yahoo! Messenger and the ads should be gone.

I just tried it, and for now this hack doesn't work in Yahoo! Messenger 10 Beta too. Changing the setting makes the ads dissaper just for some time. After a minute or so they appear again. I'll keep you updated.