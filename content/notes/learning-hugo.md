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

## Understanding Hugo

### Template

`{{ $v1 := 6}}` variable declare

(.) represents current context.

Within a range or with block you can access the context passed into the template by prepending a dollar sign ($) to the dot:

```
<h2>{{ .Title }}</h2>
{{ with "foo" }}
  <p>{{ $.Title }} - {{ . }}</p>
{{ end }}
```
Double quotes for interpreted string literals `{{ print "Hello world\u0021" }} → Hello world!`

backticks for row string literals ```{{ print `Hello world\u0021` }} → Hello world\u0021 ```

#### pipes

These pairs are equivilant
```
{{ strings.ToLower "Hugo" }} → hugo
{{ "Hugo" | strings.ToLower }} → hugo

{{ strings.TrimSuffix "o" (strings.ToLower "Hugo") }} → hug
{{ "Hugo" | strings.ToLower | strings.TrimSuffix "o" }} → hug

{{ mul 6 (add 2 5) }} → 42
{{ 5 | add 2 | mul 6 }} → 42
```
**Remember that the piped value becomes the final argument to the function or method to which you are piping.**

With variables that represent a map or object, **chain identifiers (connect with .)** to return the desired value or to access the desired method.
```
{{ $map := dict "a" "foo" "b" "bar" "c" "baz" }}
{{ $map.c }} → baz

{{ $homePage := .Site.Home }}
{{ $homePage.Title }} → My Homepage

```

#### functions

Takes one/more arguments and returns a value. Frequently used functions have aliases. `{{ $ total := add 1 2 3 4}}`

#### methods

Associated with and object, takes zero or more arguments and either returns a value or performs an action.

Page object has Date, Params, Title, etc methods. 
```
{{ .Site.Title }} → My Site Title
{{ .Page.Title }} → My Page Title
```

if the context is Page object then 
```
{{ .Title }} → My Page Title
```

if the methode take argument then
```
{{ $page := .Page.GetPage "/books/les-miserables" }}
{{ $page.Title }} → Les Misérables
```

#### comments

```
{{/* This is an inline comment. */}}

{{/*
This is a block comment.
*/}}

{{- /*
This is a block comment with
adjacent whitespace removed.
*/ -}}
```

#### include partials

```
{{ partial "google_analytics.html" . }}
{{ partial "opengraph" . }}
{{ partial "breadcrumbs.html" . }}
{{ partialCached "css.html" . }}
```

#### Params method on Site object.

```hugo.toml
baseURL = 'https://example.org'
title = 'ABC Widgets'
[params]
  copyright-year = '2023'
  subtitle = 'The Best Widgets on Earth'
  [params.author]
    email = 'jsmith@example.org'
    name = 'John Smith'
  [params.layouts]
    rfc_1123 = 'Mon, 02 Jan 2006 15:04:05 MST'
    rfc_3339 = '2006-01-02T15:04:05-07:00'
```

Access the custom site parameters by chaining the identifiers:

```
{{ .Site.Params.subtitle }} → The Best Widgets on Earth
{{ .Site.Params.author.name }} → John Smith

{{ $layout := .Site.Params.layouts.rfc_1123 }}
{{ .Site.Lastmod.Format $layout }} → Tue, 17 Oct 2023 13:21:02 PDT
```

#### Params method on Page object

In font matter:

```
+++
date = 2023-10-17T15:11:37-07:00
title = 'Annual conference'
[params]
  display_related = true
  key-with-hyphens = 'must use index function'
  [params.author]
    email = 'jsmith@example.org'
    name = 'John Smith'
+++
```

Access the custom fields by chaining the identifiers when needed:

```
{{ .Params.display_related }} → true
{{ .Params.author.email }} → jsmith@example.org
{{ .Params.author.name }} → John Smith
```

### Lookup Order

Lookup order is just hugo deciding which template to follow to design a specific page.

1. The Strict Path Match (Highest Priority)Hugo looks for a template folder that exactly matches the physical directory nesting of the content
    - layouts/store/shoes/single.html
    - layouts/store/shoes/page.html
 
3. The Type/Layout Parameter Match If a strict path layout doesn't exist, Hugo looks for an explicit classification. This is either inferred by the top-level section (store) or explicitly declared via type or layout variables in the front matter
    - layouts/store/single.html
    - layouts/store/page.html

5. The Root Fallback (Lowest Priority)If no directories match the path or type parameters, Hugo drops back to the absolute root of your layouts/ directory
    - layouts/single.html
    - layouts/page.html


## Now Challenge myself to understand everything that I have used to make this website.
