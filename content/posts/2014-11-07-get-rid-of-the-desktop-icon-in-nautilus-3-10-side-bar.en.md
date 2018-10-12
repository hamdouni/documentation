---
title: Get rid of the Desktop icon in Nautilus 3.10 side bar
author: Brahim
type: post
date: 2014-11-07T15:59:15+00:00
url: /get-rid-of-the-desktop-icon-in-nautilus-3-10-side-bar/
fb_author_post_id:
  - 739021069499021
categories:
  - How to ?
  - Linux

---
Add in ~/.config/gtk-3.0/settings.ini

<pre>gtk-shell-shows-desktop=0</pre>

Remove all entries in ~/.config/user-dirs.dirs but let this one :

<pre>XDG_DESKTOP_DIR="$HOME/"</pre>

If you remove this too, each time nautilus is launched, it will create a ~/Desktop folder.

Remove folder Desktop if it exists