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
[<img decoding="async" loading="lazy" class="alignleft size-full wp-image-447" title="dead_smiley" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/08/dead_smiley.jpg" alt="dead_smiley" width="146" height="143" />][1]A friend of mine got infected via Yahoo Messenger. The virus, spreads via mass messaging the following message:

<span style="color: #ff0000">HAHA Michael Jackson Gay 😀 >> http://looool.machiaeljack**ndied.com</span>

The link takes you to something that looks like a picture, but because the file name ends with what appears to the user as a web adress the final extension is .com not .jpg - and so you get tricked into running an executable.

**Automatic removal** can be done with the <a href="http://dnl-eu14.kaspersky-labs.com/devbuilds/AVPTool/" target="_blank" rel="noopener">Kaspersky Virus Removal tool</a>.

**Manual removal is as follows:**

Remove these files (use unlocker if needed)

<span style="color: #333399">C:Documents and Settings<user>Local SettingsTemp174094.exe<br /> C:Documents and Settings<user>Local SettingsTempMichaelJackson_SUCKS.PIF (or any other similar file .pif and containing Michael Jackson in the name)<br /> C:Documents and Settings<user>Local SettingsTempsvchost32.exe<br /> C:Documents and Settings<user>Local SettingsTempvshost32.exe<br /> C:vshost.exe<br /> C:autorun.inf</span>

_**  
The last two will be on every partition your system has. Reboot and after starting go to My computer and DON'T double click the disks; Right click and choose explore and erase vshost.exe and autorun.inf from every partition in your system.  
**_ 

Also remove the following registry key:

<span style="color: #333399">[HKEY_CURRENT_USERSoftwareMicrosoftWindowsCurrentVersionRun] “BootMgr”=”C:\DOCUME~1\\LOCALS~1\Temp\svchost32.exe”</span>

 [1]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/08/dead_smiley.jpg