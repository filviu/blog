---
title: How to recreate the Show Desktop shortcut / icon
author: silviu
type: post
date: 2009-06-08T08:36:33+00:00
url: /2009/06/08/how-to-recreate-the-show-desktop-shortcut-icon/
dsq_thread_id:
  - 48858315
categories:
  - old
tags:
  - shortcut
  - show desktop
  - temp_on

---
My wife erased by mistake the _Show Desktop_ shortcut from the Quick Launch toolbar. So I needed to recreate it. Here are the needed steps:

Start **notepad**

**Copy and paste** this text in notepad:

```ini
[Shell]
Command=2
IconFile=explorer.exe,3
[Taskbar]
Command=ToggleDesktop
```

<span class="userInput"><strong>Save as</strong> Show Desktop.scf. Now move the shortcut anywhere you want it.</span>

<span class="userInput">Did you know that? I didn't 🙂 Also you might want to know that <strong>WIN+D</strong> (Win being the button between left CTRL and ALT that opens the Start Menu) does the same thing.<br /> </span>

**
**