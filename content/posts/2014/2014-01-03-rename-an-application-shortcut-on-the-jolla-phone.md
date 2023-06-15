---
title: Rename an application shortcut on the Jolla phone
author: silviu
type: post
date: 2014-01-03T13:55:16+00:00
url: /2014/01/03/rename-an-application-shortcut-on-the-jolla-phone/
dsq_thread_id:
  - 2089469284
categories:
  - old
tags:
  - temp_on

---
Some time ago I bought OfficeSuite in the Google Play store and thought that it would be nice to have it running on my SailfishOS powered Jolla phone as well. I conacted mobisystems and they were nice enough to send me an activation code and links to the apk download. It installed and works fine (didn't do any fancy editing yet though) but the shortcut was named "com" and the icon was blank.

You need developer mode enabled. Start the terminal or login via ssh to your device.

First you need to become root and change to the folder containing application shortcuts

```bash
[nemo@localhost ~]$ devel-su
Password:
[root@localhost nemo]# cd /usr/share/applications/
[root@localhost nemo]# ls
```

In my case it was:

```bash
apkd_launcher_com_mobisystems_editor_office\__with__reg-com_mobisystems_office_splashScreen_SplashScreenActivity.desktop
``` 
(cool name, isn't it)

I used vi to edit it and changed `Name=com` to `Name=OfficeSuite` and the `Icon=some-long-name-to-a-missing-file.png` to `Icon=/var/lib/apkd/apkd_launcher_com_office_suite.png` You could also transfer the file and edit it on your computer instead but vi works fine (I can't remember but I think I actually installed vim using pkcon)

Then I prepared the icon for it on my pc. I searched for the officesuite png icon, resized it to 144&#215;144 pixels and copied on the phone. Still as root I ran:

```bash
[root@localhost nemo]# cp /home/nemo/apkd_launcher_com_office_suite.png /var/lib/apkd/apkd_launcher_com_office_suite.png
```

Not easy, but not really complicated either. If everything above seems like gibberish to you than please consider waiting for an application that would allow renaming of apps and changing of icons.
