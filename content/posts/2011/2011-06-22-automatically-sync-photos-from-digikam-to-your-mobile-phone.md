---
title: Automatically sync photos from digikam to your mobile phone
author: silviu
type: post
date: 2011-06-22T08:10:02+00:00
url: /2011/06/22/automatically-sync-photos-from-digikam-to-your-mobile-phone/
dsq_thread_id:
  - 339149371
categories:
  - old
tags:
  - bash
  - digikam
  - images
  - mysql
  - n900
  - script
  - sync
  - temp_on
  - wireless

---
<img decoding="async" loading="lazy" class="alignleft size-thumbnail wp-image-1513" title="digikam_logo" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2011/06/digikam_logo-150x150.png" alt="" width="150" height="150" />I shoot a lot of pictures. My collection keeps growing (for example ~90 Gb right now) and since last year I discovered the joy of using <a href="http://www.digikam.org/" target="_blank" rel="noopener">digikam</a> to tag and organize them. I&#8217;m using the beta 2.0.0 version and use mysql to store it&#8217;s databases (as opposed to the default sqlite) as it&#8217;s easier to interact and backup. What I want is to carry some of those pictures with me, specifically on my phone. I used to simply resize and copy files by hand but that means that I never have the latest pictures on my phone. So I devised a script that automatically resizes and syncs pictures to my phone. This is it:

[cce_bash]  
#!/bin/bash

\# your digikam database, user and password  
DB=&#8221;digikam&#8221;  
DBPASS=&#8221;password&#8221;  
DBUSR=&#8221;user&#8221;

SQL=&#8221;SELECT Albums.relativePath,&#8221;#&#8221;,Images.name FROM \`Albums\`,\`Images\`,\`ImageTags\` WHERE ImageTags.tagid=20 and Images.id=ImageTags.imageid and Albums.id=Images.album&#8221;

SRC=&#8221;/data/foto&#8221;  
DST=&#8221;/data/n900-foto&#8221;

MOBILE=&#8221;192.168.1.100:/home/user/MyDocs/foto&#8221;

while read IMG; do  
ALBUM=\`echo $IMG | awk &#8216;BEGIN { FS = &#8220;#&#8221; } ; { print $1 }&#8217; | awk &#8216;{sub(/[ t]+$/, &#8220;&#8221;);print}&#8217; | sed -e &#8216;s/^[ t]*//&#8217;\`  
IMAGE=\`echo $IMG | awk &#8216;BEGIN { FS = &#8220;#&#8221; } ; { print $2 }&#8217; | awk &#8216;{sub(/[ t]+$/, &#8220;&#8221;);print}&#8217; | sed -e &#8216;s/^[ t]*//&#8217;\`  
mkdir -p &#8220;$DST$ALBUM&#8221;  
if [ ! -f &#8220;$DST$ALBUM/$IMAGE&#8221; ]; then  
echo &#8220;Resizing $IMAGE and copying to $DST$ALBUM&#8221;  
convert &#8220;$SRC$ALBUM/$IMAGE&#8221; -resize &#8220;1600&#215;1600&#8221; &#8220;$DST$ALBUM/$IMAGE&#8221;  
fi  
done < <(mysql &#8211;skip-column-names -u$DBUSR -p$DBPASS $DB -e &#8220;$SQL&#8221;)  
echo &#8220;Syncing to the phone&#8230;&#8221;  
rsync -rv &#8211;delete $DST $MOBILE/  
[/cce_bash]  
Simple enough. Let&#8217;s go trough it:

Since I use a Nokia N900 I can have the pictures rsynced via ssh. Of course you can change the script to rsync to a standard folder (if you mount your phone using usb). The trick I use is to have a tag called &#8220;**mobile**&#8221; that I use to tag pictures I want synced to my phone. In my setup this tag has the ID 20 and that&#8217;s what the script searches for in the database. You can use a tool like phpmyadmin to find this id. Then the script uses Image Magick&#8217;s **convert** to proportionally resize the pictures to have the longside 1600 pixels. Since it checks first if the file already exists it only resizes new tagged files. It also maintains the folder structure of the original images &#8211; this way I will find them in the same folders on the phone as on the desktop. Lastly it rsyncs the files (in my case over ssh which is set up to use key based authentication).

Here&#8217;s a nice way to enjoy linux both at home and in your pocket 🙂