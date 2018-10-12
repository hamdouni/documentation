---
title: Horizontal rule in zsh prompt
author: Brahim
type: post
date: 2014-12-26T16:58:41+00:00
url: /horizontal-rule-in-zsh-prompt/
categories:
  - How to ?
  - Linux
tags:
  - linux
  - prompt
  - shell
  - zsh

---
<img class=" size-full wp-image-1304 aligncenter" src="http://brahim.hamdouni.com/wp-uploads/zsh-horizontal-rule-prompt.png" alt="zsh-horizontal-rule-prompt" width="581" height="312" srcset="http://brahim.hamdouni.com/wp-uploads/zsh-horizontal-rule-prompt.png 581w, http://brahim.hamdouni.com/wp-uploads/zsh-horizontal-rule-prompt-300x161.png 300w" sizes="(max-width: 581px) 100vw, 581px" />

Put in your ~/.zshrc :

<pre>PS1=$'%U${(r:$COLUMNS:: :)}%u'$PS1</pre>

_src = <a title="superuser" href="http://superuser.com/questions/845744/how-to-draw-a-line-between-commands-in-zsh-shell" target="_blank">superuser.com</a>_