---
title: "BSPWM Setup"
date: 2023-07-05T15:37:27+05:30
authors: ["Vikal Singh"]
description: ""
tags: ["Bspwm","dmenu","st","linux","sxhkd","alacritty","polybar"]
categories: [""]
series: [""]
url: ""
externalLink: ""
featuredImage: ""
disableComments: true
draft: false
---

### Installing ST, DMENU, and BSPWM

<div align="center">
<img src="/images/IMG_20230705_084401_490.jpg" alt="Image" width=100%>
</div>

### Introduction

So Let's Start, we will be installing two things. A window system and a layout manager. For this installation I'm using Xorg and bspwm. For those who don't know bspwm is tiling window manager for Xorg . we will install st to be our default terminal and also make use of dmenu for launching applications, I will installed both of them in addition to bspwm.

### Install Dependencies
Firt Let's install the dependencies required by st, dmenu and bspwm and other stuff.

<h4> For Arch Linux </h4>

```yaml
$ sudo pacman -S base-devel git libx11 libxft xorg-server xorg-xinit libxinerama terminus-font bspwm sxhkd nitrogen picom polybar 
```
- base-devel Since I will be installing from source this package contains various tools to compile software.
- git Is needed to get the source code from the suckless git repositories.
- libx11, libxinerama and libxft Dependanices required by dwm otherwise it will fail when trying to compile it.
- xorg-server Is the display server that provides the windows that dwm will manage.
- xorg-xinit Allows us to start the display server.
- terminus-font Dwm is configured to use a monospaced font and since I installed a barebones system I need to install such a font now.
- polybar is very customisable bar 
- nitrogen is for wallpaper
- picom is compositor
- alacritty is GPU accelerated terminal

Install Yay - AUR helper, you can use others too, but I like yay.

```yaml
yay -Syyu alacritty
```

<h4> For Debian/Ubuntu Linux </h4>

```yaml
$ sudo at install build-essential bspwm sxhkd git libx11-dev libxft-dev xorg libxinerama-dev nitrogen picom polybar
```

- build-essential Since I will be installing from source this package contains various tools to compile software.
- git Is needed to get the source code from the suckless git repositories.
- libx11-dev, libxinerama-dev and libxft-dev Dependanices required by dwm otherwise it will fail when trying to compile it.
- xorg Is the display server that provides the windows that dwm will manage.
- xinit Allows us to start the display server. it is merged in xorg
- polybar is very customisable bar
- nitrogen is for wallpaper
- picom is compositor
- alacritty is GPU accelerated terminal, alacritty is nor available in ubuntu repo, so on Ubuntu we have to build it using cargo

#### Download Git Repositories 

I am not installing DMenu, ST from repository, We will build it from source because it offers more control and customisation when compiling from source.

So, let's Start cloning Repos.

```yaml
$ mkdir suckless 
$ cd suckless/
$ git clone git://git.suckless.org/st 
$ git clone git://git.suckless.org/dmenu
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
#### Setup Bspwm, Sxhkd 
We have installed BSPWM, and SXHKD, but now we will copy the configuration, because its empty by default.
```yaml
$ cd ~/.config/ && mkdir -p bspwm sxhkd
$ cp /usr/share/doc/bspwm/examples/bspwmrc ~/.config/bspwm/
$ cp /usr/share/doc/bspwm/examples/sxhkdrc ~/.config/sxhkd/
$ chmod u+x ~/.config/bspwm/bspwmrc
```

#### Keybindings: sxhkdrc 

Check the config file, learn/modify the keybindings to your liking:
```yaml
$ nvim ~/.config/sxhkd/sxhkdrc
```
Basic shortcuts (not all default):
This is my config of SXHKD, You can copy paste it to the sxhkdrc file and then customize it as you like.
```yaml
# wm independent hotkeys
# terminal emulator
super + Return
        st
# program launcher
super + d
        dmenu_run
#its configuration files:
super + Escape
	pkill -USR1 -x sxhkd
# bspwm hotkeys
# quit/restart bspwm
super + alt + {w,r}
	bspc {quit,wm -r}
# close and kill
super + {_,shift + }q
	bspc node -{c,k}
# alternate between the tiled and monocle layout
super + m
	bspc desktop -l next

# send the newest marked node to the newest preselected node
super + y
	bspc node newest.marked.local -n newest.!automatic.local

# swap the current node and the biggest window
super + g
	bspc node -s biggest.window
#
# state/flags
#
# set the window state
super + {t,shift + t,s,f}
	bspc node -t {tiled,pseudo_tiled,floating,fullscreen}
