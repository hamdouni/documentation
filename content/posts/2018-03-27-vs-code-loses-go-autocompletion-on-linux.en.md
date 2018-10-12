---
title: VS Code loses Go autocompletion on Linux
author: Brahim
type: post
date: 2018-03-26T22:15:38+00:00
url: /vs-code-loses-go-autocompletion-on-linux/
categories:
  - How to ?
tags:
  - bug
  - dev
  - go
  - golang
  - linux

---
On my Linux, just after upgrading Go to version 1.9, I lost autompletion functionality in VS Code.
  
<img src="/wp-uploads/vscode_completion_not_working.png" alt="vscode_completion_not_working" width="768" height="440" class="alignnone size-full wp-image-1879" srcset="http://brahim.hamdouni.com/wp-uploads/vscode_completion_not_working.png 768w, http://brahim.hamdouni.com/wp-uploads/vscode_completion_not_working-300x172.png 300w" sizes="(max-width: 706px) 89vw, (max-width: 767px) 82vw, 740px" />
  
<!--more-->

[This tip][1] did not work for me.

So let&#8217;s try to debug it. 

First, we close the auto-completion server (see <a href="https://github.com/nsf/gocode" rel="noopener" target="_blank">github.com/nsf/gocode</a>) :

<pre>gocode close
killall gocode</pre>

Then we relaunch it as a server in debug mode inside a console :

<pre>gocode -debug -s</pre>

So now, we can see what&#8217;s happening.
  
OK, time to try an auto-completion inside VS Code. 

Bingo ! We got some useful log :

<pre>2018/03/26 23:27:32 Import path "net/http" was not resolved
2018/03/26 23:27:32 Gocode's build context is:
2018/03/26 23:27:32 GOROOT: /usr/local/go
2018/03/26 23:27:32 GOPATH: /home/barim
2018/03/26 23:27:32 GOOS: linux
2018/03/26 23:27:32 GOARCH: amd64
2018/03/26 23:27:32 BzlProjectRoot: ""
2018/03/26 23:27:32 GBProjectRoot: ""
2018/03/26 23:27:32 lib-path: ""
2018/03/26 23:27:32 Error parsing input file (inner block):
2018/03/26 23:27:32 3:6: expected selector or type assertion, found ';'
...
</pre>

Weird, my GOROOT isn&#8217;t at /usr/local/go but at /usr/lib/go.
  
It seems like gocode doesn&#8217;t care about my env and arbitrary choose to look inside this folder.

Ok, let&#8217;s trick him with a symlink :

<pre>sudo ln -s /usr/lib/go /usr/local/go
</pre>

Now it works !

<img src="/wp-uploads/vscode_completion_working.png" alt="vscode_completion_working" width="789" height="738" class="alignnone size-full wp-image-1878" srcset="http://brahim.hamdouni.com/wp-uploads/vscode_completion_working.png 789w, http://brahim.hamdouni.com/wp-uploads/vscode_completion_working-300x281.png 300w, http://brahim.hamdouni.com/wp-uploads/vscode_completion_working-768x718.png 768w" sizes="(max-width: 706px) 89vw, (max-width: 767px) 82vw, 740px" />

 [1]: https://github.com/Microsoft/vscode-go/issues/441