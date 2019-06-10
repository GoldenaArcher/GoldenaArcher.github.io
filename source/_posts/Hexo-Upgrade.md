---
title: Hexo Upgrade
date: 2019-06-10 15:49:16
tags: [Hexo, NexT, GitHub]
categories:
- Hexo
---

<img src="https://i.loli.net/2019/06/10/5cfe16d677f5b30473.png">

In the [NexT Upgrade](<https://goldenaarcher.github.io/2019/06/09/NexT-Upgrade/>), I list some upgrades can be done to create a better looking and more powerful site. During the process of digging, I also found some features or issues that's not related to the theme NexT, but Hexo itself. Therefore, I moved out of the sections that's only related to Hexo here.

The only file needs to be modified here is the `_config.yml` and other files under root directory.

<!--more-->

# Sub Directory for Posts

I didn't realize the directories under `categories` were not properly organized. What I wanted is:

```
|-GitHub
|	|-Git bash
|	|-Markdown
|-Hexo
|	|-NexT
|-Maven
```

However, it turned out to be like:

```
|-GitHub
|-GitHub/Git Bash
...
```

And the problem is that I did not properly organized `categories` in the source file, the proper way of constructing level of directory is using __dash(-)__:

```
categories: 
- Hexo
- NexT
```

Then, the structure became:

```
|-Hexo
|	|-NexT
```

Rather than `Hexo/NexT`

------

# Order Posts by Update Time

Change the `order_by` to `-updated`, now the articles listed in the home page is ordered by time updated rather than time created.

```
# Home page setting
# path: Root path for your blogs index page. (default = '')
# per_page: Posts displayed per page. (0 = disable pagination)
# order_by: Posts order. (Order by date descending by default)
index_generator:
  path: ''
  per_page: 10
  order_by: -updated
```

---

# Trim Command

Use short `npm` command to run instead of long command such as `hexo clean && hexo g && hexo d`. Add following scripts to `package.json`:

```
,
  "scripts": {
    "d": "hexo clean && hexo g && hexo d",
    "cg": "hexo clean && hexo g"
  }
```

Now, the long command can be replaced with `npm run d`

I do not recommend adding `"hexo clean && hexo g && hexo s"`  to `"scripts"`. 

I tried it, and it resulted prompt switch to new line after `INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.` information, and `Ctrl+C` cannot strop server from running. It can be a problem if settings are modified, and the process needs to be restarted.

So I have to find the process running the port 4000, and force to kill it, then restart the server, which is more time consuming.

```
# Find the pid of the process running in the port number (e.g., 8080)
# from https://stackoverflow.com/questions/48198/how-can-you-find-out-which-process-is-listening-on-a-port-on-windows
$ netstat -ano | findStr "4000"
  TCP    0.0.0.0:4000           0.0.0.0:0              LISTENING       8496                 TCP    [::]:4000              [::]:0                 LISTENING       8496   
$ taskkill /F /PID 8496
SUCCESS: The process with PID 8496 has been terminated.
```

------