# set the node flags
super + ctrl + {m,x,y,z}
	bspc node -g {marked,locked,sticky,private}
#
# focus/swap
# focus the node in the given direction
super + {_,shift + }{h,j,k,l}
	bspc node -{f,s} {west,south,north,east}

# focus the node for the given path jump
super + {p,b,comma,period}
	bspc node -f @{parent,brother,first,second}

# focus the next/previous window in the current desktop
super + {_,shift + }c
	bspc node -f {next,prev}.local.!hidden.window

# focus the next/previous desktop in the current monitor
super + bracket{left,right}
	bspc desktop -f {prev,next}.local

# focus the last node/desktop
super + {grave,Tab}
	bspc {node,desktop} -f last
# focus the older or newer node in the focus history
super + {o,i}
	bspc wm -h off; \
	bspc node {older,newer} -f; \
	bspc wm -h on
# focus or send to the given desktop
super + {_,shift + }{1-9,0}
	bspc {desktop -f,node -d} '^{1-9,10}'
#
# preselect
# preselect the direction
super + ctrl + {h,j,k,l}
	bspc node -p {west,south,north,east}

# preselect the ratio
super + ctrl + {1-9}
	bspc node -o 0.{1-9}

# cancel the preselection for the focused node
super + ctrl + space
	bspc node -p cancel

# cancel the preselection for the focused desktop
super + ctrl + shift + space
	bspc query -N -d | xargs -I id -n 1 bspc node id -p cancel

#
# move/resize
#

# expand a window by moving one of its side outward
super + alt + {h,j,k,l}
	bspc node -z {left -20 0,bottom 0 20,top 0 -20,right 20 0}

# contract a window by moving one of its side inward
super + alt + shift + {h,j,k,l}
	bspc node -z {right -20 0,top 0 20,bottom 0 -20,left 20 0}

# move a floating window
super + {Left,Down,Up,Right}
	bspc node -v {-20 0,0 20,0 -20,20 0}

```

#### Config file: bspwmrc 

Check the config file:

```yaml
$ vim ~/.config/bspwm/bspwmrc
```
Declare the apps to autostart when launching a session:

make sure sxhkdrc is launched at start: 
 ```yaml 
 pgrep -x sxhkd > /dev/null || sxhkd &
 ```

compositing manager: 
```yaml
picom &
```


bar (here polybar, throught a script):
```yaml 
 polybar &
```

wallpaper: 
```yaml
nitrogen --restore &
```



#### Bar: polybar
Now for polybar, Using the default config is easy and understandable, so i would suggest you to do that. But if you are comfortable with customising it then you can do it easily.
Here i am using default polybar config.
```yaml
$ mkdir ~/.config/polybar
$ cp /etc/polybar/config.ini ~/.config/polybar/
$ vim ~/.config/polybar/config 
```


#### Starting Bspwm
Since we have installed xorg-xinit I need to create a .xinitrc in my home folder. I am using [Neovim](https://neovim.io/) Editor, You can use any You Like.

```yaml
$ nvim ~/.xinitrc
```
The contents of this file is just.

```yaml
exec bspwm 
```
I can now start xorg and dwm with the below command.

```yaml
$ startx
```
Now, We have got our basic minimal dwm setup.

<h4>
  
Note : If you don't want any mess and don't have time you can directly go to my [GitHub](https://github.com/vikmenace/dotfiles) and  install the beautiful Customised bspwm with dmenu,st, polybar and other stuff directly.
</h4>


#### Steps to Install My Configaration 

```yaml
$ git clone https://github.com/vikmenace/dotfiles
#copy the files to .config folder in home

```
Copy All the files from DOTS folder to .config folder.
Now Sit Back and Relax. 
Set the wallpaper using nitrogen or xwallpaper. 
Reboot or Login Back to bspwm and you got you beautiful customised bspwm with everything you need in it.

It Will look similar to image on the top of this article.


#### Links 

 - [Bspwm](https://wiki.archlinux.org/title/bspwm#:~:text=bspwm%20is%20a%20tiling%20window,EWMH%20is%20partially%20supported)
 - [Polybar](https://github.com/polybar/polybar)
 - [Simple Terminal](https://st.suckless.org/)
 - [DMenu](https://tools.suckless.org/dmenu/)


I don't have comments as I don't want to manage them. You can however contact me at the below address if you want to.

 - [ Email singhvikal891@gmail.com](mailto:singhvikal891@gmail.com)



#### License 

[The contents of this site is licensed under a Creative Commons Attribution-ShareAlike 4.0 International License.](https://creativecommons.org/licenses/by-sa/4.0/)

[=> Return to Homepage](https://vikmenace.github.io)
