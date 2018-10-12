---
title: 'usb mount and policykit [EN]'
author: Brahim
type: post
date: 2014-06-18T21:41:51+00:00
url: /usb-mount-and-polykit-en/
fb_author_post_id:
  - 670098129724649
post_to_facebook_timeline:
  - 1
categories:
  - How to ?
  - Linux
tags:
  - dbus
  - desktop
  - dwm
  - gnome-settings-daemon
  - linux
  - policykit
  - storage
  - ubuntu
  - usb

---
When you&#8217;re not on the &#8216;<a title="Wikipedia on Desktop Environment" href="http://en.wikipedia.org/wiki/Desktop_environment" target="_blank">Desktop Environment</a>&#8216; side and rather be in light linux config, you have to deal with annoying little problems. I&#8217;m using <a title="Suckless is DWM home" href="http://dwm.suckless.org/" target="_blank">DWM</a> as my tiled window manager and loving it for years. It&#8217;s fast, flexible and fun. My linux desktop is up and running after a few seconds&#8230; (ok, thanks also to the ssd 🙂 ).

But, after I upgraded to Ubuntu 14.04, I&#8217;ve lost the ability to mount my usb disks with the file manager (same problem with Nautilus or Thunar). I&#8217;m getting this frustrating &#8220;not authorized&#8221; message.
  
My work around was to &#8216;pmount&#8217; the disk. It works but I need to search for the right device before, with dmesg, then provide the right syntax. Not so fun.

After digging a while, I found out that authorizations are managed with policykit. So after reading man page after man page, posts after posts, I found a way to easily mount my usb disks in my file manager.

Just edit a new policykit config file :

> sudo nano /etc/polkit-1/localauthority/50-local.d/55-myconf.pkla

The number and the .pkla extension are mandatory to respect. The name &#8216;myconf&#8217; is as you will.
  
Inside this file, insert those lines :

> [Dealing with disks]
  
> Identity=unix-group:plugdev
  
> Action=org.freedesktop.udisks2.filesystem-mount;org.freedesktop.udisks2.eject-media;org.freedesktop.ud$
  
> ResultAny=yes
  
> ResultInactive=yes
  
> ResultActive=yes

Now, we have to restart DBUS as it&#8217;s the service that launch the polkitd daemon

> sudo restart dbus

If you launch, as I do, gnome-settings-daemon manually, you need to relaunch it after dbus

> gnome-settings-daemon -r &

That&#8217;s it ! Plug a usb drive and use your file manager to browse it. No more &#8216;not authorized&#8217; message !