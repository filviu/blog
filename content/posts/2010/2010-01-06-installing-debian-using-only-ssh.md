---
title: Installing Debian using only SSH
author: silviu
type: post
date: 2010-01-06T11:40:32+00:00
url: /2010/01/06/installing-debian-using-only-ssh/
dsq_thread_id:
  - 326479268
categories:
  - old
tags:
  - debian
  - ssh
  - temp_on

---
I have a headless machine at home that I plan to use as a backup and development server. Even though I'm a Skackware guy I chose to install Debian on it. Of course I could have hooked a monitor and keyboard to it but for the sake of exercise I wanted to see if it's possible to install debian using ssh from the very beginning.

The short answer: **it's possible ... maybe**. Your headless machine should already be set to boot of cd if one is present, otherwise it will not work.

Here are the steps needed to start you off:

**1. Download the netinst cd image**

```bash
wget http://mirrors.kernel.org/debian-cd/5.0.3/i386/iso-cd/debian-503-i386-netinst.iso
```

**2. Mount the ISO to a folder, let's call it isoorig**

```bash
mkdir isoorig
mount -o loop -t iso9660 debian-503-i386-netinst.iso isoorig
```

**3. Extract to new folder called isonew**

```bash
mkdir isonew
rsync -a -H –exclude=TRANS.TBL isoorig/ isonew
```

**4. Change the menu to load SSH on boot by default**

```bash
/isonew# nano isolinux/txt.cfg
```

DELETE:
remove "menu default" from "label install"

ADD:

```bash
label netinstall
menu label ^Install Over SSH
menu default
kernel /install.386/vmlinuz
append auto=true vga=normal file=/cdrom/preseed.cfg initrd=/install.386/initrd.gz locale=en_US console-keymaps-at/keymap=us
```

CHANGE:

"default install" to "default netinstall"

EDIT: both files below and change "timeout 0″ to "timeout 4″ to make it auto select netinstall

```bash
nano isolinux/isolinux.cfg
nano isolinux/prompt.cfg
```

**5. Create preseed.cfg file**

```bash
nano isonew/preseed.cfg
```

**6. PASTE this to the preseed file:**

```bash
#### Contents of the preconfiguration file
### Localization
# Locale sets language and country.
d-i debian-installer/locale select en_US
# Keyboard selection.
d-i console-keymaps-at/keymap select us
### Network configuration
# netcfg will choose an interface that has link if possible. This makes it
# skip displaying a list if there is more than one interface.
d-i netcfg/choose_interface select auto
# Any hostname and domain names assigned from dhcp take precedence over
# values set here. However, setting the values still prevents the questions
# from being shown, even if values come from dhcp.
d-i netcfg/get_hostname string newdebian
d-i netcfg/get_domain string local
# Disable that annoying WEP key dialog.
d-i netcfg/wireless_wep string
# The wacky dhcp hostname that some ISPs use as a password of sorts.
#d-i netcfg/dhcp_hostname string radish
d-i preseed/early_command string anna-install network-console
# Setup ssh password
d-i network-console/password password install
d-i network-console/password-again password install
```

**7. Recreate md5sum.txt file**

```bash
md5sum `find -follow -type f` > md5sum.txt
```

**8. Create your new iso image**

```bash
mkisofs -o ../custom_install.iso -r -J -no-emul-boot -boot-load-size 4 -boot-info-table -b isolinux/isolinux.bin -c isolinux/boot.cat ../isonew
```

The image you just obtained is ready to burn. This loads everything automatically and goes to the SSH screen.

Thanks go to people on various debian forums, this information was collected via trial and error and by combining info found around. Have fun with your shiny new headless debian box.