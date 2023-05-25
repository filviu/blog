---
title: Remove the Thunar root warning
author: silviu
type: post
date: 2013-11-06T08:36:58+00:00
url: /2013/11/06/remove-the-thunar-root-warning/
dsq_thread_id:
  - 1941201952
categories:
  - old
tags:
  - root
  - slackware
  - temp_on
  - Thunar

---
[<img decoding="async" loading="lazy" class="alignright size-medium wp-image-2914" alt="thunar-warning" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2013/11/thunar-warning-300x199.png" width="300" height="199" />][1]I never understood a developer&#8217;s obsession with &#8220;their way&#8221; but anyways. Thunar is a good light file manager that has one issue, it insists on displaying a warning when being used as root that cannot be turned off. Well I run my personal laptop as root and I don&#8217;t really care what others think about it and why it might be a bad thing(TM).

In order to remove the damn warning you need to grab everything needed to rebuild the package from:

<http://mirrors.slackware.com/slackware/slackware-current/source/xfce/Thunar/> (32 bit) or <http://mirrors.slackware.com/slackware/slackware64-current/source/xfce/Thunar/> (64 bit)

After that download [this patch][2] to the same folder and replace the slackbuild with [this one][3].

**OR** simply clone [the git repo][4] and build there.

 [1]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2013/11/thunar-warning.png
 [2]: https://github.com/silviuvulcan/slackbuilds/raw/master/Thunar/no-root-warning.patch
 [3]: https://github.com/silviuvulcan/slackbuilds/raw/master/Thunar/Thunar.SlackBuild
 [4]: https://github.com/silviuvulcan/slackbuilds/