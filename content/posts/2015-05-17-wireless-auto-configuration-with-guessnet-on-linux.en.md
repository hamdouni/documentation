---
title: Wireless auto configuration with guessnet on Linux
author: Brahim
type: post
date: 2015-05-17T17:52:51+00:00
url: /wireless-auto-configuration-with-guessnet-on-linux/
categories:
  - How to ?
  - Linux
tags:
  - howto
  - linux
  - ubuntu
format: image

---
<img class="alignright wp-image-1383 size-thumbnail" src="http://brahim.hamdouni.com/wp-uploads/eiffel-wireless-150x150.png" alt="The wireless tour eiffel" width="150" height="150" />
  
Assume we have access to the wifi at work and at home. How can I configure my laptop to automatically connect to the right network without using a graphical network manager ? Welcome guessnet !
  
<!--more-->


  
Install the guessnet package :

<pre>sudo apt-get install guessnet</pre>

Edit your /etc/network/interface :

<pre>auto wlan0
mapping wlan0
	script /usr/sbin/guessnet-ifupdown
	map home work
	map timeout: 9
	map init-time: 9
	map verbose: true
	map debug: false	

iface home inet dhcp
	wpa-ssid "<em>homessid</em>"
	wpa-psk "<em>homepassword</em>"
	test wireless essid <em>HOMESSID</em>

iface work inet dhcp
	wpa-ssid "<em>workssid</em>"
	wpa-psk "<em>workpassword</em>"
	test wireless essid <em>WORKESSID</em>
</pre>

_(variables to adapt to your configuration in italic)_

We define the &#8216;home&#8217; and &#8216;work&#8217; networks as usual with the iface command. The 2 differences are :

  * we use the virtual interface &#8220;work&#8221; and &#8220;home&#8221; instead of the real interface &#8220;wlan0&#8221;.
  * we add a test line that checks the ssid : this is used by guessnet to guess the right network

The mapping block uses an external script (here guessnet) with prudent parameters

  * the &#8216;map home work&#8217; tells guessnet to only check this 2 networks
  * the init-time wait a little before configuring, to let the drive enough time

That&#8217;s it !