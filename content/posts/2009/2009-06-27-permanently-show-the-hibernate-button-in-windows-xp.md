---
title: Permanently show the Hibernate button in Windows XP
author: silviu
type: post
date: 2009-06-27T13:38:03+00:00
excerpt: Easy way to always have a hibernate button when shutting windows xp down. Just a quick registry hack and you are set !
url: /2009/06/27/permanently-show-the-hibernate-button-in-windows-xp/
dsq_thread_id:
  - 48858383
categories:
  - old
tags:
  - hibernate
  - temp_on

---
_**You like to hibernate your Windows system instead of always turning it off?**_ Me too! You still have to reboot or power off from time to time otherwise the system would slow down but at least sometimes you don't have to wait for the lengthy Windows boot.

<p style="text-align: center">
  <img decoding="async" loading="lazy" class="aligncenter size-full wp-image-526" title="The Hibernate Button" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/06/hibernat_button.jpg" alt="The Hibernate Button" width="398" height="198" />This is how you can configure Windows XP to always show the Hibernate button when clicking Turn Off like it shows on some laptops.
</p>

In windows XP, after you activate hibernation from Desktop->Properties->Screensaver -> Power (the logical place for it to be, right?) the only way to show the Hibernate button is to hold Shift while the **Turn off** menu is on. While shift is down Stand by becomes Hibernate.

Well another way is to add in:

[HKEY\_LOCAL\_MACHINESOFTWAREPoliciesMicrosoftWindowsSystemShutdown]

A value named:

"ShowHibernateButton"=dword:00000001

Easy. The Shutdown key may not be there so create that as well.

**If you don't like to edit your registry by hand you can download and execute this .reg file to make the changes automatically:  [hibernate.reg][1]**

 [1]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/06/hibernate.reg