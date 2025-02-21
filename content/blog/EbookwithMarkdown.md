---
title: 'Ebook with Markdown'
date: 2023-09-01T15:52:24+05:30
authors: ["Vikal Singh"]
description: ""
tags: ["Bspwm","dmenu","st","linux","sxhkd","alacritty","polybar"]
categories: [""]
series: [""]
url: ""
slug: ""
externalLink: ""
featuredImage: ""
disableComments: true
draft: false
---

Pandoc is a great tool for converting a file in one markup format into another. This means we can use it to convert a file written in Markdown into an EPUB file that is supported by many e-readers.

Lets start by writting a very simple markdown file called example_ebook.md.


```yaml

---
title:
- type: main
  text: Example Ebook
- type: subtitle
  text: An Ebook created from a Markdown file
creator:
- role: author
  text: David Sadler
publisher: Published by myself
---

This is an introduction.

# Chapter 1

This is the first paragraph of chapter 1.

This is the second paragraph of chapter 1.

Below is a list.

- Item One
- Item Two
- Item Three

# Chapter 2

This is the first paragraph of chapter 2.

This is the second paragraph of chapter 2.

# Chapter 3

This is the first paragraph of chapter 3.

This is the second paragraph of chapter 3.
```

Note that the file begins with a YAML metadata block that starts and ends with three hyphens (---). This allows you to specify EPUB metadata such as the title and author.

Converting this to EPUB is done by running pandoc.

```yaml
$ pandoc example_ebook.md -t epub3 --toc -o example_ebook.epub
```

There are several options that need to be passed to pandoc.

- example_ebook.md - This argument is the file that you are converting.
- also -t epub3 - Set the output format to be EPUB v3 book.
- and --toc - Include a table of contents in the output document. This will be derived from the H1 headers in the markdown.
- this -o example_ebook.epub - Tell pandoc to output the conversion to the named file instead of stdout.

You can now copy the file example_ebook.epub to any device that supports the format or use one of the many software readers such as Calibre. However, if you wish to read this on a Kindle device you will need to convert it to the Mobi format.

Amazon provides a command line tool called KindleGen that can convert our EPUB file into the Mobi format. After downloading the tool just run it as shown below.


```yaml
$ kindlegen example_ebook.epub
```

This will create a file called example_ebook.mobi that you can copy to your Kindle to read.

### Comments

I don't have comments as I don't want to manage them. You can however contact me at the below address if you want to.

 - [ Email singhvikal891@gmail.com](mailto:singhvikal891@gmail.com)



#### License 

[The contents of this site is licensed under a Creative Commons Attribution-ShareAlike 4.0 International License.](https://creativecommons.org/licenses/by-sa/4.0/)

[=> Return to Homepage](https://vikmenace.github.io)
