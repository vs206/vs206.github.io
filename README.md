# [Web Page](https://vs206,is-a.dev/)

This portfolio website build using [Hugo](https://gohugo.io/) using the [PaperMod](https://adityatelange.github.io/hugo-PaperMod/) theme.

#### Setup 


Setting up Hugo was surprisingly easy. I followed the official documentation on the Hugo website, which was very clear and helpful. Here are the steps I took:

- I downloaded and installed Hugo on my computer using **winget** on windows obviously.
- But if you use Linux or MacOS don't worry be happy and you can easily install it with package manager. Just follow the instructions on the site.


- I created a new site using the **hugo new site** command. 

```yaml
$ hugo new site <name>
```

- This created a folder with some basic files and folders for my site.

- I am using the **coder** theme for my website. I downloaded the theme I liked and cloned it into the themes folder. You can add it to as submodule with just a single command.



- I configured my site using the **config.toml** or **hugo.toml** file in the root folder of my site.
- This file contained some global settings for my site, such as the **title, language, base URL**, etc.
- I also customized some theme-specific settings, such as the color scheme, fonts, layout, etc.

I created some content for my site using the **hugo new filename** command. 
This created some Markdown files in the content folder of my site, with some predefined front matter (frontmatter) such as the title, date, categories, tags, etc. 
I edited these files with my favorite text editor and wrote my content.

```yaml
$ hugo new filename
```

- I built my site using the hugo command. This generated a public folder with all the HTML files and assets for my site.
- while making the site and writing and changing codes you can directly see the changes and it will look on the page using **hugo server** command.
- 
```yaml
$ hugo server
```
- I deployed my site using the **hugo deploy** command. This uploaded the public folder to a web server of my choice.
-  I used **Cloudflare Pages**, a free and easy-to-use hosting service that integrates well with Hugo.
That’s it! 

My website was live and ready to be visited by anyone.
You can visit it. 
