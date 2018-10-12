---
title: If ssh client disconnect and freeze
author: Brahim
type: post
date: 2015-01-14T17:55:18+00:00
url: /if-ssh-client-disconnect-and-freeze/
categories:
  - How to ?
  - Linux

---
Add in your ~/.ssh/config :

    Host *
     ServerAliveInterval 240

src = <a href="http://superuser.com/questions/98562/way-to-avoid-ssh-connection-timeout-freezing-of-terminal-tab" target="_blank">superuser.com</a>