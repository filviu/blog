---
title: Dia crashes with latest updates in slacware-current
author: silviu
type: post
date: 2013-05-30T09:58:02+00:00
url: /2013/05/30/dia-crashes-with-latest-updates-in-slacware-current/
dsq_thread_id:
  - 1338477414
categories:
  - old
tags:
  - crash
  - current
  - dia
  - fix
  - segmentation fault
  - slacware
  - temp_on

---
Having just updated to the latest set of slackware current packages I found that the trusty old Dia would segfault:

[cce_bash]

\*\* (dia:26707): CRITICAL \*\*: dia\_renderer\_set_size: assertion \`irenderer != NULL&#8217; failed  
Segmentation fault

[/cce_bash]

With Ubuntu to the rescue 🙂 according to [this report][1] I found the fix to be:

Edit $(HOME)/.dia/persistence and change the value from **false** to **true**.

[cce_xml]

<p id="yui_3_9_1_1_1369907323211_378">
    <dia:boolean role=&#8221;view_antialised&#8221;><br /> <dia:attribute name=&#8221;booleanvalue&#8221;><br /> <dia:boolean val=&#8221;true&#8221;/><br /> </dia:attribute><br /> </dia:boolean>
</p>

[/cce_xml]

Please note that this fix works only if $(HOME)/.dia/persistence already exists. What this does (from the bug report):

> i.e. make the antialiased rendering default. And please don&#8217;t use the  
> View/AntiAliased menu item to toggle the renderer later, because that would  
> trigger the crash again.

 [1]: https://bugs.launchpad.net/ubuntu/+source/dia/+bug/1102960