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
I recently started buying some music in flac format. Though I&#8217;m content on storing it as flac on my NAS I don&#8217;t like filling up my phone&#8217;s memory and also I have the impression that listening to flac uses more battery on my n900.

So I devised a small script that converts all the flac&#8217;s from a folder to mp3. It has some provisions to carry the metadata from one format to the other. It&#8217;s based on the one found [here][1], with the following modifications:

  * it encodes as 320kbps stereo (not joint stereo) There&#8217;s a whole debate on whether one can hear or not the quality improvement but it&#8217;s still less than half the original flac file so I didn&#8217;t really care on finding out if I could go lower. Changing the [lame][2] parameters is easy enough if you want different output settings
  * instead of id3 it uses id3tag as it&#8217;s more current.
  * Dependencies: metaflac, id3tag, [lame][2] (use your distro&#8217;s package manager to find out which packages provide those binaries)

&nbsp;

[cce_bash]  
#!/bin/bash  
for a in *.flac

do  
OUTF=\`echo &#8220;$a&#8221; | sed s/.flac$/.mp3/g\`

ARTIST=\`metaflac &#8220;$a&#8221; &#8211;show-tag=ARTIST | sed s/.*=//g\`  
TITLE=\`metaflac &#8220;$a&#8221; &#8211;show-tag=TITLE | sed s/.*=//g\`  
ALBUM=\`metaflac &#8220;$a&#8221; &#8211;show-tag=ALBUM | sed s/.*=//g\`  
GENRE=\`metaflac &#8220;$a&#8221; &#8211;show-tag=GENRE | sed s/.*=//g\`  
TRACKNUMBER=\`metaflac &#8220;$a&#8221; &#8211;show-tag=TRACKNUMBER | sed s/.*=//g\`  
DATE=\`metaflac &#8220;$a&#8221; &#8211;show-tag=DATE | sed s/.*=//g\`

flac -c -d &#8220;$a&#8221; | lame -m s -b 320 -s 44.1 &#8211; &#8220;$OUTF&#8221;  
id3tag -s&#8221;$TITLE&#8221; -t&#8221;${TRACKNUMBER:-0}&#8221; -a&#8221;$ARTIST&#8221; -A&#8221;$ALBUM&#8221; -y&#8221;$DATE&#8221; -g&#8221;${GENRE:-12}&#8221; &#8220;$OUTF&#8221;

done  
[/cce_bash]

 [1]: https://wiki.archlinux.org/index.php/Convert_Flac_to_Mp3
 [2]: http://manpages.sgvulcan.com/lame.1.php