---
title: '#Docker from scratch, #Golang and Multipart upload'
author: Brahim
type: post
date: 2018-01-26T12:25:23+00:00
url: /docker-from-scratch-golang-and-multipart-upload/
categories:
  - How to ?
  - Linux
  - Share
tags:
  - console
  - dev
  - docker
  - golang
  - howto
  - minimal
  - scratch
  - ubuntu

---
<img class="alignnone size-full wp-image-1726" src="http://brahim.hamdouni.com/wp-uploads/gophers-small.png" alt="" width="700" height="308" srcset="http://brahim.hamdouni.com/wp-uploads/gophers-small.png 700w, http://brahim.hamdouni.com/wp-uploads/gophers-small-300x132.png 300w, http://brahim.hamdouni.com/wp-uploads/gophers-small-600x264.png 600w, http://brahim.hamdouni.com/wp-uploads/gophers-small-624x275.png 624w" sizes="(max-width: 700px) 100vw, 700px" />

<!--more-->To reduce docker container size we can built the image from scratch instead of using bloated images, like debian or worse ubuntu.

But to put a golang binary in it you have to take care of some important stuff. We&#8217;ll see briefly how to do it. For more details, see [Building Minimal Docker Containers For Go Applications][1]

Compile staticaly your go program :

<pre>CGO_ENABLED=0 GOARCH=amd64 GOOS=linux go build -a -installsuffix cgo -o server</pre>

Your Dockerfile looks like this :

<pre>FROM scratch
ADD static /static
ADD server /server
CMD /server
</pre>

But if you add some upload code in your program, this won&#8217;t work. The upload needs the tmp folder for big files that are sent in multipart form.
  
Below, the code in the os.file_unix Go package :

    // TempDir returns the default directory to use for temporary files.
    func TempDir() string {
      dir := Getenv("TMPDIR")
    	if dir == "" {
    		if runtime.GOOS == "android" {
    			dir = "/data/local/tmp"
    		} else {
    			dir = "/tmp"
    		}
    	}
    	return dir
    }
    

So, as we are on linux, dir = &#8220;/tmp&#8221; is our usual suspect.

But the scratch docker does not contain a tmp folder. This was a hard bug to catch but so easy to fix, just changing the Docker file :

<pre>FROM scratch
VOLUME /tmp
ADD static /static
ADD server /server
</pre>

Now link the container /tmp to the host tmp :

<pre>docker run -P -v /tmp:/tmp your_image 
</pre>

That&#8217;s it ! Enjoy a fully functionnal minimal docker golang application !

 [1]: https://blog.codeship.com/building-minimal-docker-containers-for-go-applications/