---
title: Git Bash Issues
date: 2019-06-09 22:45:34
tags: [GitHub, Git bash]
categories: [GitHub]
---

Just some problems that I have encountered, and how to resolve these issues.

<!-- more -->

---

# Could not resolve hostname

```
$ git push
ssh: Could not resolve hostname github.com: Name or service not known
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```

I found this solution from [this problem](<https://stackoverflow.com/questions/9393409/ssh-could-not-resolve-hostname-github-com-name-or-service-not-known-fatal-th>) perfectly solves this issue:

```
ipconfig /flushdns
```

---



