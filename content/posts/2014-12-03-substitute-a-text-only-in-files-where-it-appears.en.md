---
title: Substitute a text only in files where it appears
author: Brahim
type: post
date: 2014-12-03T18:12:31+00:00
url: /substitute-a-text-only-in-files-where-it-appears/
categories:
  - How to ?
  - Linux
tags:
  - linux
  - shell

---
For example, to substitute foo with bar

    for f in `grep -lR foo`; do
    	echo -n ">> $f";
    	sed 's/foo/bar/g' $f > $f.tmp ;
    	mv $f.tmp $f ;
    	echo " done.";
    done

  * 1) for loops on all files containing the text “foo”, _grep -l_ only show the file name with corresponding text inside.
  * 3) sed replace foo with bar in all file
  * 4) mv save the modification (delete if you don’t want to overwrite the original files, the modified files is named with .tmp at the end) 
  * 2) & 5) echo: which file is treated