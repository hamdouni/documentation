---
title: ZSH, nohup and background process that lasts…
author: Brahim
type: post
date: 2014-11-27T10:58:55+00:00
url: /zsh-nohup-and-background-process-that-lasts/
fb_author_post_id:
  - 748374655230329
categories:
  - How to ?
  - Linux
tags:
  - linux
  - zsh

---
When I switched to  ZSH, and letting BASH behind, I missed some behaviour : one of them was the ability to quit my terminal while some jobs are still alive.

In ZSH, I get a message like this if I exist with running jobs :

<pre>zsh you have running jobs</pre>

If I exit again, my jobs are killed. But zsh accept some useful option to overide this :

<pre>setopt NO_HUP
 setopt NO_CHECK_JOBS</pre>

First one is for not killing process after terminal exit, and second one is for not warning you about it.