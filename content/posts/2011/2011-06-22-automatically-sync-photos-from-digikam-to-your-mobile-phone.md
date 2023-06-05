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
<img decoding="async" loading="lazy" class="alignleft size-thumbnail wp-image-1513" title="digikam_logo" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2011/06/digikam_logo-150x150.png" alt="" width="150" height="150" />I shoot a lot of pictures. My collection keeps growing (for example ~90 Gb right now) and since last year I discovered the joy of using <a href="http://www.digikam.org/" target="_blank" rel="noopener">digikam</a> to tag and organize them. I'm using the beta 2.0.0 version and use mysql to store it's databases (as opposed to the default sqlite) as it's easier to interact and backup. What I want is to carry some of those pictures with me, specifically on my phone. I used to simply resize and copy files by hand but that means that I never have the latest pictures on my phone. So I devised a script that automatically resizes and syncs pictures to my phone. This is it:

[cce_bash]  
#!/bin/bash

\# your digikam database, user and password  
DB="digikam"  
DBPASS="password"  
DBUSR="user"

SQL="SELECT Albums.relativePath,"#",Images.name FROM \`Albums\`,\`Images\`,\`ImageTags\` WHERE ImageTags.tagid=20 and Images.id=ImageTags.imageid and Albums.id=Images.album"

SRC="/data/foto"  
DST="/data/n900-foto"

MOBILE="192.168.1.100:/home/user/MyDocs/foto"

while read IMG; do  
ALBUM=\`echo $IMG | awk 'BEGIN { FS = "#" } ; { print $1 }' | awk '{sub(/[ t]+$/, "");print}' | sed -e 's/^[ t]*//'\`  
IMAGE=\`echo $IMG | awk 'BEGIN { FS = "#" } ; { print $2 }' | awk '{sub(/[ t]+$/, "");print}' | sed -e 's/^[ t]*//'\`  
mkdir -p "$DST$ALBUM"  
if [ ! -f "$DST$ALBUM/$IMAGE" ]; then  
echo "Resizing $IMAGE and copying to $DST$ALBUM"  
convert "$SRC$ALBUM/$IMAGE" -resize "1600&#215;1600" "$DST$ALBUM/$IMAGE"  
fi  
done < <(mysql -skip-column-names -u$DBUSR -p$DBPASS $DB -e "$SQL")  
echo "Syncing to the phone&#8230;"  
rsync -rv -delete $DST $MOBILE/  
[/cce_bash]  
Simple enough. Let's go trough it:

Since I use a Nokia N900 I can have the pictures rsynced via ssh. Of course you can change the script to rsync to a standard folder (if you mount your phone using usb). The trick I use is to have a tag called "**mobile**" that I use to tag pictures I want synced to my phone. In my setup this tag has the ID 20 and that's what the script searches for in the database. You can use a tool like phpmyadmin to find this id. Then the script uses Image Magick's **convert** to proportionally resize the pictures to have the longside 1600 pixels. Since it checks first if the file already exists it only resizes new tagged files. It also maintains the folder structure of the original images - this way I will find them in the same folders on the phone as on the desktop. Lastly it rsyncs the files (in my case over ssh which is set up to use key based authentication).

Here's a nice way to enjoy linux both at home and in your pocket 🙂