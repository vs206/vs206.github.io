---
title: 'Guide To Git'
date: 2023-09-05T15:52:24+05:30
authors: ["Vikal Singh"]
description: ""
tags: ["git","github","gitlab","linux","Version Control","computer","technology"]
categories: [""]
series: [""]
url: ""
slug: ""
externalLink: ""
featuredImage: ""
disableComments: true
draft: false
---

This is a practical guide for git, and it is mainly aimed towards the ones who have no idea on what and how to use git. If you know someone who does not know how to use git, share them this article.



## What is Git?
Git is a fast, scalable, distributed version control system with an unusually rich command set that provides both high-level operations and full access to internals.

Which means it is a version control system, that tracks the changes that are made on a file/files.

### How to install Git?
#### Windows
[installing git for windows link](https://gitforwindows.org/)
#### Mac

```
brew install git
```

#### Ubuntu/Debian
```
sudo apt-get install git
```

#### Arch
```
sudo pacman -S git
```

#### OpenSuse 
```
sudo zypper install git
```
### How to configure Git?

When you first install git you need to add your username and email.
> For adding your username
```
git config --global user.name "username"
```

> For adding your email
```
git config --global user.email "email"
```

### Basic Commands For Git

1. git add
The git add command is used to add files to git, so that the git can track. When you add files through the git add command they get staged. You can think it as an intermediate stage between the start and the end of something. Syntax :-
```
# For adding one file

$ git add (filename)
# Adding multiple files
$ git add (filename1) (filename2)
# For adding all the files in a folder
$ git add *
```
2. git commit
Now you have staged and added your files with git add for finalising it you need to run the command git commit command. It must be followed by a -m tag, and you must type message in quotes, stating your commit (what are you committing) you can also type garbage, but it defeats the purpose of the -m tag.
```
# Commiting a file 
$ git commit -m "Commit Message"
# Example 2
$ git commit -m "Refactored the code"
```
3. Git pull
the git pull command downloads all the files present in the repository. It's advised to do a git pull before a push, as it can reduce merge conflicts. Imagine you and your friend are working a project (creating a website). You are working on the CSS whereas your friend is working on HTML. When have completed your part and planning to push to code to the repository, your friend have already made some changes to the files. But these changes are not present in your system, hence for downloading the changes made by your friend you need to do a git pull.
```
# Git pull command
$ git pull
```
4. Git push
The git push command sends the changes and new files to the repository. Now if you are asking what is repository, consider as a online folder where all your colleagues contribute their work.
```
# Git push command
$ git push
```
5. Git status
The git status command shows your tracked, untracked, which files differ from the working tree.
```
# git status command
$ git status
```
When you do a git push, git will ask for your credentials. There are a few ways in which you can authenticate it, my preferred way is to use SSH keys. I will be releasing a new article based on this, so do follow me.

### Comments 
I don't have comments as I don't want to manage them. You can however contact me at the below address if you want to.

 - [ Email singhvikal891@gmail.com](mailto:singhvikal891@gmail.com)



### License 

[The contents of this site is licensed under a Creative Commons Attribution-ShareAlike 4.0 International License.](https://creativecommons.org/licenses/by-sa/4.0/)

[=> Return to Homepage](https://vikmenace.github.io)
