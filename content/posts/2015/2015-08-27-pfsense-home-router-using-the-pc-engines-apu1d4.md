---
title: pfSense home router using the PC Engines APU1D4
author: silviu
type: post
date: 2015-08-27T09:05:18+00:00
url: /2015/08/27/pfsense-home-router-using-the-pc-engines-apu1d4/
dsq_thread_id:
  - 4071241726
categories:
  - tech
tags:
  - amd
  - apu1d4
  - openvpn
  - pc engines
  - pfsense
  - t40e

---
{{< figure 
    src="/blog/images/2015/pcalix-home-router.jpg" 
    alt="Picture of PC Engines APU1D4 with cover removed, a wireless card mounted in the middle slot and an ADATA 32GB mSATA SSD next to it, ready to be mounted." 
>}}


My old home router based on a sandy bridge dual core celeron and a gigabyte motherboard got "stolen" by my wife to use as a desktop as her old laptop was getting pretty slow.

I ran for a while Tomato on a Cisco E3200 router but it wasn't able to keep up with my home connection (300 down / 100 up). Even if the router has gigabit ports it was only able to nat at ~100-150Mbit and openvpn was limited to around 10Mbit

The decision came (due to what is available in my part of the world) to the Fitlet X or the PC Engines APU1D4.

The fitlet has 4 intel LAN ports and a quad core AMD 1GHz cpu (two generations newer than the APU). This was really apealing oposed the APU's dual core bobcat and 3 realtek based NICs.

Eventually I settled with the APU due to the two internal mini-pcie slots and being only half the cost of the Fitlet. (Consider that you have to buy RAM for the fitlet-x and that you don't have any internal mini-pcie left, the only one is used by the FACET card with the 3 LANs)

I won't go into detail about the [build][1] or do a [full review][2] as this has already been made. I will only go trough the bits of information I had trouble finding before and after buying it.

{{< figure 
    src="/blog/images/2015/apu_speedtest_4606109727.png" 
    alt="Screenshot of speedtest ran using the APU1D4 router showing 297.86 Mb/s download and 102.66 Mb/s upload." 
>}}

* **Throughput**: without heavy use (squid, snort, etc.) you should see 400-500 Mbit WAN->LAN (limited by the realtek NICs). I know Mbit is not a good measure of a router/firewall performance but this is what matters to me at home. I saw mentions of 600 Mbit. I was eager to deploy it so I didn't do any testing so all I can say is that 300Mbit works fine without any strain.
* **OpenVPN:** it does around 50Mbit for me using AES-CBC-128. This was really a tough one as I didn't find any useful values before buying and it was important for me. It's a bit disappointing but very usable. The Bobcat T40E doesn't support AES-NI but as far as I found out from others it's not really helping OpenVPN either. There is low hope that newer versions of OpenVPN will perform better. The Fitlet-X CPU should be 15% faster due to IPC gains on it's newer core so you should see a bit more.
* **Temperature: **it appears that ~60 deg. C in idle is normal. Coming from Intel CPUs this worried me at first but seems normal for this CPU
* **Wireless: **if you go the pfSense route as I did get the Compex WLE200NX usually sold together with the APU. It's atheros (best for pfSense) and what most pfSense developers using the APU have.
* **SSD**: don't buy the 16GB crap SSD that is offered together with this board. Get a cheap ADATA/whatever instead. It's probably going to be 32GB and at least twice as fast
* **Case:** important due to the solution PC Engines chose for [cooling][1]. Note that this case doesn't offer space for a 2.5 SSD/HDD (even if one SATA port is onboard), additional USBs (even if headers are present) or for a second set of antennas (even if two mini-pcie devices can be installed)

[1]: http://www.pcengines.ch/apucool.htm
[2]: http://planet.ipfire.org/post/pc-engines-apu1c-a-review