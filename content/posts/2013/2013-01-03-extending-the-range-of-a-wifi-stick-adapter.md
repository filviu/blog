---
title: Extending the range of a WiFi stick adapter
author: silviu
type: post
date: 2013-01-03T12:03:06+00:00
url: /2013/01/03/extending-the-range-of-a-wifi-stick-adapter/
dsq_thread_id:
  - 1005988048
categories:
  - old
tags:
  - adapter
  - antenna
  - extend
  - range
  - temp_on
  - usb
  - wireless

---
I relocated some of my networking gear and by doing that one of my pc's found itself in a blind spot of the wireless network. I decided to try and see if I can extend the range of the usb wireless adapter it uses. I had a few antennas available but unfortunately the usb adapter didn't have a connector. I decided to solder the antenna wire directly:

![WiFi Adapter PCB next to an antenna and it's plastic shell](/blog/images/2013/IMG_1764.jpg)

First I pried open the usb adapter and located the internal antenna pads. With this particular adapter the internal antenna is composed by the two spiral tracks at the right.

![WiFi Adapter PCB next to an antenna cable cut and prepared to be soldered](/blog/images/2013/IMG_1770.jpg)

I cut the connector and stripped some of the insulation. After that I separated the core from the shielding and striped some of the core insulation.

![WiFi Adapter PCB next to an antenna and it's plastic shell](/blog/images/2013/IMG_1771.jpg)

Then I soldered the middle lead to one of the antenna pads and the shielding wire to the metal housing.

I didn't do any special tests but the change was that from dropping the connection every 2 minutes and running at 11Mbps now the adapter maintains a stable connection at 54Mbps
