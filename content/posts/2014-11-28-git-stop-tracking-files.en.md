---
title: GIT – stop tracking files
author: Brahim
type: post
date: 2014-11-28T10:19:27+00:00
url: /git-stop-tracking-files/
fb_author_post_id:
  - 748829645184830
categories:
  - Git
  - How to ?
tags:
  - dev
  - git

---
If you have some files that you need to have in your repo but don’t need to have updates, git allows it :

    git update-index --skip-worktree <FILES>
    

Then a “git status” won’t show those files until you do :

    git update-index --no-skip-worktree <FILES>
    

To show the skipped files :

    git ls-files -v . | grep ^S
    

&#8211;skip-worktree is a better solution than &#8211;assume-unchanged because status will not get lost once an upstream change is pulled.

source : <http://stackoverflow.com/a/39776107/3181414>

&nbsp;