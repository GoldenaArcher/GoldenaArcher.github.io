---
title: Git Still Tracks Files in .gitignore?
date: 2019-06-10 23:27:05
tags: [GitHub, Git bash]
categories: 
- GitHub
- Git bash
---

<img src="https://i.loli.net/2019/06/10/5cfe784215d4c44471.png" width=500>

Once upon a time, when I was using Intellij IDEA for one of my school project, I found all the configuration files of  Intellij are very annoying. I added all the files into the `.gitignore`, and hope those files wouldn't be uploaded anymore. Yet... They were still uploading and updating which drove me crazy. I didn't know what're the problems, and I was so occupied by other works. I decided to let it be.

However, now, I'm facing the same issue when I add ` Views` to the project, and I have to remove all the `_config.yml` files from git branch. Though my project is not worthy to crack, I'm not comfortable to let my password flow around on the internet.

SO, they have to be __REMOVED__!

<!-- more -->

# The Causes

First of all steps is always to search on the Google for any similar problems, and whether answers have already been provided.

Not surprise, many people have encountered same issues, and solutions have been provided. [How to make Git “forget” about a file that was tracked but is now in .gitignore?](https://stackoverflow.com/questions/1274057/how-to-make-git-forget-about-a-file-that-was-tracked-but-is-now-in-gitignore) and [.gitignore still tracking files even if I tried to ignore them, why?](https://stackoverflow.com/questions/42441522/gitignore-still-tracking-files-even-if-i-tried-to-ignore-them-why) have explained it very well.

To be more specific, the reasons that `.gitignore` is not ignoring listed files are:

- Files have been cached locally. That is:
  - Files have been tracked by `git add` command;
  - Or files have been pushed to local repository by `git push` command.
- Files have been pushed to remote repository already.

---

# Solutions

This is the paths I took.

First of all, use `git rm --cached <file>` to untrack files, if files haven't been commit locally or pushed remotely, this command is all good.

On the other hand, if the files have been commit locally or pushed remotely, then, a commit is necessary to save the changes.

So, the code is:

```
# <file> can be a file or a location
$ git rm --cached <file>
# just in case, commit the changes
$ git commit -m "remove cached files"
```

---

## Furthermore...

In my case, I did not know that `.gitignore` is not working properly, and save `app_id` in the `_config.yml` file already. `git rm --cached` only removes files from caches locally, but will not change the files have already been pushed to remote repository.

Since I realized the problem early on, I decided to rebase the current branch to previous state, and everything is all good:

```
# rebase to previous stage since it's my last commit
$ git rebase -i HEAD~2
# force push
$ git push --force
```

---

# Conclusion

The `git rm --cached` command does not remove files from all the commits, therefore only works when files that have not yet been committed, or the files have been committed are not important.

It is always a good habit to add all the files in `.gitignore`beforehead, rather than trying to make up later.