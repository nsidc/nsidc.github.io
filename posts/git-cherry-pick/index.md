---
title: "Cherry-Pick on GitHub"
author: "Robyn Marowitz"
date: "2023-09-26"
description: "Committing a mistake in GitHub can feel so scary, cherry picking is a tool to help you fix your history when something like that happens. This post lays out simple and clear instructions on the cherry picking method."
categories: [github, open-science]
image: "cherry_pick.jpeg"
---

## What is git cherry-pick?

It is the act of picking a commit from one branch and applying it to another branch.  

## When should I use cherry-pick?

Cherry-Pick is best used when a change has been committed onto a different branch than desired. You can *pick* commits one by one and move them to the desired branch. 

`git cherry-pick` usually brings a commit from somewhere else and applies it on top of your current branch, recording a new commit, while `git rebase` takes your current branch and rewrites a series of its own tip commits in one way or another.

## Git command/syntax:

When using cherry pick it is very important to look at your git log and understand what is gong on.

First it can be useful to look at the branches you have. I did this with the `git branch` command and as you can see the one with the asterik and in green is the branch I am currently on. 

![](show-branches.png)

I use `git lola` which is an alias:  `lola = log --graph --decorate --oneline --all`. I highly recommending adding this alias to your `.gitconfig`. 

Git throws things away after 2 weeks that are not pushed. 
