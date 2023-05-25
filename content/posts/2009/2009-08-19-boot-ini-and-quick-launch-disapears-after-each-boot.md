---
title: Boot.ini and Quick Launch disapears after each boot
author: silviu
type: post
date: 2009-08-19T13:14:38+00:00
url: /2009/08/19/boot-ini-and-quick-launch-disapears-after-each-boot/
dsq_thread_id:
  - 48858462
categories:
  - old
tags:
  - boot.ini
  - disappears
  - internet explorer
  - quick launch
  - temp_on

---
So, Microsoft took care of another hour of my life I&#8217;ll never see again&#8230;

**The problem:**

On a computer, after each boot the files c:boot.ini and the folder Internet Explorer from C:documents and settingsuserapplication datamicrosoftinternet explorer are **erased**. After fiddling with malware scanning, registry tweaks the problem was still there.

**The solution:**

I found someone on a forum noting that uninstalling Internet Explorer 8 fixed this problem for him. What? Ok, I understand that IE8 might screw around with the Quick Launch, but boot.ini? That&#8217;d be the day?

Well, to cut it short, uninstalling IE8 solved the problem. I bet that it&#8217;s not IE8, it was probably some update to IE8 that borked everything. Well, we agreed that IE8 should go all together, just to be sure.

So, it was not a virus after all, well, maybe just the virus called Windows.

So if you cannot create the Quick Launch toolbar, or if you create it&#8217;s folder and it goes away on every boot, simply go to control panel -> add remove programs, check _**show updates**_ and unintsall Internet Explorer 8. Do yourself a favour and install Firefox. Or Opera. Or Chrome. Or Safari. Heck even text mode lynx would be better and safer.

Well done Microsoft!