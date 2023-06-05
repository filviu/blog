---
title: Wake on LAN a machine using Python – WOL
author: silviu
type: post
date: 2010-01-16T21:50:17+00:00
url: /2010/01/16/wake-on-lan-a-machine-using-python-wol/
dsq_thread_id:
  - 326504288
categories:
  - old
tags:
  - python
  - temp_on
  - wol

---
<img decoding="async" loading="lazy" class="alignleft size-thumbnail wp-image-688" title="Wake-on-lan-cable" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/01/Wake-on-lan-cable-150x150.jpg" alt="" width="150" height="150" />This is something useful: code to wake up a machine on lan using python. Since python is available on most devices now (symbian, maeom, windows, linux and so on) it's pretty usefull. So, if you have machines that you want to be able to start this is the code to do it. I found it floating on the internet but since it's GPL I see no problem in posting it. Full credit and thanks for the useful code go to the author. BTW I use this on my n800 tablet to wake up my backup server and my media center pc - what will you use it for?  
[ccNe_python]  
Wake-On-LAN  
#  
\# Copyright (C) 2002 by Micro Systems Marc Balmer  
\# Written by Marc Balmer, marc@msys.ch, http://www.msys.ch/  
\# This code is free software under the GPL

import struct, socket

def WakeOnLan(ethernet_address):

\# Construct a six-byte hardware address

addr\_byte = ethernet\_address.split(':')  
hw\_addr = struct.pack('BBBBBB', int(addr\_byte[0], 16),  
int(addr_byte[1], 16),  
int(addr_byte[2], 16),  
int(addr_byte[3], 16),  
int(addr_byte[4], 16),  
int(addr_byte[5], 16))

\# Build the Wake-On-LAN "Magic Packet"&#8230;

msg = 'xff' \* 6 + hw_addr \* 16

\# &#8230;and send it to the broadcast address using UDP

s = socket.socket(socket.AF\_INET, socket.SOCK\_DGRAM)  
s.setsockopt(socket.SOL\_SOCKET, socket.SO\_BROADCAST, 1)  
s.sendto(msg, (", 9))  
s.close()

\# Example use  
WakeOnLan('0:3:93:81:68:b2')  
[/ccNe_python]