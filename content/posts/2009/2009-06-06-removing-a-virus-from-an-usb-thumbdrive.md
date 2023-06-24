---
title: Removing a virus from an USB Thumbdrive
author: silviu
type: post
date: 2009-06-06T12:49:43+00:00
url: /2009/06/06/removing-a-virus-from-an-usb-thumbdrive/
dsq_thread_id:
  - 48858306
categories:
  - old
tags:
  - spyware
  - temp_on
  - virus

---
I have seen a lot of usb thumbdrives with viruses lately, even cards from cameras and mp3 players. When you insert a new drive windows will pop up a message with stuff you can do (play, open, etc). If you have the slightest suspicion of infection click **cancel**.

![infected_usb_stick_autorun_message](/blog/images/2009/infected_usb_stick_autorun_message.jpg) 

Infected usb drive autorun message. Notice the two Open folder to view files?

Most of the times, when the drive is infected some of the icons will look weird: 

**Unknow program** type icons, **two open folder to view files** entries, and so on.  So, any of those show up, or you have used your stick on a suspect computer (or a public terminal) you probably have a virus. So, click cancel. If there's nothing you need on the stick stop right here. Just go to my computer, right click on the drive and **format** it. The virus, **along with all your files** will be gone.

If you need the files it's going to be a little trickyer:

Go to **My computer**. **Right** click on the problem disk and choose **explore**. NOT open, run or anything else. Make sure windows is set to show hidden and system files. DELETE the following file and folders:

autorun.inf, RECYCLED, RECYCLER, and any other suspicious file or folder it is not yours. Be careful not to run or launch anything.

Done, all clean.