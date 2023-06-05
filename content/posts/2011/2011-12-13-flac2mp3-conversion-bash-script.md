---
title: flac2mp3 conversion bash script
author: silviu
type: post
date: 2011-12-13T18:40:42+00:00
url: /2011/12/13/flac2mp3-conversion-bash-script/
dsq_thread_id:
  - 503335548
categories:
  - old
tags:
  - bash
  - conversion
  - convert
  - flac
  - flac2mp3
  - mp3
  - temp_on

---
I recently started buying some music in flac format. Though I'm content on storing it as flac on my NAS I don't like filling up my phone's memory and also I have the impression that listening to flac uses more battery on my n900.

So I devised a small script that converts all the flac's from a folder to mp3. It has some provisions to carry the metadata from one format to the other. It's based on the one found [here][1], with the following modifications:

  * it encodes as 320kbps stereo (not joint stereo) There's a whole debate on whether one can hear or not the quality improvement but it's still less than half the original flac file so I didn't really care on finding out if I could go lower. Changing the [lame][2] parameters is easy enough if you want different output settings
  * instead of id3 it uses id3tag as it's more current.
  * Dependencies: metaflac, id3tag, [lame][2] (use your distro's package manager to find out which packages provide those binaries)

 

[cce_bash]  
#!/bin/bash  
for a in *.flac

do  
OUTF=\`echo "$a" | sed s/.flac$/.mp3/g\`

ARTIST=\`metaflac "$a" -show-tag=ARTIST | sed s/.*=//g\`  
TITLE=\`metaflac "$a" -show-tag=TITLE | sed s/.*=//g\`  
ALBUM=\`metaflac "$a" -show-tag=ALBUM | sed s/.*=//g\`  
GENRE=\`metaflac "$a" -show-tag=GENRE | sed s/.*=//g\`  
TRACKNUMBER=\`metaflac "$a" -show-tag=TRACKNUMBER | sed s/.*=//g\`  
DATE=\`metaflac "$a" -show-tag=DATE | sed s/.*=//g\`

flac -c -d "$a" | lame -m s -b 320 -s 44.1 - "$OUTF"  
id3tag -s"$TITLE" -t"${TRACKNUMBER:-0}" -a"$ARTIST" -A"$ALBUM" -y"$DATE" -g"${GENRE:-12}" "$OUTF"

done  
[/cce_bash]

 [1]: https://wiki.archlinux.org/index.php/Convert_Flac_to_Mp3
 [2]: http://manpages.sgvulcan.com/lame.1.php