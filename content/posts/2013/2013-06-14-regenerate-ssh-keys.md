---
title: Regenerate SSH keys
author: silviu
type: post
date: 2013-06-14T12:04:43+00:00
url: /2013/06/14/regenerate-ssh-keys/
dsq_thread_id:
  - 1401165275
categories:
  - old
tags:
  - centos
  - rhel
  - ssh
  - temp_on
  - virtualisation

---
I'm a big fan of virtualization. I find it very useful both on my workstation as for the servers. What this means is that I often clone virtual machines to repurpose, run tests or simply add web capacity for load balanced sites. One of the steps is that you have to regenerate the ssh keys (besides the usual suspects that are changing IP, hostname and so on) so you don't have multiple hosts with the same ssh keys. At least on CentOS and RHEL this simply means removing all the keys from **/etc/ssh**

[cce_bash]  
cd /etc/ssh/  
/bin/rm \*key\*  
[/cce_bash]

The init script for SSH will detect that the host keys are missing and will regenerate them. Comment below if this works for other distros!