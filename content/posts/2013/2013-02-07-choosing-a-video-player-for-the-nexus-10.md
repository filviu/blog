---
title: Choosing a video player for the Nexus 10
author: silviu
type: post
date: 2013-02-07T12:12:24+00:00
url: /2013/02/07/choosing-a-video-player-for-the-nexus-10/
dsq_thread_id:
  - 1070243042
categories:
  - old
tags:
  - 10
  - andoid
  - comparison
  - nexus
  - player
  - roundup
  - table
  - temp_on
  - video

---
<!-- @page { margin: 0.79in } 		P { margin-bottom: 0.08in } -->So, I made the leap and I bought a tablet, a Google Nexus 10 to be more precise. Up until now I used vPlayer and the default video player on my Android Phone (galaxy S2) but on the tablet the default video player is very poor (or let&#8217;s say simple) and vPlayer showed some weird artifacts, so to the search it is. I choose from other roundups and recommandations the following:

  * [BsPlayer FREE][1]
  * [DICE Player][2]
  * [MoboPlayer][3]
  * [MX Player][4]
  * [VLC Beta][5]
  * [vPlayer][6]

All those players offer a nice, clean interface with similar basic functionality: resume position, some offer network playback, but not all video formats play the same in all players.

I collected a few files reflecting more than anything my usage, this might not necessarily reflect yours.

**Video samples:**

  * Lower quality avi/divx clip
  * ISO image of a DVD
  * Standard def MP4 (H264)
  * 1080p mkv clip
  * 1440p mkv clip (the 2560&#215;1440 version of [timescapes][7])

**[<img decoding="async" loading="lazy" class="alignright" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2013/02/bsplayer_free.png" alt="bsplayer_free" width="300" height="187" />][8]BsPlayer FREE**

_**Interface**_: A nice feature is that it searches and downloads subtitles automatically. You can swipe the screen for volume, brightness and seek control.

In order to make HW decoding possible on the nexus 10 I had to select **Preferences->playback preferences ->Use alternate HW decoding mode.**

It also offers a LAN mode that allows playing from SMB shares.

  * avi only plays in SW mode
  * ISO worked (somewhat) in SW mode, had to use **Open With **from Ghost Commander to load the .iso file. It goes linearly trough warnings, menu and starts the movie in SW mode
  * SD mp4 file works fine
  * 1080p mkv plays fine in HW mode
  * 1440p mkv plays ok with no dropped frames

Worth noting that it ignores silent settings.

&nbsp;

**[<img decoding="async" loading="lazy" class="alignright" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2013/02/dice_player.png" alt="dice_player" width="300" height="187" />][9]DICE Player**

Same simple interface you find in all these players. A good network options selection:smb, ftp and http network play

  * avi worked only in sw mode once. Crashed every time after that
  * ISO worked (somewhat) in SW mode, had to use **Open With **from Ghost Commander to load the .iso file. It goes linearly trough warnings, menu and starts the movie in SW mode
  * SD mp4 file works fine in HW mode
  * 1080p mkv plays fine in HW mode but the seek is choppy
  * 1440p crashes on load

&nbsp;

**[<img decoding="async" loading="lazy" class="alignright" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2013/02/mobo_player.png" alt="mobo_player" width="300" height="187" />][10]MoboPlayer**

Mobo offers a nice shinny interface with www, http and rtsp network play. As a downside the seek is not _live_ &#8211; i.e. while you drag the clip stays at the previous position until you release it.

  * avi did not start
  * iso plays black 15s of black image and then stops
  * SD mp4 works ok
  * 1080p mkv worked fine
  * 1440p switched to SW mode and dropped frames, it was unwatchable

&nbsp;

**[<img decoding="async" loading="lazy" class="alignright" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2013/02/mx_player.png" alt="mx_player" width="300" height="187" />][11]MX Player**

Has the same interface as all the other players but offers some interesting options &#8211; for example you can choose wether to use the HW decoder or not depending on video type and source (local/net/10bit)

It plays network streams (offers http as an example but others might be supported)

Worth noting is that it shows ads while the video is paused.

  * avi works fine SW mode
  * ISO worked (somewhat) in SW mode, had to use **Open With **from Ghost Commander to load the .iso file. It goes linearly trough warnings, menu and starts the movie in SW mode
  * SD mp4 played fine in HW mode
  * 1080p mkv works fine in HW mode
  * 1440p plays ok in HW mode

A weird thing was that videos started in SW mode even if they worked fine after I selected HW mode (yes HW mode was set in settings).

Worth noting that seek was smooth even for the 1440p clip

&nbsp;

**[<img decoding="async" loading="lazy" class="alignright" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2013/02/vlc.png" alt="vlc" width="300" height="187" />][12]VLC Beta**

Again the same simple interface as the others, with a nice touch with the left auto-hiding menu.

Offers over the network play for at least http, mms, rtsp streams.

  * avi works if HW is deselected &#8211; this means SW decoder is not automatically selected if the HW one fails
  * iso DVD is shown in the list and works (again linear, with a wrong aspect ratio)
  * SD mp4 works fine
  * 1080p mkv doesn’t start
  * 1440p mp4 doesn’t start

Again the seek is static, the video keeps playing until you release the seek bar.

&nbsp;

**[<img decoding="async" loading="lazy" class="alignright" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2013/02/vplayer.png" alt="vplayer" width="300" height="187" />][13]Vplayer**

Yet once more the file list interface but it does offer a streams tab and a library tab. A big disadvantage is that there is no auto switching between SW and HW playback mode and so if a video doesn&#8217;t play you must try to switch them. Fortunately you can do it without exiting the video.

  * avi works in SW mode
  * ISO does not start
  * SD mp4 works but shows strange banding just like color gradients on the wrong diplay color depth
  * 1080p mkv blocks on seek, same banding issues, drops frames
  * 1440p mp4 same banding (screenshot), drops lots of frames

It plays network streams with bookmarks &#8211; but you have to add one in order to play a clip. And it has a very good uPNP plugin that allows me to play media directly from my NAS server.

<figure style="width: 300px" class="wp-caption alignright">[<img decoding="async" loading="lazy" title="vPlayer banding" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2013/02/vplayer_banding.png" alt="vPlayer banding" width="300" height="187" />][14]<figcaption class="wp-caption-text">vPlayer banding</figcaption></figure>

_More about the banding issue:_ this is actually the reason I started looking for an alternative player. I have used vPlayer for more than a year now on my phone, and I actually bought the full version. When I got the nexus 10 tablet I noticed weird _banding_ (for lack of a better description, see the screenshot). First I thought that it&#8217;s because of the scale-up needed to make the SD clips I was watching fit the immense resolution of the tablet. Than I noticed that even the 1440p Timescapes video shows the same. It looks like a gradient on a low color-depth screen. I knew the N10 has a lower saturation than other displays but still this was too much. So I tried the default video player (with the few files it supports) and noticed that there the problem is nonexistent hence the need for a new player.

## Comparison Table

<table>
  <tr>
    <td>
    </td>
    
    <td>
      AVI Sample
    </td>
    
    <td>
      ISO dvd copy
    </td>
    
    <td>
      SD mp4 file
    </td>
    
    <td>
      1080p mkv file
    </td>
    
    <td>
      1440p mp4 file
    </td>
  </tr>
  
  <tr>
    <td>
      <a href="https://play.google.com/store/apps/details?id=com.bsplayer.bspandroid.free">BsPlayer FREE</a>
    </td>
    
    <td>
      SW
    </td>
    
    <td>
      SW<sup>*</sup>
    </td>
    
    <td>
      HW
    </td>
    
    <td>
      HW
    </td>
    
    <td>
      HW
    </td>
  </tr>
  
  <tr>
    <td>
      <a href="https://play.google.com/store/apps/details?id=com.inisoft.mediaplayer.a">DICE Player</a>
    </td>
    
    <td>
      SW<sup>1</sup>
    </td>
    
    <td>
      SW<sup>*</sup>
    </td>
    
    <td>
      HW
    </td>
    
    <td>
      HW
    </td>
    
    <td>
      crash
    </td>
  </tr>
  
  <tr>
    <td>
      <a href="https://play.google.com/store/apps/details?id=com.clov4r.android.nil">MoboPlayer</a>
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      HW
    </td>
    
    <td>
      HW
    </td>
    
    <td>
      SW, drops frames
    </td>
  </tr>
  
  <tr>
    <td>
      <a href="https://play.google.com/store/apps/details?id=com.mxtech.videoplayer.ad">MX Player</a>
    </td>
    
    <td>
      SW
    </td>
    
    <td>
      SW<sup>*</sup>
    </td>
    
    <td>
      HW
    </td>
    
    <td>
      HW
    </td>
    
    <td>
      HW
    </td>
  </tr>
  
  <tr>
    <td>
      <a href="https://play.google.com/store/apps/details?id=org.videolan.vlc.betav7neon">VLC Beta</a>
    </td>
    
    <td>
      manual SW
    </td>
    
    <td>
      SW<sup>2</sup>
    </td>
    
    <td>
      HW
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      &#8211;
    </td>
  </tr>
  
  <tr>
    <td>
      <a href="https://play.google.com/store/apps/details?id=me.abitno.vplayer.t">vPlayer</a>
    </td>
    
    <td>
      SW
    </td>
    
    <td>
      &#8211;
    </td>
    
    <td>
      HW<sup>**</sup>
    </td>
    
    <td>
      HW<sup>3,**</sup>
    </td>
    
    <td>
      HW drops frames
    </td>
  </tr>
</table>

* had to use &#8220;Open With&#8221; from Ghost Commander, plays linearly including warnings and menu

** shows ugly banding

1 &#8211; played once, after that it crashed every time on load

2 &#8211; wrong aspect ratio but shows in the file list

3 &#8211; ugly artifact blocks after seeking, persisting ~5 seconds

## Conclusion

Let&#8217;s start with the disappointments.

[BsPlayer FREE][1] &#8211; Here my disappointment is that it worked pretty good. I secretly wanted it to fail because I dislike it from the time they started to add spyware to the free PC version. I know, they probably got over that phase but I cannot trust someone who once could justify that decision to themselves. It was unstable at times and it doesn&#8217;t obey volume settings.

[DICE Player][2] &#8211; I read a few articles noting it as a good player. Unfortunately with my selection not so much. The avi file loaded once but crashed each time after that and the 1440p crashed the app as well.

[MoboPlayer][3] &#8211; this one proved to be another disappointment as I read (lifehacker I think) that it&#8217;s one of the best around. Well in my selection it was one of the worst.

[MX Player][4] &#8211; I know MX since it was one of the few that supported multicore decoding and HW decoding on the than new Galaxy Tab 10.1 my wife uses. She got used to it and never felt the need to change it with something new. It played everything I tried and also had the best seek (I know, subjective) I didn&#8217;t like the ads shown while pausing.

[VLC Beta][5] &#8211; this was by far the biggest disappointment. Once I saw it I thought the search was over, as I use vlc on the desktop (both windows and linux) and it works great. Here on the other hand it was the absolute worst.

[vPlayer][6] &#8211; It&#8217;s still the good player I decided to pay for on my phone. Unfortunately the banding issue makes it very annoying to use.

**What gets uninstalled**: BsPlayer (because I&#8217;m not over their spyware crap), DICE because it crashes, MoboPlayer because it desn&#8217;t play everything I need it to.

**What I keep**: VLC to see if new versions will bring it to the same level of usability of the desktop app. MX Player because it plays everything I need (and it does it very good) and vPlayer because hopefully an upgrade will fix the banding issue.

 [1]: https://play.google.com/store/apps/details?id=com.bsplayer.bspandroid.free
 [2]: https://play.google.com/store/apps/details?id=com.inisoft.mediaplayer.a
 [3]: https://play.google.com/store/apps/details?id=com.clov4r.android.nil
 [4]: https://play.google.com/store/apps/details?id=com.mxtech.videoplayer.ad
 [5]: https://play.google.com/store/apps/details?id=org.videolan.vlc.betav7neon
 [6]: https://play.google.com/store/apps/details?id=me.abitno.vplayer.t
 [7]: http://timescapes.org/products/Default.aspx
 [8]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2013/02/bsplayer_free.png
 [9]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2013/02/dice_player.png
 [10]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2013/02/mobo_player.png
 [11]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2013/02/mx_player.png
 [12]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2013/02/vlc.png
 [13]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2013/02/vplayer.png
 [14]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2013/02/vplayer_banding.png