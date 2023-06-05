---
title: Freenas and Bittorent/transmission problems
author: silviu
type: post
date: 2009-06-01T17:40:52+00:00
excerpt: 'I ran into two problems with the Transmission BitTorrent client built into FreeNAS 0.69.1 and here you can find the solutions, both for the wrong file &amp; folder permissions and the downloads missing / forgotten between reboots.'
url: /2009/06/01/freenas-and-bittorenttransmission-problems/
code_editor:
  - |
    #!/bin/sh
    # filename:   perm_reset.sh
    # author:     Dan Merschi edited by evadman
    # date:       2008-10-24 original, edit 2008-10-28
    # purpose:    Reset permissions on torrent file and directory once
    #
    DIR=$(/usr/local/bin/xml sel -T -t -v "/freenas/bittorrent/downloaddir" /conf/config.xml)
    if   [ ! $(pgrep transmission) ]; then
     logger -p local5.info "Transmission not running"
    elif   [ ! -d "$DIR" ];then
     logger -p local5.info "Transmission download dir not set."
    else
     /usr/bin/find $DIR -type d ! -perm 777 -exec /bin/chmod 777 {} ;
     /usr/bin/find $DIR -type f ! -perm 666 -exec /bin/chmod 666 {} ;
    fi
code_type:
  - Cpp
dsq_thread_id:
  - 48858282
categories:
  - old
tags:
  - bittorrent
  - freenas
  - temp_on
  - transmission

---
As I mentioned in another post I run a <a href="http://www.freenas.org/" target="_blank" rel="noopener">FreeNAS </a>0.69.1(at the time of posting) based machine on my network, for backup, downloads and storage. I also use it to leave downloads running when I'm not at home. FreeNAS is great but I had this  problems when downloading torrents:

Yesterday I left it downloading the latest ubuntu version. (Yes I know I'm behind), it's been out for some time now. When I got back from town I just shut down the nas without checking on progress. Today, when I checked transmission the torrent was gone. The .iso was in the downloaded folder but it should have been seeding in transmision too. I also noticed that I cannot move the file from the place where it was downloaded. So two problems, two fixes:

  1. I didn't set the configuration folder for bittorent: Services -> BitTorrent -> Configuration directory, I assumed that it would use whatever the default is. Well, I set it to a folder on my shared drive, added some files rebooted and the downloads were still there, so one problem solved.
  2. The second was even easier as danmero & evadman offer a solution on the Freenas forums <a href="http://apps.sourceforge.net/phpbb/freenas/viewtopic.php?f=12&t=18" target="_blank" rel="noopener">here</a>. The file & folder rights of downloaded files are insufficient, so I just added the following into cron (System -> Advanced -> Cron):

[ccNe_bash]  
#!/bin/sh  
\# filename:   perm_reset.sh  
\# author:     Dan Merschi edited by evadman  
\# date:       2008-10-24 original, edit 2008-10-28  
\# purpose:    Reset permissions on torrent file and directory once  
#  
DIR=$(/usr/local/bin/xml sel -T -t -v "/freenas/bittorrent/downloaddir" /conf/config.xml)  
if   [ ! $(pgrep transmission) ]; then  
logger -p local5.info "Transmission not running"  
elif   [ ! -d "$DIR" ];then  
logger -p local5.info "Transmission download dir not set."  
else  
/usr/bin/find $DIR -type d ! -perm 777 -exec /bin/chmod 777 {} ;  
/usr/bin/find $DIR -type f ! -perm 666 -exec /bin/chmod 666 {} ;  
fi  
[/ccNe_bash]  
Done, I can now move and delete files from the downloads folder.