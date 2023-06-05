---
title: Use Vagrant on Windows with Ansible under Cygwin
author: silviu
type: post
date: 2016-02-04T11:24:45+00:00
url: /2016/02/04/use-vagrant-on-windows-with-ansible-under-cygwin/
dsq_thread_id:
  - 4550707487
categories:
  - tech
tags:
  - ansible
  - cygwin
  - vagrant
  - Windows

---
If due to some reason you have to run vagrant under windows and plan on using Ansible you will need a couple of wrappers.

[ansible-playbook.bat][1] has to be in the Windows PATH;

[ansible-winpath-playbook.sh][2] is called by ansible-playbook.bat to change paths from Windows style paths to *nix style paths that ansible under cygwin can understand.

 [1]: https://gist.github.com/filviu/20f8aca03b72069998b3#file-ansible-playbook-bat
 [2]: https://gist.github.com/filviu/20f8aca03b72069998b3#file-ansible-winpath-playbook-sh