---
title: No album cover art in Symbian ^3 Belle on an E7
author: silviu
type: post
date: 2012-07-13T08:31:25+00:00
url: /2012/07/13/no-album-cover-art-in-symbian-3-belle-on-an-e7/
categories:
  - tech
tags:
  - album art
  - belle
  - cover
  - e7
  - music
  - player

---
Sooo, my beloved n900 kicked the bucket and the fine folks at Nokia Romania decided it's not fixable and they replaced it. With an E7. After 6 weeks. Hey Nokia still wondering why you're going down the drain?

I have my music neatly organized and with cover art embeded inside the id3tag. But it won't show up. Actually it showed up for one album out of 15. So I started the hunt to see why. For tagging I use the excellent [EasyTAG](http://easytag.sourceforge.net/). 

**First suspect was Type. When you select Pictures to embed you can set the type. I set it to Cover (front)** A transfer and library refresh later I was happy to see that it still didn't work. I checked it for the album that had cover art displayed and it was set too to Cover (front) but the **Description:** field was empty. On the albums that showed no covers it was set to the original filename.

**So step 2 is to set Description: to empty.**

So the excellent Symbian coders who released a half baked music app ( you can't play an album if it has different artists for example) took the time to check for this damn filed and show nothing if it's filled. Really, really smart.

**Update:**
**Step 3**, if you already copied an album and just updated the tags and copied over the cover will not appear. You need to rename the album folder and rescan. You can rename it back and rescan again if you want.

The n900 will be probably the last in a long line of Nokia phones I bought.
