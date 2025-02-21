---
title: "Why Hugo"
date: 2023-06-21T15:37:27+05:30
authors: ["Vikal Singh"]
description: ""
tags: ["why hugo?","hugo"]
categories: [""]
series: [""]
externalLink: ""
featuredImage: ""
disableComments: true
draft: false
---
### Introduction

Hello, and welcome to my blog! I'm very excited to share my journey of creating this website using Hugo, a fast and flexible static site generator. I always wanted to write blogs as I have a passion for writing. I never knew that setting up a blog page would be this easy. Static Site Generators (SSGs) have made it easier for many people including newbies as well as professionals in their day-to-day life. In this post, I'll tell you why I chose Hugo, how I set it up, and what I learn in the process.

### Why Hugo?

So I always wanted to have my own website, but I was intimidated by the complexity and cost of building and hosting one. There are many SSGs available like zola, ssg5 and hugo. I chose to go with hugo.

I first started learning web development directly with the basic**HTML, CSS** and **JS**. I created and i got so much into web that I started making different pages with different content on them. I createat it and after that i started updating it then I feel that making is not important, the important is to maintain it. Then after many attempts i maintained it. 
But Then a guy suggest me Hugo, but it took me some time to actually start using it. Here is my first attempt at it. Hugo is a static site generator that lets you create beautiful websites from plain text files. The content is written in Markdown, a simple and easy-to-learn markup language, and Hugo converts it into HTML pages that you can upload to any web server.

Hugo has many advantages over other static site generators. It’s very fast, generating thousands of pages in seconds. It’s very flexible, allowing you to customise every aspect of your site with themes and templates. It’s very powerful, supporting features like taxonomies, menus, pagination, shortcodes, and more. And it’s very easy to use, with a simple and intuitive command-line interface.

### Setup

Setting up Hugo was surprisingly easy. I followed the official documentation on the Hugo website, which was very clear and helpful. Here are the steps I took:

1. I downloaded and installed Hugo on my computer using `winget`.
2. I created a new site using the `hugo new site` command. This created a folder with some basic files and folders for my site.

```yaml
$ hugo new site <name>
```

3. I am using the `coder` theme for my website. I downloaded the theme I liked and cloned it into the `themes` folder.

```yaml
$ git submodule add https://github.com/luizdepra/hugo-coder.git themes/hugo-coder
```
4. I configured my site using the `config.toml` file in the root folder of my site. This file contained some global settings for my site, such as the title, language, base URL, etc. I also customized some theme-specific settings, such as the color scheme, fonts, layout, etc.
5. I created some content for my site using the `hugo new` command. This created some Markdown files in the `content` folder of my site, with some predefined front matter (frontmatter) such as the title, date, categories, tags, etc. I edited these files with my favorite text editor and wrote my content.
   
```yaml
$ hugo new filename
```

6. I built my site using the `hugo` command. This generated a `public` folder with all the HTML files and assets for my site.
7. I deployed my site using the `hugo deploy` command. This uploaded the `public` folder to a web server of my choice. I used Cloudflare Pages, a free and easy-to-use hosting service that integrates well with Hugo.

That's it! My website was live and ready to be visited by anyone.

### Learnings

Creating this website with Hugo was a fun and rewarding experience. I learned a lot about web development, Markdown, HTML, CSS, and more. Here are some of the things I learned:

- How to structure and organize my content using folders and files
- How to format and style my content using Markdown syntax
- How to add images, videos, links, tables, lists, etc. to my content using Markdown or HTML
- How to use shortcodes to insert dynamic content or functionality into my content
- How to use taxonomies to categorize and tag my content
- How to use menus to create navigation for my site
- How to use partials and templates to reuse common elements across my site
- How to use live reloading to preview changes in real time

Having set up my site now I can't wait to post more blogs. See you there.


#### Links
I don't have comments as I don't want to manage them. You can however contact me at the below address if you want to.

 - [Email singhvikal891@gmail.com](mailto:singhvikal891@gmail.com)



#### License 

[The contents of this site is licensed under a Creative Commons Attribution-ShareAlike 4.0 International License.](https://creativecommons.org/licenses/by-sa/4.0/)

[=> Return to Homepage](https://vikmenace.github.io)
