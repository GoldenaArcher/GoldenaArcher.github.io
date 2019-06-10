---
title: NexT Upgrade
date: 2019-06-09 17:42:43
tags: [Hexo, NexT, GitHub]
categories: 
- Hexo
- NexT
---

<img src="https://i.loli.net/2019/06/09/5cfcda11a511617155.jpg" width=400>

Technically, this article is not upgrading the NexT theme, rather, it's exploring the already setup features of the theme.

<!-- more-->

If not specified, all the changes made are under `/themes/next/_config.yml`. Just use `ctrl+f` to find the corresponding section, and modified the section of code.

---

# Symbol Count

Basically, I just followed the instructions from the [project](<https://github.com/theme-next/hexo-symbols-count-time>). Authors have explained it pretty well.

Here's the quote from the project:

>Symbols count and time to read of articles.
>
>Better than [`hexo-reading-time`](https://github.com/ierhyna/hexo-reading-time) and faster than [`hexo-worcount`](https://github.com/willin/hexo-wordcount). No external dependencies.

## Installation

```
$ npm install hexo-symbols-count-time --save
```

## Configuration

1. Edit the `_config.yml` of Hexo rather than NexT, use `ctrl+f` to find whether `symbols_count_time` is in the configuration file. If so, edit it, otherwise, just add this section of code at the end of file:

   ```
   symbols_count_time:
     symbols: true
     time: true
     total_symbols: true
     total_time: true
     exclude_codeblock: false
   ```

   Most likely `symbols_count_time` is not here or is commented out, otherwise, the function should already be on the site.

2. Edit `themes/next/_config.yml` as following:

   ```
   symbols_count_time:
     separated_meta: true
     item_text_post: true
     item_text_total: false
     awl: 4
     wpm: 275
     suffix: mins.
   ```

3. Last, rerun the server:

   ```
   # If you don't see any changes, and most likely you will not see the changes...
   $ hexo clean && hexo g && hexo s
   ```

For more detailed information, read the instructions from the project.

---

# Links

```
# Blog rolls
links_icon: link
links_title: Links
links_layout: block
#links_layout: inline
links:
  Name_of_the_site: https://name_of_the_link.com
```

---

# Social Links

```
# Social Links
# Usage: `Key: permalink || icon`
# Key is the link label showing to end users.
# Value before `||` delimeter is the target permalink.
# Value after `||` delimeter is the name of FontAwesome icon. If icon (with or without delimeter) is not specified, globe icon will be loaded.
social:
  GitHub: https://github.com/GoldenaArcher || github
  #E-Mail: mailto:yourname@gmail.com || envelope
  #Weibo: https://weibo.com/yourname || weibo
  #Google: https://plus.google.com/yourname || google
  #Twitter: https://twitter.com/yourname || twitter
  #FB Page: https://www.facebook.com/yourname || facebook
  #VK Group: https://vk.com/yourname || vk
  #StackOverflow: https://stackoverflow.com/yourname || stack-overflow
  #YouTube: https://youtube.com/yourname || youtube
  #Instagram: https://instagram.com/yourname || instagram
  #Skype: skype:yourname?call|chat || skype
```

---

# Avatar

```
# Sidebar Avatar
avatar:
  # In theme directory (source/images): /images/avatar.gif
  # In site directory (source/uploads): /uploads/avatar.gif
  # You can also use other linking images.
  url: put url here
  # If true, the avatar would be dispalyed in circle.
  rounded: false
  # The value of opacity should be choose from 0 to 1 to set the opacity of the avatar.
  opacity: 1
  # If true, the avatar would be rotated with the cursor.
  rotated: false
```

---

# Since

```
footer:
  # Specify the date when the site was setup. If not defined, current year will be used.
  since: 2019
```

---

# View #

Doesn't want to translate since I'm not sure how I did it... but the [instruction](<https://github.com/theme-next/hexo-theme-next/blob/master/docs/LEANCLOUD-COUNTER-SECURITY.md>) is very clear and can be easily to set up for free.

---

# Visitors

Just set `busuanzi` function to true:

```
# Show Views / Visitors of the website / page with busuanzi.
# Get more information on http://ibruce.info/2015/04/04/busuanzi
busuanzi_count:
  enable: true
  total_visitors: true
  total_visitors_icon: user
  total_views: true
  total_views_icon: eye
  post_views: true
  post_views_icon: eye
```

---

