---
title: 'I have a linux Jukebox ! [2011 update]'
author: silviu
type: post
date: 2009-08-26T19:30:04+00:00
url: /2009/08/26/i-have-a-linux-jukebox/
dsq_thread_id:
  - 48858468
categories:
  - old
tags:
  - blaupunkt
  - esekeyd
  - jukebox
  - lcd-stuff
  - lcdproc
  - linux
  - mpc
  - mpd
  - numpad
  - temp_on
  - usb

---
Finally, after years of putting it away, after a few design changes and a fried motherboard I have a linux jukebox. Well, not a jukebox but more an internet radio.

**Check at the bottom for the latest updates.**

<figure id="attachment_463" aria-describedby="caption-attachment-463" style="width: 300px" class="wp-caption aligncenter">[<img decoding="async" loading="lazy" class="size-medium wp-image-463" title="Linux Webradio" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/08/IMG_9095_i-300x200.jpg" alt="Linux Webradio" width="300" height="200" />][1]<figcaption id="caption-attachment-463" class="wp-caption-text">Linux internet radio inside a vintage Blaupunkt radio case</figcaption></figure>

When I first had the ideea I noticed an old ~ '50s Blaupunkt Radio my father had in his basement. I investigated if the radio was worth restoring but the inside was rusted, the capacitors were long gone and most of the tubes were missing. It was more a case of rebuilding rather than restoring. I checked around the internet and saw that many models like this one existed, so it was not rare. And so, the radio was gutted and the insides went away. I cleaned and repaired the case as best as I could.

The first ideea was to have a big harddrive inside, an amp and external speakers hooked to it. It worked like this for a while until the motherboard I used fried and so did the amp. The project was eventualy put aside.

Anyways recently, I aquired an old Pentium III Compaq. By the case I could swear it was a small motherboard. It was NOT, and also the custom compaq psu had very short wires, but I managed to fit it inside. Since I have a media center pc hooked to the tv and the surround with all the music on it I decided to change the original ideea and make it what it originally was: a radio.

So, I gutted an old set of very good sounding Altec Lansing computer speakers and installed the small amp and speakers inside. I also mounted the motherboard and psu inside. One small fan on a side does the job of cooling everything down. I use one of the buttons on the front for the amp and another one for the computer.

I gave up the harddrive from the original design for a compact flash <-> ide adapter and the system now boots from a 4 Gb compact flash card. I think I could have squeezed everything on a smaller card but I decided to do all the compiling in place and since cards are cheap I went for a big one. The adapter has space for a second card and, if I want I can fit a second, bigger card, to hold some music.

I have a usb numpad for control and the [usb lcd display][2] featured some time ago on this site for display.

Software:

  * <a href="http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki" target="_blank" rel="noopener">mpd</a> for playback
  * <a href="http://mpd.wikia.com/wiki/Client:Mpc" target="_blank" rel="noopener">mpc</a> for mpd control
  * <a href="http://lcdproc.omnipotent.net/" target="_blank" rel="noopener">Lcdproc</a> and [lcd-stuff][3] for usb lcd display
  * <a href="http://www.burghardt.pl/tag/keyboard/" target="_blank" rel="noopener">esekeyd</a> for numpad control
  * a bunch of bash scripts to glue everything in place

I hit a few problems:

  * Event Music Player Client daemon does not work, at least with my keypad. So I had to use an external daemon - esekeyd with mpc to control mpd.
  * lcd-stuff does not display the Name tag (that would be the radio station name, just the artist and track name. Fortunately it has a configuration tag to use as a title for the screen - on every playlist change a bashscript modifies that configuration setting to reflect the radio station's name and reloads lcd-stuff - it's ugly but it works.
  * I didn't find a way to save .pls and .m3u files and have them recognized by the mpd database. So a script is called at boot time (and also can be started from one of the keys on the keypad) to generate a playlist of the radio stations. Control is easy after that, it's a matter of play/stop, next / prev
  * I wanted to have a way to shut down the system safely from the keypad. OTOH I didn't want shutting down every time I hit the wrong key. But esekeyd doesn't support combinations. So I had ***** create a file, **/** create a second one but only if the first file (created by *) existed and on backspace press verify if the two files exist and if yes poweroff.

I'll post soon more photos, the insides and the configuration files and bash scripts used.

**2011 Update**

It never functioned reliably and so I decided on rebuilding it once more 🙂

  * The Compaq Deskpro EN was reassembled and donated to charity.
  * I bought the cheapest intel motherboard with an atom processor.
  * With the motherboard I also bought a small, slim PSU which happened to have the loudest annoying fan I ever heard. Fortunately the motherboard and disk use small amounts of power so no heat is produced. I hooked the fan to 5v and now it's quiet.
  * I got a good deal on a pair of Microlab powered speakers (were the last in stock, open box) so I hooked those up to the radio. It's still possible to use the insternal speakers but why would you want to 🙂
  * Used a 500Gb sata disk that I also had around.
  * Took the oportunity to update slackware, mpd and everything else to the latest versions.
  * Took out the LCD until I can find time to build it in a nice case
  * The usb numpad is still there but I'm having trouble finding a daemon that actually works between two reboots
  * I use Client175 for web control and also Sonata on n800 and DroidMPD on my wife's tablet to control it. Having 500Gb it's got it's music back (not only internet radio).
  * Since playlist support seems to be better now I have each radio stored in a playlist that DroidMPD or Client175 can simply load.
  * The best thing is that there are no custom hackish scripts left that could break all the time. It's just stock mpd, playlists and the clients. Oh, I also have the command line clients installed for when I ssh into it using my n900.
  * The only problematic thing left is the shitty usb wi-fi adapter I use (don't know, might be the drivers) it's slow and sometimes connection drops. I added **ping -c1 GATEWAY_IP** in cron every 2 minutes and this seems to help.

Somebody in the comments asked for the configurations and scripts  The original ones, from the compact flash should still be in backups somewhere but I don't see how they could help, as they point to old or discontinued versions.  (lcd-stuff comes to mind). The configuration I use now is as stock as one can get with mpd. Let me know if you have questions about it and also **_please_** recommend me a daemon that can listen for keystrokes from the usb keypad and it's stable.

Have fun.

#  <span id=":4g" class="hP">I have a linux Jukebox !</span> {.ha}

 [1]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/08/IMG_9095_i.jpg
 [2]: http://www.sgvulcan.com/4x20-lcd-screen-with-usb-interface/
 [3]: http://lcd-stuff.berlios.de/