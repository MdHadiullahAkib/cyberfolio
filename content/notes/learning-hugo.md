+++
title = 'Learning Hugo'
date = 2026-05-17T13:01:10+06:00
tags = ["note", "website"]
type = "notes"
topic = "hugo"
summary = "Hugo static site generator is a must to maintain blog."
+++

Hugo static site generator is a must to maintain blog. Using Hugo one can manage a blog, note or portfolio website easily.

<!--more-->

# About Hugo

Hugo is one of the most popular open-source static site generators. With its amazing speed and flexibility, Hugo makes building websites fun again. It is open-source and free to use. Hugo has a large and active community. If you have questions or need help, you can ask in the [Hugo forums](https://discourse.gohugo.io/).  
Check out their official [website](https://discourse.gohugo.io/) if you are interested.

## How It all works

Basically markdown is a lightweight markup language for creating formatted text using a plain-text editor. John Gruber created Markdown in 2004 as an easy-to-read markup language. It is widely used for note taking, many of you must have heard of the popular note taking app [obsidian](https://obsidian.md/).

As markdown is a markup language and uses symbles to format its documents it is converted/rendered in html. After that you can add `css`, `javascript` to make it look good.

That is exactly what hugo does. It creates files, folders structure and converts, renders, builds and formates the markdown file and puts all together to make a website.

## Installing Hugo

Installing hugo is going to be different depending on which operating system you are using.

### Prerequisites

[git](https://git-scm.com/),  [hugo](https://gohugo.io/installation/)
optional [go](https://go.dev/) language

If you are a windows user then you have to download the prebuilt binary, extract it and move it to `C:` directory and add the directory to path variable. Its a lots of work.  
But instead what you can do is use a package manager like [Chocolatey](https://chocolatey.org/), [Scoop](https://scoop.sh/), [Winget](https://learn.microsoft.com/en-us/windows/package-manager/) and run a single command.
`choco install hugo-extended`  
or  
`scoop install hugo-extended`  
or  
`winget install hugo-extended`  

If everything went well then check that you have it installed by running `hugo version` command.

Now to start a new project and add a theme run these commands
```bash
hugo new project quickstart
cd quickstart
git init
git submodule add https://github.com/gohugo-ananke/ananke themes/ananke
echo "theme = 'ananke'" >> hugo.toml
hugo server
```
the first line creates a new project/folder named quickstart   
the `cd foldername` changes the directory  
to add a theme you have to start a git repo using `git init`  
check out different themes available to install in [hugo themes](https://themes.gohugo.io/) and run `git submodule add 'theme link'`  
after that run `hugo server` to build and view the website on your [localhost:1313](localhost:1313) link


## My pipeline

I have uploaded all my cyberfolio codes in [this github repo](https://github.com/MdHadiullahAkib/cyberfolir)

For deploying my website I have made this bash script

```bash

#!/etc/profiles/per-user/akib/bin/bash

echo "Changing Directory"

cd ~/HugoSites/cyberfolio

echo "Clearing public directory"

rm -r public/*

echo "building site"

hugo

git add .

read -p 'Enter commit name: ' commit

git commit -m "$commit"

echo "pushing to remote repo"

git push -u origin main

echo "spliting public directory"

git subtree split --prefix public -b site-deploy

git push origin site-deploy:deploy --force

git branch -D site-deploy

echo "Deployed succesfully"
```
