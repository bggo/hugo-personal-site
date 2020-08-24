---
title: "Deploying a personal website 2/4"
date: 2020-08-24T15:41:50-03:00
draft: false
---

## Part 2 of 4 - Welcome to Hugo!

After many years without writing in a blog, not having a space to call it mine, I have decided to understand what some tech fellows were using to handle personal pages and tech blogs. I must let you know I did not go in any deeper research, I was willing to find something easy to manage, powerful, modern but at the same time able to give some fun while learning.

This are some of the blogs I spy and get inspired on:

* https://gomex.me/
* https://www.fernandoike.com/
* https://ffrizzo.com/
* https://gohugo.io/showcase/forestry/
* https://gohugo.io/showcase/linode/ 

Let's get started: /o/

## Installing Hugo

As Hugo is multi platform, find [here](https://gohugo.io/getting-started/installing) the best way so you can install it. In my case, I just used homebrew: 
``` commandline
brew install hugo
```
Then just try:

``` commandline
hugo version
```

```
Hugo Static Site Generator v0.74.2/extended darwin/amd64 BuildDate: unknown
```

## Creating a new Site 

So now Hugo framework is installed and you can use it. To create a site new run:

``` commandline
hugo new site my-new-site
```

```
Congratulations! Your new Hugo site is created in $PATH/my-new-site.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation:
```

This will generate the folder my-new-site with all Hugo files inside:

``` commandline
ls -l my-new-site
```

```
total 8
drwxr-xr-x  3 user  staff  96 Aug 20 11:24 archetypes
-rw-r--r--  1 user  staff  82 Aug 20 11:24 config.toml
drwxr-xr-x  2 user  staff  64 Aug 20 11:24 content
drwxr-xr-x  2 user  staff  64 Aug 20 11:24 data
drwxr-xr-x  2 user  staff  64 Aug 20 11:24 layouts
drwxr-xr-x  2 user  staff  64 Aug 20 11:24 static
drwxr-xr-x  2 user  staff  64 Aug 20 11:24 themes
```

For now, you will need to understand some folder structure. Read [this](https://gohugo.io/getting-started/directory-structure/#directory-structure-explained) to get yourself familiarized! 

I'll cover in the next few steps, how to set up a theme, add a page/post and how to serve it locally.

## Installing a new theme

Hugo has lots of cool [themes](https://themes.gohugo.io/) and to start, you will need to pick one. I've selected [Toha](https://themes.gohugo.io/toha/), looks clean and nice!

Make sure you are in your new website folder than:

``` commandline
cd my-new-site 
git init 
```
```
Initialized empty Git repository in $PATH/my-new-site/.git/
```
``` commandline
git submodule add https://github.com/hossainemruz/toha.git themes/toha
```
```
Cloning into '$PATH/my-new-site/themes/toha'...
remote: Enumerating objects: 15, done.
remote: Counting objects: 100% (15/15), done.
remote: Compressing objects: 100% (14/14), done.
remote: Total 1214 (delta 1), reused 4 (delta 0), pack-reused 1199
Receiving objects: 100% (1214/1214), 24.89 MiB | 10.88 MiB/s, done.
Resolving deltas: 100% (663/663), done.
```

This will download the toha theme to your Hugo installation in Themes folder, have a look:

``` commandline
ls -l themes/toha
```
```
total 32
-rw-r--r--  1 user  staff  1074 Aug 20 11:25 LICENSE
-rw-r--r--  1 user  staff  6691 Aug 20 11:25 README.md
drwxr-xr-x  3 user  staff    96 Aug 20 11:25 archetypes
drwxr-xr-x  5 user  staff   160 Aug 20 11:25 exampleSite
drwxr-xr-x  4 user  staff   128 Aug 20 11:25 images
drwxr-xr-x  7 user  staff   224 Aug 20 11:25 layouts
drwxr-xr-x  3 user  staff    96 Aug 20 11:25 static
-rw-r--r--  1 user  staff   472 Aug 20 11:25 theme.toml
```

Say Hugo that you will use this theme by adding theme key to the config file:

``` commandline
echo "theme = \"toha\"" >> config.toml
```

Once your set, let's give Hugo a try. 

``` commandline
hugo server 
```

```
                   | EN  
-------------------+-----
  Pages            | 14  
  Paginator pages  |  0  
  Non-page files   | 12  
  Static files     | 46  
  Processed images |  0  
  Aliases          |  0  
  Sitemaps         |  1  
  Cleaned          |  0  

Built in 50 ms
Watching for changes in $PATH/my-new-site/{archetypes,content,data,layouts,static,themes}
Watching for config changes in $PATH/my-new-site/config.yaml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at (bind address 127.0.0.1)
Press Ctrl+C to stop
```

Open your browser and go to: http://localhost:1313/

## Hugo Server

And this is the magical part, you do not need any apache, nginx or other web server apart. Hugo Framework already offers its own [micro web server](https://gohugo.io/commands/hugo_server/#hugo-server) so we do not need any specific configuration to run it.

Notice that once Hugo server runs, it renders all the configuration files into the static final files in the public directory, following the templates. You will be able to access in http://localhost:1313/ as we did in the last step.

## Setup minimal configs

To make all the soft configuration in Hugo use a file called: **config.toml**. Ohhh no, another markdown language to deal. Ok, no rush, let's just setup Hugo to understand the main config file in yaml!

First prepare a simple config file in yaml! You can just base yours on the theme example: 

``` commandline
vim config.yaml
```
``` yaml
baseURL: http://example.org/
languageCode: en-us
title: "Toha"
theme: "toha"
```

Then just ask HUGO to set the main config file as config.yaml

``` commandline
rm config.toml

hugo server
```

Lets just add some more keys in the configuration file and make it yaml! Get the example from Toha:

``` commandline
vim config.yaml
```
Paste all the configs:
``` yaml
baseURL: http://example.org/
languageCode: en-us
title: "Toha"
theme: "toha"

paams:
  enableBlogPost: true
  author:
    name: "Your name"

```

Done.

By reading this config file you will understand that this theme has a lot of options you can customize just changing values. Information and background, social networks and more! Explore a little, have some fun then try it out!

``` commandline
hugo server
```

## First Page/Post

By this time, if you read the folder structure page, you know that all the content like pages or posts are placed in the content/ folder.

In Toha theme, we already have a folder called posts which will handle all our blog posts, but you can add any page outside of it too. So, to create a new blog post run:

``` commandline
hugo new posts/my-new-post.md
```
```
$PATH/content/posts/my-new-post.md created
```

the file content/posts/my-new-post have been created, let's have a look:

``` commandline
cat content/posts/my-new-post
```
```
---
title: "My New Post"
date: 2020-08-20T11:09:57-03:00
draft: true
---
```

You can modify the title and date if you want but the main important information in this header is the draft tag. While draft stills on true, content will not be rendered into the public folder. Let's understand.

After adding the page run:

``` commandline
hugo server
```
Try to access your new page going to: http://localhost:1313/posts/my-new-post

Page will not be available, because it is set as draft. You can use one function of our web server to see all draft pages by adding -D.

``` commandline
hugo server -D
```

Now, you can see all your draft content!: http://localhost:1313/posts/my-new-post

As a next step, look into public folder structure. 

As the content is tagged as draft, hugo did not render any md file in html. 

```
ls -l public
total 40
-rw-r--r--  1 user  wheel  3464 Aug 24 16:09 404.html
drwxr-xr-x  5 user  wheel   160 Aug 24 16:02 assets
drwxr-xr-x  5 user  wheel   160 Aug 24 16:09 categories
-rw-r--r--  1 user  wheel  4507 Aug 24 16:09 index.html
-rw-r--r--  1 user  wheel   467 Aug 24 16:09 index.xml
-rw-r--r--  1 user  wheel   355 Aug 24 16:09 sitemap.xml
drwxr-xr-x  5 user  wheel   160 Aug 24 16:09 tags
```

Here we can see there is no html rendered for our posts structure. Set draft key to false in the post file: 


``` commandline
vim content/posts/my-new-post.md
```
```
---
title: "My New Post"
date: 2020-08-20T11:09:57-03:00
draft: false
---
```

Run hugo so your pages can be rendered.

``` commandline
hugo
```

```
                   | EN
-------------------+-----
  Pages            | 10
  Paginator pages  |  0
  Non-page files   |  0
  Static files     | 34
  Processed images |  0
  Aliases          |  3
  Sitemaps         |  1
  Cleaned          |  0
```

Hugo get all the pages/posts not in draft and renders.
``` commandline
ls -l public
```

```
total 40
-rw-r--r--  1 user  wheel  3452 Aug 24 16:29 404.html
drwxr-xr-x  5 user  wheel   160 Aug 24 16:02 assets
drwxr-xr-x  5 user  wheel   160 Aug 24 16:09 categories
-rw-r--r--  1 user  wheel  4695 Aug 24 16:29 index.html
-rw-r--r--  1 user  wheel   783 Aug 24 16:29 index.xml
drwxr-xr-x  6 user  wheel   192 Aug 24 16:29 posts
-rw-r--r--  1 user  wheel   636 Aug 24 16:29 sitemap.xml
drwxr-xr-x  5 user  wheel   160 Aug 24 16:09 tags
```

``` commandline
ls -l public/posts
```

```
total 24
-rw-r--r--  1 user  wheel  4729 Aug 24 16:29 index.html
-rw-r--r--  1 user  wheel   813 Aug 24 16:29 index.xml
drwxr-xr-x  3 user  wheel    96 Aug 24 16:29 my-new-post
drwxr-xr-x  3 user  wheel    96 Aug 24 16:29 page
```

Now we are good to go! 

```
hugo server
```

You can see all the content you publish! =D

Hope you enjoyed this journey. See you in the next chapter where we are going to set yor Firebase Hosting to publish our site. Stay tunned!

### References:

* https://gohugo.io/documentation/
* https://www.youtube.com/watch?v=ResipmZmpDU&feature=youtu.be
* https://gohugo.io/hugo-modules/theme-components/
* https://gohugo.io/getting-started/installing/
* https://gohugo.io/getting-started/configuration/
* https://gohugo.io/content-management/organization/

Read this article on [Medium](https://medium.com/@brunogurgel/deploying-a-personal-website-2-4-b2f451b9c62c)