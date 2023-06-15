---
title: Windows 7 small arrow icons for Desktop shortcuts
author: silviu
type: post
date: 2009-10-18T20:21:06+00:00
url: /2009/10/18/windows-7-small-arrow-icons-for-desktop-shortcuts/
dsq_thread_id:
  - 48858513
categories:
  - old
tags:
  - 7
  - arrow
  - icon
  - shortcut
  - temp_on
  - Windows

---
Many  guides found online will show you how to completely remove the arrow of the desktop shortcuts. If you, like me, preffer the smaller shortcut arrow icon that Windows XP has, as opposed to the big one Windows 7 proudly shows here's what you have to d:

Start  **regedit** (Alt+R, regedit.exe, enter)**
**
 ****
Go to:

 **HKEY_LOCAL_MACHINESOFTWAREMicrosoft WindowsCurrentVersionExplorerShell Icons**
If  **Sell Icons** is not there, under Explorer create the new key. (Right cklick, new key)

In the right pane create a new **String Value** with the name **29**.

Right click on this value and choose Modify.

Type the following as it's value:
**c:windowsSystem32shell32.dll,29** and click **ok**.

Restart you computer to see the effects.

_Please note that 29 after the comma is the respective icon from inside **shell32.dll**_