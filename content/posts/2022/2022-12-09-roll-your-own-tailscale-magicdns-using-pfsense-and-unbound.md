---
title: Roll Your Own Tailscale MagicDNS Using pfSense and Unbound
author: silviu
type: post
date: 2022-12-09T14:38:21+00:00
url: /2022/12/09/roll-your-own-tailscale-magicdns-using-pfsense-and-unbound/
categories:
  - tech

---
# The Why

First question that would come to mind is why bother ? Tailscale implements a perfectly usable MagicDNS feature. Well there are a few reasons I quickly discovered after telling myself _"Looks great, let's enable it"_:

  1. Even if the [issue is closed][1] I still very often get DNS issues in Android if Tailscale with MagicDNS is active. 
  2. When in the "home network" if tailscale is not active you have to remember two URLs: device.something-something.ts.net and device.mydomain.com. Additional troubles for services that only support one trusted URL (Tiny Tiny RSS, joplin-server). 
  3. You can't get SSL certificates with let's encrypt, you have to get them using Tailscale HTTPs

Basically the one that I care the most about is this: My work laptop is already connected to the work tailnet. But I also want it able to connect to a few of my home services (nextcloud, joplin-server) at least when at home - which face it is 90% of the time - without switching connections all the time.

One sollution would be to only use the hostname without the FQDN as URL. DNS search resolves this to either the tailnet URL or device.mydomain.com but I dislike it and doesn't work for SSL.

Another would be to share devices between work and home tailnets but I won't do that due to obvious reasons.
So in the words of one of my [favourite youtubers][2] "I Make a New One!"

## Setup Tailscale and Unbound on pfsense

Beyond the scope of this post, you should already have unbound and the official tailscale package setup on pfsense. These aditional settings are needed for our setup:

Use **DHCP Registration** or **Host Overrides** or both to add machine1.mydomain.com and machine2.mydomain.com with internal IPs to Unbound. Ofc. you can have as many as you want.

**Network interfaces** need to be set to **All**. That's because the tailscale interface doesn't show up in the Unbound interfaces list. Use firewall rules to shield Unbound on unwanted interfaces e.g. on WAN.

Then add the following in the **Custom options** box:

```ini
server:
  access-control-view: 100.64.0.0/10 ts_view

view:
  name: "ts_view"
  view-first: yes
# machine1
  local-data: "service1.mydomain.com. 90 IN A 100.aa.bb.cc"
  local-data: "service2.mydomain.com. 90 IN A 100.aa.bb.cc"
# machine2
  local-data: "service3.mydomain.com. 90 IN A 100.aa.bb.dd"
```

**What this does**: when a request arrives via the 100.64.0.0/10 network (tailscale) it will answer with the IPs defined in the "ts_view" istead of what's registered in overrides or DHCP. Incidently you can also use this feature to answer with different IPs depending on the Unbound interface the request arrives on. (I use it for storage servers serving multiple vlans)

**Go to Access Lists** and **Add** a new one to allow requests from the Tailscale net: <figure class="wp-block-image size-large">

![pfsense settings for Unbound ACLs](/blog/images/2022-12-09/pfsense-unbound-acls.png)

## Setup DNS on Tailscale

Go to **Tailscale Admin Console => DNS**

Add custom Nameservers for your domain **mydomain.com** in this example:<figure class="wp-block-image size-full">

![Tailscale DNS settings](/blog/images/2022-12-09/tailscale-dns-settings.png)

**Replace 100.80.1.2** with the **Tailscale IP** of your pfsense (or whatever you use for this split DNS setup)

# DONE

Once this is setup what happens:

When a machine in your home lan without tailscale tries service1.mydomain.com pfsense will return the internal IP of the machine. Good.

When a machine running tailscale tries service1.mydomain.com tailscale will intercept that and pipe the request to your pfsense via the tailscale interface. This makes Unbound respond with the tailscale IP you defined in the custom view. Good.
If you have a machine at home set to override your home DNS (maybe your work VPN forces other DNS servers) it won't work as any other DNS server doesn't know about service1.mydomain.com. Bad.

 [1]: https://github.com/tailscale/tailscale/issues/4252
 [2]: https://www.youtube.com/c/mymechanics