---
title: Convert PDF to PNG with enough resolution
author: Brahim
type: post
date: 2017-03-27T23:06:02+00:00
url: /convert-pdf-to-png-with-enough-resolution/
categories:
  - How to ?
  - Linux
tags:
  - console
  - howto
  - ImageMagick
  - linux
  - shell

---
<img class="screenshot wp-image-1714 size-full alignright" src="http://brahim.hamdouni.com/wp-uploads/téléchargement.png" alt="ImageMagick logo" width="256" height="256" srcset="http://brahim.hamdouni.com/wp-uploads/téléchargement.png 256w, http://brahim.hamdouni.com/wp-uploads/téléchargement-150x150.png 150w" sizes="(max-width: 256px) 100vw, 256px" />As &#8216;man convert&#8217; states :

> The convert program is a member of the ImageMagick suite of tools. Use it to convert between image formats as well as resize an image, blur, crop, despeckle, dither, draw on, flip, join, re-sample, and much more.

<!--more-->

I use it to convert a pdf file to png picture with enough pixel density for the screen. This is the command :

<pre>convert -density 100 source.pdf target.png</pre>