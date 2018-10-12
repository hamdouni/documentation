---
title: 'Force #wifi interface name on #Ubuntu 18.04'
author: Brahim
type: post
date: 2018-09-07T14:31:00+00:00
url: /force-wifi-interface-name-on-ubuntu-18-04/
categories:
  - How to ?
  - Linux
  - Share
tags:
  - console
  - howto
  - linux
  - network
  - shell
  - ubuntu
  - udev
  - wifi

---
Using Udev, you can change the wifi interface name.

First, you need to get the mac address.<!--more-->

<pre>$ ip link

1: lo: &lt;LOOPBACK,UP,LOWER_UP&gt; mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: <span style="color: #ff0000;"><strong>wlp1s0</strong></span>: &lt;BROADCAST,MULTICAST,UP,LOWER_UP&gt; mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether <span style="color: #ff0000;"><strong>9c:b6:d0:8a:71:11</strong></span> brd ff:ff:ff:ff:ff:ff
</pre>

My wifi interface is name wlp1s0 and its mac address is just after the keyword &#8220;link/ether&#8221; : 9c:b6:d0:8a:71:11.

Now, create or update a udev rules file in /etc/udev/rules.d containing something like :

<pre>$ cat /etc/udev/rules.d/60-persistent-net.rules

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<strong><span style="color: #ff0000;">9c:b6:d0:8a:71:11</span></strong>", ATTR{type}=="1", NAME="<strong><span style="color: #ff0000;">wlan0</span></strong>"</pre>

You certainly need root access. Just change the address and choose the name you want, then reboot.

Check if all is ok with :

<pre>$ ip link

1: lo: &lt;LOOPBACK,UP,LOWER_UP&gt; mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: <strong><span style="color: #ff0000;">wlan0</span></strong>: &lt;BROADCAST,MULTICAST,UP,LOWER_UP&gt; mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether 9c:b6:d0:8a:71:11 brd ff:ff:ff:ff:ff:ff
</pre>