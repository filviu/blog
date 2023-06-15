---
title: Clear Windows 7″Recent Items”/ jumplists
author: silviu
type: post
date: 2011-09-21T18:44:29+00:00
url: /2011/09/21/clear-windows-7recent-items-jumplists/
dsq_thread_id:
  - 421755896
categories:
  - old
tags:
  - hidden
  - jumlist
  - recent items
  - scheduler
  - task
  - temp_on
  - Windows

---
I hate windows's jump lists. If you read this you probably hate them too 🙂

They are stored as hidden files in a, you guessed, hidden directory. You can't browse to it but you can type it in RUN or windows explorer location bar:

[ccNe_DOS]
%APPDATA%MicrosoftWindowsRecentAutomaticDestinations
[/ccNe_DOS]

You will see there a bunch of files with long weird names. You can either search trough them to find the one you want to delete or simply do like I do: delete them all! Not just from time to time, but add a task in Windows Task Scheduler to remove them on shutdown.

 