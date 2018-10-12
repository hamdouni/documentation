---
title: Samba public share
author: Brahim
type: post
date: 2018-01-10T15:48:35+00:00
url: /samba-public-share/
categories:
  - How to ?
  - Linux
tags:
  - console
  - howto
  - linux
  - samba
  - shell

---
How to configure a Debian based Linux distribution to share a folder with anyone on the network, with read and write access ?
  
<!--more-->

Create the public directory

<pre>mkdir /media/public && chmod 777 /media/public</pre>

Edit the samba file configuration

<pre>vi /etc/samba/smb.conf</pre>

Add the code below at the end

<pre>[public]
comment = Public Folder
path = /media/public
guest ok = yes
public = yes
writable = yes
printable = no
create mask = 777</pre>

Restart samba

<pre>sudo service smbd restart</pre>