---
title: Convert multiple files to utf8 using vim
author: Brahim
type: post
date: 2014-12-03T17:44:07+00:00
url: /convert-multiple-files-to-utf8-using-vim/
fb_author_post_id:
  - 751410358260092
categories:
  - How to ?
  - Linux
tags:
  - linux
  - shell
  - vim

---
The fastest and more efficient way to batch multiple files encoding conversion :

`` vim +"argdo se fileencoding=utf-8 | w | bnext" +"q" ` find . -type f -name "*.rsp" ` ``

+&#8221;argdo&#8221; : execute the following vim commands for each file (filencode, save and next buffer)

+&#8221;q&#8221; : quit after last one

find : get all files with corresponding name