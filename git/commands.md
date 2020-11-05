---
layout: default
title: Commands
parent: Git
---

## Single Command

| Command                    | Description |
| -------------------------- | ----------- |
| `git log --pretty=oneline` | View commit history |
| `git status --short`       | View status with simplified format |
| `git commit --amend`       | Make a change to previous commit message |
| `git reflog`               | See a list of everything done in git across all branches |


## Series of Commands

### I did something wrong. Let me go back in time.

```
# See a list of everything done in git across all branches
git reflog
# Reset to a point before you broke something
git reset HEAD@{index}
```

### Make a change to previous commit

```
# Add all files or individual files
git add .
# Make a change to previous commit
git commit --amend
```

### I accidentally committed something to master that should have been on a new branch.

```
git branch new-branch-name
git reset HEAD~ --hard
git checkout new-branch-name
```

### I committed to the wrong branch.

```bash
git checkout name-of-the-correct-branch
# grab the last commit to master
git cherry-pick master
# delete it from master
git checkout master
git reset HEAD~ --hard
```

### I need to update a forked repository.

```bash
# Add the remote, call it "upstream":

git remote add upstream https://github.com/whoever/whatever.git

# Fetch all the branches of that remote into remote-tracking branches,
# such as upstream/main or upstream/master:

git fetch upstream

# Make sure that you're on your main branch:

git checkout main

# Rewrite your main branch so that any commits of yours that
# aren't already in upstream/main are replayed on top of that
# other branch:

git rebase upstream/main

# If you don't want to rewrite the history of your main branch, (for example because other people may have cloned it) then you should replace the last command with
git merge upstream/main

# If you've rebased your branch onto upstream/main you may need to force the push in order to push it to your own forked repository on GitHub
git push -f origin main
```
