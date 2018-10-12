---
title: 'Minimal #Docker + #Golang et le téléversement Multipart'
author: Brahim
type: post
date: 2018-01-26T12:25:23+00:00
url: /minimal-docker-golang-et-le-televersement-multipart/
categories:
  - Comment faire ?
  - Linux
  - Partage
tags:
  - howto
  - ubuntu

---
<img class="alignnone size-full wp-image-1726" src="http://brahim.hamdouni.com/wp-uploads/gophers-small.png" alt="" width="700" height="308" srcset="http://brahim.hamdouni.com/wp-uploads/gophers-small.png 700w, http://brahim.hamdouni.com/wp-uploads/gophers-small-300x132.png 300w, http://brahim.hamdouni.com/wp-uploads/gophers-small-600x264.png 600w, http://brahim.hamdouni.com/wp-uploads/gophers-small-624x275.png 624w" sizes="(max-width: 700px) 100vw, 700px" />

<!--more-->Pour réduire la taille d&#8217;un container Docker, on peut créer l&#8217;image en partant de rien, ou plus précisément, en partant de &#8220;scratch&#8221;, qui ne contient rien. On obtient à la fin un container beaucoup plus léger que si l&#8217;on partait de Debian, ou pire, d&#8217;Ubuntu.

Afin de mettre un binaire Go à l&#8217;intérieur, quelques précautions sont nécessaires. Nous verrons rapidement comment faire. Mais si vous voulez avoir plus d&#8217;infos, vous pouvez consulter la page en anglais de Codeship : [Building Minimal Docker Containers For Go Applications][1]

Compiler statiquement votre programme Go :

<pre>CGO_ENABLED=0 GOARCH=amd64 GOOS=linux go build -a -installsuffix cgo -o server</pre>

Votre fichier Dockerfile doit ressembler à ça :

<pre>FROM scratch
ADD static /static
ADD server /server
CMD /server
</pre>

Mais si vous avez besoin d&#8217;une fonctionnalité de téléversement (upload), cela ne va pas marcher. Le téléversement a besoin d&#8217;un dossier temporaire pour traiter les gros fichiers envoyés depuis un formulaire multipart.

Regardons directement dans le code du package Go os.file_unix :

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
    

Comme on est sous Linux, on voit que le dossier temporaire se trouve dans /tmp.

Oui mais notre container, qu&#8217;on a construit à partir de scratch, ne contient pas de dossier /tmp. D&#8217;où plantage du téléversement 🙁

C&#8217;était un bug difficile à trouver, mais la solution est simple. Modifions notre fichier Dockerfile pour ajouter une entrée :

<pre>FROM scratch
VOLUME /tmp
ADD static /static
ADD server /server
</pre>

Maintenant on peut lier notre container avec un dossier qui servira de dossier temporaire comme suit :

<pre>docker run -P -v /tmp:/tmp your_image 
</pre>

Et voilà ! Une image Docker minimale, avec un binaire Go dedans et rien d&#8217;autre.

 [1]: https://blog.codeship.com/building-minimal-docker-containers-for-go-applications/