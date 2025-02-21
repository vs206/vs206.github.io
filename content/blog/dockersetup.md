---
title: "Docker Installation"
date: 2023-08-23T15:37:27+05:30
authors: ["Vikal Singh"]
description: ""
tags: ["docker","arch","systemd","linux","containers"]
categories: [""]
series: [""]
url: ""
externalLink: ""
featuredImage: ""
disableComments: true
draft: false
---


##### Installing Docker
Docker is installed via package manager.
###### Arch Linux
```yaml
$ sudo pacman -S docker
```

###### Debian/Ubuntu Linux
```yaml
$ sudo apt-get install docker.io
```


#### Starting Docker Engine
Start the Docker daemon which provides the Docker Engine. This process serves the Docker API and manages Docker containers.
```yaml
$ sudo systemctl start docker.service
```


If you want Docker Engine to automatically start when you system boots issue the below command.
```yaml
$ sudo systemctl enable docker.service
```
Verify that Docker Engine is running.
```yaml
$ docker info
```
Verify that you can run containers. The below will download the latest Arch Linux image and use it to run a "Hello World" bash script in the container.
```yaml
$ docker run -it --rm archlinux bash
```

#### Links
I don't have comments as I don't want to manage them. You can however contact me at the below address if you want to.

 - [Email singhvikal891@gmail.com](mailto:singhvikal891@gmail.com)



#### License 

[The contents of this site is licensed under a Creative Commons Attribution-ShareAlike 4.0 International License.](https://creativecommons.org/licenses/by-sa/4.0/)

[=> Return to Homepage](https://vikmenace.github.io)
