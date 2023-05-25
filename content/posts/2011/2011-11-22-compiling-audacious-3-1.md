---
title: Compiling audacious 3.1
author: silviu
type: post
date: 2011-11-22T09:18:26+00:00
url: /2011/11/22/compiling-audacious-3-1/
dsq_thread_id:
  - 480108899
categories:
  - old
tags:
  - audacious
  - audacious-plugins
  - compile
  - configure
  - make
  - make install
  - slackware
  - temp_on

---
I&#8217;m a big fan of classic media players (audacious, xmms, the old winamp, etc.) That&#8217;s why I wanted today to complile the latest version of <a href="http://audacious-media-player.org/" target="_blank" rel="noopener">audacious</a> (3.1) for my slackware laptop. Since the audacious build scripts are kind enough to provide make uninstall I didn&#8217;t bother with package builds, I simply compiled the stock source.

BTW that required upgrading libmowgli  (got one from slacky). Audacious compiled succesfully but for audacious-plugins **configure** refused to run:  
[cce_bash]  
checking for AUDACIOUS&#8230; no  
configure: error: Cannot find Audacious 3.1; have you installed Audacious yet?</pre> 

[/cce_bash]  
That was strange as I just finished compiling and installing audacious. I double checked and it was installed, binary in /usr/local/bin

I tried to run audacious and got:  
[cce_bash]  
bash-4.1# ./audacious  
WARNING: Audacious seems to be already running but is not responding.  
FATAL: No output plugin found.  
[/cce_bash]  
The warning was strange, there was no stale process. I checked ~/.config/audacious and found a **lock** file. **Removing that allowed configure to proceed.**

_**Update:**_ Spoke (blogged) to soon. I was in the wrong folder and I though it worked but it didn&#8217;t. This was actually needed since I was installing in /usr/local (run prior to configure)  
[cce_bash]  
export PKG\_CONFIG\_PATH=/usr/local/lib/pkgconfig:$PKG\_CONFIG\_PATH  
LD\_LIBRARY\_PATH=/usr/local/lib:$LD\_LIBRARY\_PATH</pre> 

[/cce_bash]  
&nbsp;