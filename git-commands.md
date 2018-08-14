---
title: "Git Commands"
date: 2017-11-29T17:01:37+11:00
draft: false
tags: ["git"]
categories: ["Developer"]
---

# 1. git config
Tell Git who you are
```shell
git config -l
git config --global user.name "David Duan"
git config --global user.email david.duan@fabricgroup.com.au
```
# 2. git init
Create a new local repository
```shell
git init
```

# 3. git clone
Check out a repository
```shell
#Create a working copy of a local repository:
git clone /path/to/repository
#For a remote server, use:
git clone username@host:/path/to/repository
```

# 4. git add
Add files
```shell
git add <filename>
git add *
```

# 5. git commit
Commit
```shell
#Commit changes to head (but not yet to the remote repository):
git commit -m "Commit message"
#Commit any files you've added with git add, and also commit any files you've changed since then:
git commit -a
```

# 6. git push
Push
```shell
#Send changes to the master branch of your remote repository:
git push origin master
#Push the branch to your remote repository, so others can use it:
git push origin <branchname>
#Push all branches to your remote repository:
git push --all origin
#Delete a branch on your remote repository:
git push origin --delete <branch_name>
# or
git push origin :<branchname>
#Push all tags to remote repository:
git push --tags origin
```

# 7. git status
Status
```shell
#List the files you've changed and those you still need to add or commit:
git status
```
# 8. git remote
Connect to a remote repository
```shell
#If you haven't connected your local repository to a remote server, add the server to be able to push to it:
git remote add origin <server>
#List all currently configured remote repositories:
git remote -v
#Show remote status and local status.
git remote show origin
```

# 9. git checkout
```shell
#Create a new branch and switch to it:
git checkout -b <branchname>
#Switch from one branch to another:
git checkout <branchname>
#If you mess up, you can replace the changes in your working tree with the last content in head,Changes already added to the index, as well as new files, will be kept.
git checkout -- <filename>
```

# 10. git branch
```shell
#List all the branches in your repo, and also tell you what branch you're currently in:
git branch
#Delete the feature branch:
git branch -d <branchname>
```

# 11. git pull
```shell
#Fetch and merge changes on the remote server to your working directory:
git pull
```

# 12. git merge
```shell
#To merge a different branch into your active branch:
git merge <branchname>
```

# 13. git diff
```shell
#View all the merge conflicts:
git diff
#View the conflicts against the base file:
git diff --base <filename>
#Preview changes, before merging:
git diff <sourcebranch> <targetbranch>
```

# 14. git tag
```shell
#You can use tagging to mark a significant changeset, such as a release:
git tag 1.0.0 <commitID>
```

# 15. git log
```shell
#CommitId is the leading characters of the changeset ID, up to 10, but must be unique. Get the ID using:
git log
```

# 16. git rebase
With the rebase command, you can take all the changes that were committed on one branch and replay them on another one.
Often, you’ll do this to make sure your commits apply cleanly on a remote branch 
```shell
git checkout experiment
git rebase master
```
You can rebase to your current branch in order to merge multiple commits into one.
```shell
git rebase -i HEAD~6 //6 number of commits
```

# 17. git stash
Use git stash when you want to record the current state of the working directory and the index, but want to go back to a clean working directory. The command saves your local modifications away and reverts the working directory to match the HEAD commit.
```shell
git stash list [<options>]
git stash show [<stash>]
git stash drop [-q|--quiet] [<stash>]
git stash ( pop | apply ) [--index] [-q|--quiet] [<stash>]
git stash branch <branchname> [<stash>]
git stash save [--patch] [-k|--[no-]keep-index] [-q|--quiet]
		      [-u|--include-untracked] [-a|--all] [<message>]
git stash [push [--patch] [-k|--[no-]keep-index] [-q|--quiet]
		       [-u|--include-untracked] [-a|--all] [-m <message>]
		       [-- <pathspec>...]]
git stash clear
```

# 18. git reset
This usage of git reset is a simple way to undo changes that haven’t been shared with anyone else. It’s your go-to command when you’ve started working on a feature and find yourself thinking, “Oh crap, what am I doing? I should just start over.”
!["git commands git reset before and after"](/post/images/git-commands-git-reset-before.png)
```shell
# discard all unstaged changes
git reset --hard
# discard last 2 commits
git reset HEAD~2
# revert the last commit to unstaged
git reset --soft HEAD^
```

# 19 git revert
Reverting undoes a commit by creating a new commit. This is a safe way to undo changes, as it has no chance of re-writing the commit history.

You can also think of git revert as a tool for undoing committed changes, while git reset HEAD is for undoing uncommitted changes.
```shell
git revert HEAD~2
```
!["git commands git revert before and after"](/post/images/git-commands-git-revert-before-after.svg)

# 20 git cherry-pick
Merging a specific commit from one branch to another.

```shell
git cherry-pick d4d8e7c
```

# Reference
+ [https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html](https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html)
+ [https://git-scm.com/book/en/v2/Git-Branching-Rebasing](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)
+ [https://git-scm.com/docs/git-stash](https://git-scm.com/docs/git-stash)
+ [https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting](https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting)