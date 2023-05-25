---
title: Working mediatomb config.xml for Samsung UE37C5000
author: silviu
type: post
date: 2011-09-13T14:11:47+00:00
url: /2011/09/13/working-mediatomb-config-xml-for-samsung-ue37c5000/
dsq_thread_id:
  - 413295480
categories:
  - old
tags:
  - led tv
  - linux
  - mediatomb
  - samsung
  - temp_on
  - ue37c5000

---
I have a NAS and an Samsung UE37C5000 UPNP/DLNA enabled led TV. Streaming from the first to the second should be easy, right? Well after a few tweaks MediaTomb makes it possible.

I don&#8217;t say this is the best configuration possible but it&#8217;s the one that works INCLUDING pause and fast forwarding.

Relevant from the default are the custom header, extended protocol info and the mkv and avi lines.

[cce_xml]

MediaTomb  
uuid:0f53d0ff-5951-4d27-8fa7-06ce378ae789  
/var/lib/mediatomb  
/usr/share/mediatomb/web

mediatomb.db

localhost  
mediatomb  
mediatomb

49152  
<!-- For PS3 support change to "yes" -->

  
<!--
       Uncomment the lines below to get rid of jerky avi playback on the
       DSM320 or to enable subtitles support on the DSM units
    -->

redsonic.com  
105

<!-- Uncomment the line below if you have a Telegent TG100 -->

  
<!&#8211;  
101  
&#8211;>

128  
5  
yes  
no  
8

<mark>  
*  
<mark>  
video  
</mark>  
</mark>

lastfmuser  
lastfmpass

/usr/share/mediatomb/js/common.js  
/usr/share/mediatomb/js/playlists.js

/usr/share/mediatomb/js/import.js

<map />

<map />

<map />

<map />

<map />

<map />

<map />

<map />

<map />

<map />

<map />

<map />

<map />

<map />

<map />

<map />

<map />

<map />

<map />

<map />

<!-- Uncomment the line below for PS3 divx support -->

  
<!&#8211; </p> 

<map />
&#8211;>
  
<!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 -->

  
<!&#8211; </p> 

<map />
&#8211;></p> 

<map />

<map />

<map />

audio/L16  
no  
yes  
no

video/mpeg  
yes  
yes  
yes

[/cce_xml]