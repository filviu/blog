---
title: Subdomains pointing to private IPs are not resolved on Tomato
author: silviu
type: post
date: 2015-05-26T10:47:12+00:00
url: /2015/05/26/subdomains-pointing-to-private-ips-are-not-resolved-on-tomato/
dsq_thread_id:
  - 3794467671
categories:
  - old
tags:
  - temp_on

---
Some time ago I used to remember IPs on my home and work network but these days I rely much more on dns and dhcp reservation for this tasks. This has the advantage that I can easy move a service, say git.example.com to a new server.

At home I switched (at least for a while) from a dedicated Debian router/gateway box to a router running Tomato. Suddenly subdomains pointing to private IP addresses were no longer resolved. Turns out the [DNS rebinding protection][1] is at fault. Now you could easily just disable it but this is not the secure way to fix a problem. You can actually white list domains to allow private IPs on subdomains.

Go to Advanced => DHCP / DNS Server (LAN)

**Don't uncheck** _"Prevent DNS-rebind attacks" _as this will leave you vulnerable to this attack. Instead add the following to the _Dnsmasq_
_Custom configuration_

```ini
rebind-domain-ok=/domain1.com/domain2.com/
```

Where domain1.com, domain2.com, etc. are the domains for which you want to allow subdomains that resolve to private IPs.

 [1]: http://en.wikipedia.org/wiki/DNS_rebinding