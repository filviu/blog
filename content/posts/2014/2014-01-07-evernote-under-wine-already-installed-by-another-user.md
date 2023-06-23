---
title: 'Evernote under Wine: "already installed by another user."'
author: silviu
type: post
date: 2014-01-07T12:34:01+00:00
url: /2014/01/07/evernote-under-wine-already-installed-by-another-user/
dsq_thread_id:
  - 2101287396
categories:
  - old
tags:
  - evernote
  - temp_on
  - update
  - wine

---
Trying to update to the latest evernote version on a linux laptop I use I hit the error mentioned in the title: **"evernote was already installed by another user."**

Weird, but solvable. I ended doing the following:

Uninstall evernote:

```bash
wine uninstaller
```

Trying to install still gave the same error and so I had to do some registry surgery (be sure to replace **root** with your username):

```bash
grep "with upgrade" ~/.wine/drive_c/users/root/Temp/EvernoteSetup.log
[01/07/2014 14:23:18] Located product {C2EECB42-2C7F-11E3-8960-00163E98E7D0} with upgrade code {AE2C091E-CF5F-4e30-8659-D640E23A8B99}.
```
The first set of digits (they will be different in your case!) is of interest, in my case **C2EECB42**; reverse those digits and remove any entry from the registry that contains them (exporting them before removing is a good idea)

```bash
wine regedit
```

CTRL+F and search for 24BCEE2C, remove the entry. Now you can install the new version.