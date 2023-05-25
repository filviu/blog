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
<div class="wp-block-image">
  <figure class="aligncenter size-full"><img decoding="async" loading="lazy" width="899" height="549" src="https://www.silviuvulcan.ro/wp-content/uploads/2021/10/pcalix-home-router.jpg" alt="" class="wp-image-3843" srcset="https://www.silviuvulcan.ro/wp-content/uploads/2021/10/pcalix-home-router.jpg 899w, https://www.silviuvulcan.ro/wp-content/uploads/2021/10/pcalix-home-router-300x183.jpg 300w, https://www.silviuvulcan.ro/wp-content/uploads/2021/10/pcalix-home-router-768x469.jpg 768w, https://www.silviuvulcan.ro/wp-content/uploads/2021/10/pcalix-home-router-210x128.jpg 210w" sizes="(max-width: 899px) 100vw, 899px" /></figure>
</div>

My old home router based on a sandy bridge dual core celeron and a gigabyte motherboard got &#8220;stolen&#8221; by my wife to use as a desktop as her old laptop was getting pretty slow.

I ran for a while Tomato on a Cisco E3200 router but it wasn&#8217;t able to keep up with my home connection (300 down / 100 up). Even if the router has gigabit ports it was only able to nat at ~100-150Mbit and openvpn was limited to around 10Mbit

The decision came (due to what is available in my part of the world) to the Fitlet X or the PC Engines APU1D4.

The fitlet has 4 intel LAN ports and a quad core AMD 1GHz cpu (two generations newer than the APU). This was really apealing oposed the APU&#8217;s dual core bobcat and 3 realtek based NICs.

Eventually I settled with the APU due to the two internal mini-pcie slots and being only half the cost of the Fitlet. (Consider that you have to buy RAM for the fitlet-x and that you don&#8217;t have any internal mini-pcie left, the only one is used by the FACET card with the 3 LANs)

I won&#8217;t go into detail about the [build][1] or do a [full review][2] as this has already been made. I will only go trough the bits of information&nbsp;I had trouble finding before and after buying it.

<div class="wp-block-image">
  <figure class="aligncenter size-full"><img decoding="async" loading="lazy" width="300" height="135" src="https://www.silviuvulcan.ro/wp-content/uploads/2021/10/4606109727.png" alt="" class="wp-image-3844" srcset="https://www.silviuvulcan.ro/wp-content/uploads/2021/10/4606109727.png 300w, https://www.silviuvulcan.ro/wp-content/uploads/2021/10/4606109727-210x95.png 210w" sizes="(max-width: 300px) 100vw, 300px" /></figure>
</div>

  * **Throughput**: without heavy use (squid, snort, etc.) you should see 400-500 Mbit WAN->LAN (limited by the realtek NICs). I know Mbit is not a good measure of a router/firewall performance but this is what matters to me at home. I saw mentions of 600 Mbit. I was eager to deploy it so I didn&#8217;t do any testing so all I can say is that 300Mbit works fine without any strain.
  * **OpenVPN:**&nbsp;it does around 50Mbit for me using AES-CBC-128. This was really a tough one as I didn&#8217;t find any useful values before buying and it was important for me. It&#8217;s a bit disappointing but very usable. The Bobcat&nbsp;T40E doesn&#8217;t support AES-NI but as far as I found out from others it&#8217;s not really helping OpenVPN either. There is low hope that newer versions of OpenVPN will perform better. The Fitlet-X CPU should be 15% faster due to IPC gains on it&#8217;s newer core so you should see a bit more.
  * **Temperature:&nbsp;**it appears that ~60 deg. C in idle is normal. Coming from Intel CPUs this worried me at first but seems normal for this CPU
  * **Wireless:&nbsp;**if you go the pfSense route as I did&nbsp;get the Compex&nbsp;WLE200NX usually sold together with the APU. It&#8217;s atheros (best for pfSense) and what most pfSense developers using the APU have.
  * **SSD**: don&#8217;t buy the 16GB crap SSD that is offered together with this board. Get a cheap ADATA/whatever instead. It&#8217;s probably going to be 32GB and at least twice as fast
  * **Case:**&nbsp;important due to the solution PC Engines chose for [cooling][1]. Note that this case doesn&#8217;t offer space for a 2.5 SSD/HDD (even if one SATA&nbsp;port is onboard), additional USBs (even if headers are present) or for a second set of antennas (even if two mini-pcie devices can&nbsp;be installed)

 [1]: http://www.pcengines.ch/apucool.htm
 [2]: http://planet.ipfire.org/post/pc-engines-apu1c-a-review