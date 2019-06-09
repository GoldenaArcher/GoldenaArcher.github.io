---
title: Build GitHub Page with Hexo
date: 2019-06-07 00:16:39
tags: [Hexo, GitHub]
categories: [Hexo]
---

I have set up io site for GitHub for a while, have not really play with the Git page anyway. However, since I started to study more and more, I feel like to have some place supports Markdown so that I can organize my notes is important. Eventually, my previously set Git page came to my mind.

Hence, I spent some time to set it up on my local machine, and decided to write it down in case I need to use it in the future. The original template is not bad, but limited in functions, so I changed to [NexT](https://theme-next.org/).

<!-- more -->

---

# Environment

I used __Windows__!

The [documentation of Hexo](<https://hexo.io/docs/index.html>) has stated pretty clear that the minimum requirements for installing Hexo, which are:

> - [Node.js](http://nodejs.org/) (Should be at least nodejs 6.9)
> - [Git](http://git-scm.com/)

NodeJs is very easy to install. Just go to the [official website](http://nodejs.org/), download the `.msi` file of the latest stable version.

Installing git is also very easy on the Windows system. Also going to the [official website](<https://git-scm.com/downloads>), and download the latest stable version based on the system of the pc. 

By following all of the steps, the environment should look something like:

```
# the environment of my pc
$ node -v
v8.12.0
$ git --version
git version 2.15.0.windows.1
```

---

# Install and Initialize Hexo

## Install Hexo

Following the instructions, the [documentation](<https://hexo.io/docs/index.html>) also states that:

> If your computer already has these, congratulations! Just install Hexo with npm:
>
> ```
> $ npm install -g hexo-cli
> ```

After that, npm will automatically download the required dependencies of Hexo. After downloading all of the files, Hexo is almost ready to use

---

## Initialize Hexo and Testrun

Change to the desired directory/location where the blog is going to be set up, then, just simply following these steps:

```
# assume the directory's name is blog
hexo init blog
$ cd blog
$ npm install
$ hexo g # or hexo generate
$ hexo s # or hexo server, the hexo server will run on localhost:4000
```

At this point, Hexo is ready on the local machine.

---

# Config and Deploy Hexo

## Config Info for Site

All the configurations need to be separated by space!

Follow the [Configuration](<https://hexo.io/docs/configuration.html>), add the title, description, and other variables for site. I changed settings in `_config.yml`:

```
# Site
title: GoldenaArcher's Note
subtitle:
description: GoldenaArcher's personal blog
keywords:
author: GoldenaArcher
language:
timezone:

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: https://goldenaarcher.github.io/
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:
```

By default, the language is English.

Have not played around the URL and subdirectory things, but I feel that's what the author of [theme hipaper](<https://github.com/iTimeTraveler/hexo-theme-hipaper>) did in his Hexo. The [sample theme](<https://itimetraveler.github.io/hexo-theme-hipaper/>) looks different than the [author's blog](<https://itimetraveler.github.io/>), though the links share the common header - `https://itimetraveler.github.io/`.

---

## <a name="config-info-for-github">Config Info for GitHub

Assume that public key for GitHub and/or RSA and/or username-password, and have been set up already. If not, following the [help page from GitHub](<https://help.github.com/en/articles/connecting-to-github-with-ssh>) to generate SSH key things. Then modifies `_config.yml`: 

```
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: https://github.com/GoldenaArcher/GoldenaArcher.github.io
```

---

## Deploy Hexo

Deploy is very easy. For the first timer, after done with config Hexo locally, using following commands on git bash to deploy the project:

```
$ npm install hexo-deployer-git --save
hexo d
```

Then everything will be deployed to the location configured under `deploy`.

In my case, after this step, the blog is synced with Git page as I only configured GitHub site.

It seems like by default Hexo upload files under `public` to deployment.

If git bash indicates `Permission denied (publickey).`, go back to [previous section](#config-info-for-github), and check with GitHub documentation.

## Common Hexo Command

```
# common shortcut
$ hexo n == hexo new
$ hexo g == hexo generate
$ hexo s == hexo server
$ hexo d == hexo deploy

# common combination
$ hexo d -g # generate deployment
$ hexo s -g # generate view

# the combination I find to be useful as well
$ hexo clean && hexo g && hexo d
$ hexo clean && hexo g && hexo s

# can be used to monitor files
$ hexo generate --watch
```

---

# Change Theme

The default I remember was landscape, not bad but needs more function. Then I switched to [hipaper](<https://github.com/iTimeTraveler/hexo-theme-hipaper>), but found some glitches on Table of Content set up by default. Finally I decided change to [NexT](https://theme-next.org/) which is the theme I am using right now.

## Download Theme

Make sure that the current directory is the home directory of the site, then using the command below:

```
$ git clone https://github.com/theme-next/hexo-theme-next themes/next
```

After download finishes, the theme is downloaded.

---

## Config Theme

Changes are still made in `_config.yml`. Search for `theme`, and made changes like:

```
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next
```

---

## Apply for Changes

```
# to see it locally
$ hexo clean && hexo g && hexo s
# deploy the project
$ hexo clean && hexo g && hexo d
```

AND... That's IT!

---

# Some Other Useful Config

At this point, it's pretty good, but the sections below might help to make the site better.

## <a name="add-tags">Add Tags

1. Create new tags directory under source folder, the code is listed below:

   ```
   $ mkdir tags
   $ cd tags
   $ hexo new page "tags"
   ```

2. Edit __index.md__ file, I did not change others, but add the following below:

   ```
   type: tags
   layout: tags
   ```

3. Edit _config.yml file as below:

   ```
   menu:
   	tags: /tags/
   ```

   Note that in my theme, the designer named it menu, but I've seen in other themes named as `nav`. 

4. Check the _config.yml of __hexo__

   ```
   # Directory
   tag_dir: tags
   ```

   Most likely the config file for hexo does not need to modify, but still check it just in case.

***

## Add Categories

Basically identical to [Add Tags](#add-tags), just need to change `tags` to `categories`.

1. Create new categories directory under source folder, the code is listed below:

   ```
   $ mkdir categories 
   $ cd categories 
   $ hexo new page "categories"
   ```

2. Edit __index.md__ file:

   ```
   type: categories
   layout: categories
   ```

3. Edit _config.yml file as below:

   ```
   menu:
   	categories: /categories/
   ```

4. Check the _config.yml of __hexo__

   ```
   # Directory
   category_dir: categories
   ```

---

## Change Templates

Add `categories` to the post template. Update the  `/scaffolds/post.md`:

```
---
title: {{ title }}
date: {{ date }}
tags: 
categories: 
---
```

Now, when type `$ hexo new filename` to generate new post, the default settings are:

```
---
title: test-post
date: 2019-06-09 16:15:03
tags:
categories:
---
```

Which saves some time from typing `categories:` all the time.

---

## Push All Files on GitHub

With the default deploy, Hexo only push files under `public` to GitHub. However, when working with different computers, there will be issues. Checking out another branch to keep all the files can save the trouble:

```
# make sure it's at the root
git init
git remote add origin site's_source_on_git   # add the repo to origin
git checkout -b hexo   		 # create a new branch
git add . 			 # add all the changes
git commit -m "commit"  # commit all changes
git push origin hexo   # push all changes to branch hexo
```





---

# Reference

[How to use Hexo and deploy to GitHub Pages](<https://gist.github.com/btfak/18938572f5df000ebe06fbd1872e4e39#2-create-a-project-for-your-github-pages>)

[基于Hexo+Coding+Github搭建个人博客的全过程](<https://11.tt/posts/2018/set-up-hexo-with-coding-and-github/>)

