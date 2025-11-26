+++ 
date = 2025-09-18
title = "How I Built My Website Using Hugo"
description = "Lab Hugo Blog"
slug = ""
authors = ["Sophia"]
tags = ["Blog", "Hugo"]
categories = ["Lab"]
externalLink = ""
series = []
+++

---
# How I Built My Hugo Website  
*(Blog Setup)*

In this post, I document the complete process I followed to create my personal website using **Hugo**, a static site generator. This includes installation, theme setup, writing content, and deployment.  
These notes are based on the class material from the HCI course from the Master VAR.

---
## Why Create a Website?

Creating a website is more than a technical exercise:

- It allows me to **share knowledge** with the world.  
- It's a place to **tell my story** to employers.  
- It showcases **professionalism and maturity** in documentation.  
- It becomes a living **portfolio** of all my projects.

Documentation is crucial:
- write what worked and what didn't  
- keep notes  
- include screenshots, videos, snippets  
- **don't try to make it perfect**, just make it work first :contentReference[oaicite:2]{index=2}

---
## Installing Hugo

Hugo runs on macOS, Linux, Windows, BSD - anything that supports Go. I runned mine on Microsoft WSL2

### Installing on Linux  
```bash
sudo snap install hugo
```

---
## Creating My Hugo Site

To create a new site:

```bash
hugo new site my-website
```

This generates the full folder structure automatically (config, content, layouts, etc.)
Then I navigated into the website folder:

```bash
cd my-website
```

---
## Adding a Theme (Hugo Coder)

Hugo sites can be fully customized through themes, which define structure, layouts, and styles.

I chose **hugo-coder**.

Before downloading, I ensured git was installed:

```bash
sudo apt install git
```

Then I added the theme as a submodule:

```bash
git init
git submodule add https://github.com/luizdepra/hugo-coder.git themes/hugo-coder
```

Many themes require **Hugo Extended**.
After installing, I verified the content of the theme:

```bash
cd themes/hugo-coder
ls -ltr
```

I copied the example site to my root folder.
This gave me a working structure including the config.toml template.

---
## Editing the Website Configuration

To edit main settings, I modified the file **config.toml** using VSCode.

The config file controls:
- site title
- URLs
- languages
- menus and more

---
## Creating Blog Posts

To create a new blog post:

```bash
hugo new posts/my-first-post.md
```

By default:

```md
draft = true
``` 

Set it to:

```md
draft = false
``` 

to publish it.

---
## Running the Website Locally

To preview the website:

```bash
hugo server -D
```

Then open:

```bash
http://localhost:1313/
```

Every change updates automatically in real time.
This is extremely convenient during development.

---
## Deployment - Publishing to GitHub Pages

I deployed my site using GitHub Project Pages - a site tied to a specific repo.

Steps:
### 1. Create a GitHub repo

I created a *project* repository for my website.

### 2. Add all files

```bash
git add .
git commit -m "First commit"
git push
```

If GitHub login gives an error, update scopes as required (token settings)

### 3. Create GitHub Actions workflow

Inside my repository:

```bash
.github/workflows/hugo.yml
```

I pasted the recommended Hugo build + deploy action from Hugo's docs

### 4. Trigger Deployment

After pushing, I went to: GitHub, Actions, and ran the Deploy workflow.

### 5. Set Build Output

In GitHub: Settings, Pages, Branch: main

Finally, I set the site URL:

```toml
baseURL = "http://SophBG.github.io/MasterVAR-HCI-blog"
```

After this, the website was live online.

---
## Final Result

My site is now online, automatically updated via GitHub Actions, fast thanks to Hugo, and structured cleanly because everything is based on Markdown and static files.

This workflow is simple, robust, and perfect for maintaining a professional portfolio for the HCI course and future projects.

The project can be found here:
https://github.com/SophBG/MasterVAR-HCI-blog