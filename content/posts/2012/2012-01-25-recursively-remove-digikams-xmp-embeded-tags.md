---
title: Recursively remove digikam’s xmp embeded tags
author: silviu
type: post
date: 2012-01-24T22:06:44+00:00
url: /2012/01/25/recursively-remove-digikams-xmp-embeded-tags/
dsq_thread_id:
  - 551435972
categories:
  - old
tags:
  - digikam
  - exiftool
  - sidecar
  - tags
  - temp_on
  - xmp

---
Because digikam made a mess of the tags I started to add to my pictures I decided to start from scratch. Note that I tried to get the max and I had set to write tags both to .xmp sidecar files and inside the image files. I also use the mysql backend.

One of the above broken everything (I started seeing _digikam_root_tag) and some of my tags were doubled. So all in all I wanted to delete them all:

  * Remove your collection from digikam
  * Drop all tables from the digikam database
  * Remove all .xmp files. In the folder containing your collection:
    find . -name *.xmp -exec rm {} ;
  * Remove all embedded xmp tags (again in the folder containing you collection)
    exiftool -r -P -xmp:TagsList= -xmp:LastKeywordXMP= -xmp:HierarchicalSubject= -xmp:Subject= -iptc:Keywords= *

**DON'T FOLLOW THIS BLINDLY**

This is just a sketch of the process. If you don't understand what are you doing don't do it! I also kept all .original files exiftool generated, just in case I discover something later on.

 