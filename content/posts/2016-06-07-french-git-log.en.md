---
title: French Git Log
author: Brahim
type: post
date: 2016-06-07T09:25:33+00:00
url: /french-git-log-2/
categories:
  - How to ?
tags:
  - git

---
Git log in colors.

<img class="size-full wp-image-1501 aligncenter" src="http://brahim.hamdouni.com/wp-uploads/french-git.png" alt="french git example" srcset="http://brahim.hamdouni.com/wp-uploads/french-git.png 782w, http://brahim.hamdouni.com/wp-uploads/french-git-300x135.png 300w, http://brahim.hamdouni.com/wp-uploads/french-git-768x345.png 768w, http://brahim.hamdouni.com/wp-uploads/french-git-600x269.png 600w, http://brahim.hamdouni.com/wp-uploads/french-git-624x280.png 624w" sizes="(max-width: 706px) 89vw, (max-width: 767px) 82vw, 740px" />

<!--more-->

<pre>git log --pretty='format:%Cblue%h%Creset %ad %Cred%&lt;(8,trunc)%an%Creset%Cgreen%d%Creset %s' --date=short</pre>

Shows how to use pretty format in Git with colors and fixed with columns (trunc) :

%Cblue &#8230; %Creset
:   begin and end a colored sequence (here in blue, also possible : red and green)

%h
:   hash short format

%ad
:   author date (short version with the &#8211;date=short git argument)

%<(8,trunc)
:   the next item will take 8 positions with spaces at right if necessary and truncated if longer

%an
:   author name

%d
:   ref names (branch, tag, &#8230;)

%s
:   subject (ie the commit comment)