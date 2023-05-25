---
title: Simple script to add multiple trackers to a torrent downloading in transmission
author: silviu
type: post
date: 2012-11-06T20:29:30+00:00
url: /2012/11/06/simple-script-to-add-multiple-trackers-to-a-torrent-downloading-in-transmission/
dsq_thread_id:
  - 916440991
categories:
  - old
tags:
  - script
  - temp_on
  - trackers
  - transmission

---
Sometime you might want to download some old or obscure distro that was once packaged as a torrent. But many times the tracker embeded in the torrent file has long been abandoned or it has no peers. But many other trackers might have cached your torrent and maybe those have seeds. So I wrote a quick and dirty script to get a list of online trackers from <a href="http://www.trackon.org/" target="_blank" rel="noopener">trackon.org</a> and add them to a torrent you have downloading inside <a href="http://www.transmissionbt.com/" target="_blank" rel="noopener">transmission</a>.  
[cc_bash]  
#!/bin/bash

TRANSMISSION_REMOTE=&#8217;/usr/bin/transmission-remote&#8217;

\# Below is a command that will generate a tracker  
\# list with one tracker per line  
\# i.e. cat /some/path/trackers.txt for a static list

LIVE\_TRACKERS\_LIST_CMD=&#8217;curl -s www.trackon.org/api/live&#8217;

if [ $# -ne 1 ]; then  
echo &#8220;This script expects one parameter &#8211; the tracker id&#8221;  
echo &#8220;Use $TRANSMISSION_REMOTE -l to find it&#8221;  
exit 1  
fi

$LIVE\_TRACKERS\_LIST_CMD | while read TRACKER  
do  
echo &#8220;Adding $TRACKER&#8221;  
$TRANSMISSION_REMOTE -t $1 -td $TRACKER  
done  
[/cc_bash]  
You simply run it passing as parameter the ID of the torrent you want updated. You can find the ID by running  
[cci\_bash]transmission-remote -l[/cci\_bash]  
or maybe  
[cci\_bash]transmission-remote -l | grep -i &#8220;name&#8221;[/cci\_bash]