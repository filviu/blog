---
title: Moving a solaris guest from VMWare to Virtualbox
author: silviu
type: post
date: 2011-06-16T12:01:50+00:00
url: /2011/06/16/moving-a-solaris-guest-from-vmware-to-virtualbox/
dsq_thread_id:
  - 333832946
categories:
  - old
tags:
  - boot
  - reboot
  - solaris
  - temp_on
  - virtualbox
  - vmware

---
<img decoding="async" loading="lazy" class="alignleft size-thumbnail wp-image-1499" title="virtualbox" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2011/06/virtualbox-150x150.png" alt="" width="150" height="150" />I&#8217;m a big fan of Virtualbox. It&#8217;s easy, fast and free. Recently I had to revive an older Solaris guest that used to run under vmware, and to set it up to run under Virtualbox. I quickly found out that after the grub screen it enters a reboot loop and nothing seemed to help. I could boot into failsafe and mount the root partition as /a/

Someone suggested that the problem was that vmware had the disk as SCSI (c0t0d0s0) and virtualbox enumerated them as IDE (c0d0s0). I tried setting the disk on a virtual SCSI controller but it didn&#8217;t help. I set it back to IDE and proceeded to inform Solaris of the new setup: (it takes a bit of tinkering, be sure to have a backup of the image)  
<!--more-->

  1. Boot Solaris in safeboot (failsafe) It&#8217;s usually the last option in Grub.
  2. The original root partition should be found and mounted under /a Be sure to say y and mount it read-write. If you, like me, come from the Linux world running /usr/bin/bash will help you. Also export TERM=xterm will allow vi to run.
  3. Move /a/dev /a/devices and /a/etc/path\_to\_inst to other names (rename them to .old or .orig or something)  
    [cce_bash]  
    mv /a/dev /a/dev.orig  
    mv /a/devices /a/devices.orig  
    mv /a/etc/path\_to\_inst /a/etc/path\_to\_inst  
    [/cce_bash] 
  4. Run **&#8220;devfsadm -r /a&#8221;** to rebuild the devices folders
  5. Now you will fix the boot disk path. Edit **/a/boot/solaris/bootenv.rc** using vi (oh joy) and fix the line that reads **&#8220;setprop bootpath &#8216;/pci@0,0&#8230;.&#8221;** You will want the line to point to the same path as your disk points. Again if you come from Linux you will ask the same as me. Where the @#$% to I get this. Easy **&#8220;ls -l /dev/dsk/c0d0s0&#8221;** (or whatever device **&#8220;df -k&#8221;** says /a is mounted from. The same pci path, without ../../devices needs to go at setprop bootpath. Save and exit.
  6. Edit **/a/etc/vfstab** to match (here you will have **/dev/dsk/c0d0s0** or similar &#8211; see the beauty of this ? 🙂 )
  7. Run **&#8220;bootadm update-archive -v -R /a&#8221;** to rebuild the boot archive on /a
  8. Force to reconfigure on next boot **&#8220;touch /a/reconfigure&#8221;**
  9. **&#8220;cd /; sync; sync; sync; umount /a&#8221;** Don&#8217;t worry much if it wound unmount.
 10. **&#8220;init 6&#8221;** to reboot

Have fun!