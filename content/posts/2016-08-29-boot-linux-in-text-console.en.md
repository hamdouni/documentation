---
title: Boot Linux in text console
author: Brahim
type: post
date: 2016-08-29T08:41:27+00:00
url: /boot-linux-in-text-console/
categories:
  - How to ?
  - Linux
tags:
  - boot
  - console
  - howto
  - linux
  - text

---
Get rid of graphic boot on Linux with a few modifications in grub configuration :<!--more-->

<pre># edit your grub config
sudo vi /etc/default/grub

# remove splash, quiet, ... from GRUB_CMDLINE_LINUX_DEFAULT
GRUB_CMDLINE_LINUX_DEFAULT="text"

# save the file and update grub
sudo update-grub
</pre>