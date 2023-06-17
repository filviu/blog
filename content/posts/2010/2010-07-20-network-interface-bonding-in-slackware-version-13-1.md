---
title: Network interface bonding in Slackware (version 13.1)
author: silviu
type: post
date: 2010-07-20T11:26:08+00:00
url: /2010/07/20/network-interface-bonding-in-slackware-version-13-1/
dsq_thread_id:
  - 326479341
categories:
  - old
tags:
  - bond
  - bonding
  - failover
  - network
  - redudancy
  - slackware
  - temp_on
  - trunk
  - trunking

---
A backup NAS I set up for a client had some problems - i.e. from time to time the network card would hang forcing a reboot (the machine was headless). The disks in the nas are RAID 1 providing redundancy in case of failure. We wanted the same with the network. So, nothing easier than to install a second network card and set up bonding.

### What is network bonding?

Bonding is the same as port trunking. It means that two (ore more) physical network connections are combine to form one virtual network connection. The added benefit is that bandwidth adds too.  So theoretically this could offer multi gigabit capabilities.

### How is it configured

First you need a small utility that comes with the linux kernel: **ifenslave**. So we must compile it. After that it should be moved somewhere more apropriate.
```bash
cd /usr/src/linux/Documentation/networking
gcc -Wall -O -I/usr/src/linux/include ifenslave.c -o ifenslave
cp ifenslave /sbin/ifenslave
```
Then we need some scripts that will set up bonding on boot. So we go to **/etc/rc.d** and create a new file called **rc.bond**
```bash
cd /etc/rc.d
touch rc.bond
```
Edit the file you just created to contain the following:
```bash
#!/bin/sh

case "$1" in
'start')
echo "start bond0"
modprobe bonding mode=balance-rr miimon=100
modprobe tg3
ifconfig bond0 up
ifenslave bond0 eth0
ifenslave bond0 eth1
#You don't necesarily need to change the hardware address
#It will take it from the first hardware interface
#ifconfig bond0 hw ether 00:16:3e:aa:aa:aa
;;
'stop')
ifconfig bond0 down
rmmod bonding
rmmod tg3
;;
*)
echo "Usage: $0 {start|stop}"
;;
esac
```
Save this file and make it executable
```bash
chmod +x /etc/rc.d/rc.bond
```
We need to start this on boot. So edit rc.M You need to find the line containing **#Initialize the networking hardware** and insert this after it
```bash
\# If script rc.bond is executeable then start it
if [ -x /etc/rc.d/rc.bond ]; then
. /etc/rc.d/rc.bond start
fi
```
Finally we must configure **rc.inet1.conf** to set our bond interface and to make sure the physical interfaces are not configured. Add the following:
```bash
IFNAME[4]="bond0"
IPADDR[4]="XXX.XX.XX.XX"
NETMASK[4]="255.255.255.0"
USE_DHCP[4]=""
DHCP_HOSTNAME[4]=""
```
**Make sure that the physical interfaces, like 0, 1 and so on are NOT configured.**
Reboot, and everything will be set.

For your reference those are the bonding modes available:

> **mode=0 (balance-rr)**
> Round-robin policy: Transmit packets in sequential order from the first available slave through the last. This mode provides load balancing and fault tolerance.
> 
> **mode=1 (active-backup)**
> Active-backup policy: Only one slave in the bond is active. A different slave becomes active if, and only if, the active slave fails. The bond's MAC address is externally visible on only one port (network adapter) to avoid confusing the switch. This mode provides fault tolerance. The primary option affects the behavior of this mode.
> 
> **mode=2 (balance-xor)**
> XOR policy: Transmit based on [(source MAC address XOR'd with destination MAC address) modulo slave count]. This selects the same slave for each destination MAC address. This mode provides load balancing and fault tolerance.
> 
> **mode=3 (broadcast)**
> Broadcast policy: transmits everything on all slave interfaces. This mode provides fault tolerance.
> 
> **mode=4 (802.3ad)**
> IEEE 802.3ad Dynamic link aggregation. Creates aggregation groups that share the same speed and duplex settings. Utilizes all slaves in the active aggregator according to the 802.3ad specification.
> 
> <pre><em>Pre-requisites:
	1. Ethtool support in the base drivers for retrieving
	the speed and duplex of each slave.
	2. A switch that supports IEEE 802.3ad Dynamic link
	aggregation.
	Most switches will require some type of configuration
	to enable 802.3ad mode.</em>
```
> 
> **mode=5 (balance-tlb)**
> Adaptive transmit load balancing: channel bonding that does not require any special switch support. The outgoing traffic is distributed according to the current load (computed relative to the speed) on each slave. Incoming traffic is received by the current slave. If the receiving slave fails, another slave takes over the MAC address of the failed receiving slave.
> 
> <pre><em>Prerequisite:
	Ethtool support in the base drivers for retrieving the
	speed of each slave.</em>
```

> **mode=6 (balance-alb)**
> Adaptive load balancing: includes balance-tlb plus receive load balancing (rlb) for IPV4 traffic, and does not require any special switch support. The receive load balancing is achieved by ARP negotiation. The bonding driver intercepts the ARP Replies sent by the local system on their way out and overwrites the source hardware address with the unique hardware address of one of the slaves in the bond such that different peers use different hardware addresses for the server.
> 
> [source: <a href="http://www.linuxhorizon.ro/bonding.html" target="_blank" rel="noopener">http://www.linuxhorizon.ro/bonding.html</a>]

The most used are the first four mode types...