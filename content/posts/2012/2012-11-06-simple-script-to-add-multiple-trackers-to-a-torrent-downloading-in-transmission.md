---
title: Simple script to add multiple trackers to a torrent downloading in transmission
author: silviu
type: post
date: 2012-11-06T20:29:30+00:00
url: /2012/11/06/simple-script-to-add-multiple-trackers-to-a-torrent-downloading-in-transmission/
categories:
  - old
tags:
  - script
  - temp_on
  - trackers
  - transmission

---
Sometime you might want to download some old or obscure distro that was once packaged as a torrent. But many times the tracker embeded in the torrent file has long been abandoned or it has no peers. But many other trackers might have cached your torrent and maybe those have seeds. So I wrote a quick and dirty script to get a list of online trackers from [transmission](http://www.transmissionbt.com/).
```bash
#!/bin/bash

TRANSMISSION_REMOTE='/usr/bin/transmission-remote'

# Below is a command that will generate a tracker
# list with one tracker per line
# i.e. cat /some/path/trackers.txt for a static list

LIVE_TRACKERS_LIST_CMD='curl -s www.trackon.org/api/live'

if [ $# -ne 1 ]; then
echo "This script expects one parameter - the tracker id"
echo "Use $TRANSMISSION_REMOTE -l to find it"
exit 1
fi

$LIVE_TRACKERS_LIST_CMD | while read TRACKER
do
echo "Adding $TRACKER"
$TRANSMISSION_REMOTE -t $1 -td $TRACKER
done
```
You simply run it passing as parameter the ID of the torrent you want updated. You can find the ID by running
 
```bash
transmission-remote -l
```

or maybe

```bash
transmission-remote -l | grep -i "name"
```