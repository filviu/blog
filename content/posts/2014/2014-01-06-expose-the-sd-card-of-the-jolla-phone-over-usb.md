---
title: Expose the sd-card of the Jolla phone over USB
author: silviu
type: post
date: 2014-01-06T06:41:03+00:00
url: /2014/01/06/expose-the-sd-card-of-the-jolla-phone-over-usb/
dsq_thread_id:
  - 2094819242
categories:
  - old
tags:
  - temp_on

---
I know there are many ways to get content onto the Jolla phone (rsync over ssh springs to mind) but for large files I still prefer USB. Having just bought a 64Gb micro-sd I wanted to copy the bulk of my music and videos using USB. BTW this is the card I bought and works great (formatted as btrfs) [Kingston 64GB Class 10][1]<img decoding="async" loading="lazy" style="border: none !important;margin: 0px !important" alt="" src="http://ir-uk.amazon-adsystem.com/e/ir?t=sgvulcan-21&l=as2&o=2&a=B00AO1VIN8" width="1" height="1" border="0" />

There is one easy step to do. Start the terminal and create a symlink to the card on the phone:

[cce LANG=&#8221;BASH&#8221;]  
[nemo@argo ~]$ devel-su  
Password:  
[root@argo nemo]# cd /home/nemo  
[root@argo nemo]# ln -s /run/user/100000/media/sdcard/  
[/cce]

That&#8217;s it, the folder sdcard in the root of your phone is actually the sd card (windows will report free space on the phone only, though)

 [1]: http://www.amazon.co.uk/gp/product/B00AO1VIN8/ref=as_li_qf_sp_asin_tl?ie=UTF8&camp=1634&creative=6738&creativeASIN=B00AO1VIN8&linkCode=as2&tag=sgvulcan-21