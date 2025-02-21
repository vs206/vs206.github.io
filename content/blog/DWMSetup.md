---
title: " DWM Setup"
date: 2023-07-15T15:37:27+05:30
authors: ["Vikal Singh"]
description: ""
tags: ["dwm","dmenu","st","linux","suckless"]
categories: [""]
series: [""]
url: ""
externalLink: ""
featuredImage: ""
disableComments: true
draft: false
---

### Installing ST, DMENU and DWM

<div align="center">
<img src="/images/IMG_20230705_080551_895.png" alt="Image" width=100%>
</div>

### Introduction

So Let's Start, we will be require to install two things. A window system of some sort and a layout manager. For this installation I'm going with Xorg and dwm. For those that are not aware dwm is dynamic window manager for Xorg that has been developed by Suckless. Since by default dwm expects st to be installed as the system's terminal and also makes use dmenu using which we launch applications I will installed both of them in addition to dwm.

### Install Dependencies
Firt off We need to install the dependencies required by st, dmenu and dwm.

<h4> For Arch Linux </h4>

```yaml
$ sudo pacman -S base-devel git libx11 libxft xorg-server xorg-xinit libxinerama terminus-font
```
- base-devel Since I will be installing from source this package contains various tools to compile software.
- git Is needed to get the source code from the suckless git repositories.
- libx11, libxinerama and libxft Dependanices required by dwm otherwise it will fail when trying to compile it.
- xorg-server Is the display server that provides the windows that dwm will manage.
- xorg-xinit Allows us to start the display server.
- terminus-font Dwm is configured to use a monospaced font and since I installed a barebones system I need to install such a font now.

<h4> For Debian/Ubuntu Linux </h4>

```yaml
$ sudo at install build-essential  git libx11-dev libxft-dev xorg libxinerama-dev
```

- build-essential Since I will be installing from source this package contains various tools to compile software.
- git Is needed to get the source code from the suckless git repositories.
- libx11-dev, libxinerama-dev and libxft-dev Dependanices required by dwm otherwise it will fail when trying to compile it.
- xorg Is the display server that provides the windows that dwm will manage.
- xorg-xinit Allows us to start the display server. it is merged in xorg


#### Download Git Repositories 

The source code for the software is avialable from the Suckless git repositories so I simply clone them.


```yaml
$ mkdir suckless 
$ cd suckless/
$ git clone git://git.suckless.org/st 
$ git clone git://git.suckless.org/dmenu
$ git clone git://git.suckless.org/dwm 
```

#### Install ST
I install st by first moving to the directory created when cloning the repository.
```yaml
$ cd st
```
Compile and install as usual.
```yaml
$ make clean
$ sudo make install
```
#### Install DMENU
```yaml
$ cd dmenu
```
Again compiling and installing is done with the below commands.
```yaml
$ make clean
$ sudo make install
```


#### Install DWM
```yaml
$ cd dwm/
```
Compile and install as usual.

```yaml
$ make clean
$ sudo make install
```

#### Starting DWM
Since we have installed xorg-xinit I need to create a .xinitrc in my home folder. I am using [Neovim](https://neovim.io/) Editor, You can use any You Like.

```yaml
$ nvim ~/.xinitrc
```
The contents of this file is just.

```yaml
exec dwm
```
I can now start xorg and dwm with the below command.

```yaml
$ startx
```
Now, We have got our basic minimal dwm setup.

<h4>
  
Note : If you don't want any mess and don't have time you can directly go to my [GitHub](https://github.com/singh-vikal/harbs) and use the script to install the beautiful Customised dwm with dmenu,st, and other stuff directly with a single command.
</h4>


#### Steps to Install My Configaration 

```yaml
$ mkdir suckless 
$ cd suckless/
$ git clone https://github.com/singh-vikal/harbs
$ cd harbs/
$ sudo chmod +x install.sh
$ ./install.sh
```
Now Sit Back and Relax.
You just have to select **Yes** at some places and this script will give you a beautiful **Dwm** setup with **dmenu, st, alacritty, slstatus, Brave browser, mpv, audio setup** and other daily required packages.



#### Links 

 - [Dynamic Window Manager (DWM)](https://dwm.suckless.org/)
 - [Suckless](https://suckless.org/)
 - [Simple Terminal](https://st.suckless.org/)
 - [DMenu](https://tools.suckless.org/dmenu/)

I don't have comments as I don't want to manage them. You can however contact me at the below address if you want to.

 - [ Email singhvikal891@gmail.com](mailto:singhvikal891@gmail.com)



#### License 

[The contents of this site is licensed under a Creative Commons Attribution-ShareAlike 4.0 International License.](https://creativecommons.org/licenses/by-sa/4.0/)


#### Credit:
 - [Harsh/Sei](https://github.com/seicq)
 - [Me](https://github.com/vikmenace)


[=> Return to Homepage](https://vikmenace.github.io)
