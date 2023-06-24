---
title: Yahoo Messenger Michael Jackson virus
author: silviu
type: post
date: 2009-08-19T09:59:09+00:00
url: /2009/08/19/yahoo-messenger-michael-jackson-virus/
dsq_thread_id:
  - 48858459
categories:
  - old
tags:
  - instructions
  - messeneger
  - michael jackson
  - removal
  - Security
  - temp_on
  - virus
  - yahoo

---
![dead_smiley](/blog/images/2009/dead_smiley.jpg) A friend of mine got infected via Yahoo Messenger. The virus, spreads via mass messaging the following message:

<span style="color: #ff0000">HAHA Michael Jackson Gay 😀 >> http://looool.machiaeljack**ndied.com</span>

The link takes you to something that looks like a picture, but because the file name ends with what appears to the user as a web adress the final extension is .com not .jpg - and so you get tricked into running an executable.

**Automatic removal** can be done with the [Kaspersky Virus Removal tool](http://dnl-eu14.kaspersky-labs.com/devbuilds/AVPTool/).

**Manual removal is as follows:**

Remove these files (use unlocker if needed)

```shell
C:\Documents and Settings\<user>\Local Settings\Temp\174094.exe
C:\Documents and Settings\<user>\Local Settings\Temp\MichaelJackson_SUCKS.PIF (or any other similar file .pif and containing Michael Jackson in the name)
C:\Documents and Settings\<user>\Local Settings\Temp\svchost32.exe
C:\Documents and Settings\<user>\Local Settings\Temp\vshost32.exe
C:\vshost.exe
C:\autorun.inf</span>

_**
The last two will be on every partition your system has. Reboot and after starting go to My computer and DON'T double click the disks; Right click and choose explore and erase vshost.exe and autorun.inf from every partition in your system.
**_
Also remove the following registry key:

`[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run]` `"BootMgr"="C:\DOCUME~1\\LOCALS~1\Temp\svchost32.exe"`
