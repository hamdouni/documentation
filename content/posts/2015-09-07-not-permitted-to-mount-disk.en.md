---
title: 'Not permitted to mount disk ? [EN]'
author: Brahim
type: post
date: 2015-09-07T05:30:59+00:00
url: /not-permitted-to-mount-disk/
post_to_facebook_timeline:
  - 1
wp-to-buffer-success:
  - 1
categories:
  - How to ?
  - Linux

---
A few days ago, I started to have a very disturbing &#8220;Not permitted&#8221; message when trying to mount a usb disk from <a title="Thunar: File manager by XFCE" href="http://en.wikipedia.org/wiki/Thunar" target="_blank">Thunar</a>. The only way I found was to pmount the disk : not as intuitive as just clicking the disk on Thunar.

But after some googling, I found where was the real problem : udisk, who is responsible of mounting disks, uses polkit to know if I have the right to mount, or not, external disk. So, if you have the same problem, follow this steps :

<pre>sudo nano /usr/share/polkit-1/actions/org.freedesktop.udisks2.policy
</pre>

(use your favorite text editor in place of nano)

Then, look for the section with &#8220;udisks2.filesystem-mount&#8221;, inside you&#8217;ll have a &#8220;defaults&#8221; section with interesting stuff :

<pre>&lt;defaults&gt;
&lt;allow_any&gt;auth_admin&lt;/allow_any&gt;
&lt;allow_inactive&gt;auth_admin&lt;/allow_inactive&gt;
&lt;allow_active&gt;auth_admin_keep&lt;/allow_active&gt;
&lt;/defaults&gt;</pre>

Now, replace all &#8220;auth_admin*&#8221; by &#8220;yes&#8221; to give access for every user, like this :

<pre>&lt;defaults&gt;
 &lt;allow_any&gt;yes&lt;/allow_any&gt;
 &lt;allow_inactive&gt;yes&lt;/allow_inactive&gt;
 &lt;allow_active&gt;yes&lt;/allow_active&gt;
&lt;/defaults&gt;</pre>

Save your modifications. Forget this annoying message !