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

```bash
\*\* (dia:26707): CRITICAL \*\*: dia_renderer_set_size: assertion \`irenderer != NULL' failed
Segmentation fault
```

With Ubuntu to the rescue 🙂 according to [this report][1] I found the fix to be:

Edit $(HOME)/.dia/persistence and change the value from **false** to **true**.

[cce_xml]

<p id="yui_3_9_1_1_1369907323211_378">
    <dia:boolean role="view_antialised"><br /> <dia:attribute name="booleanvalue"><br /> <dia:boolean val="true"/><br /> </dia:attribute><br /> </dia:boolean>
</p>

[/cce_xml]

Please note that this fix works only if $(HOME)/.dia/persistence already exists. What this does (from the bug report):

> i.e. make the antialiased rendering default. And please don't use the
> View/AntiAliased menu item to toggle the renderer later, because that would
> trigger the crash again.

 [1]: https://bugs.launchpad.net/ubuntu/+source/dia/+bug/1102960