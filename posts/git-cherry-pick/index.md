---
title: "Cherry-Pick on GitHub"
author: "Robyn Marowitz"
date: "2023-09-26"
description: "Committing a mistake in GitHub can feel so scary. Cherry picking is a tool to help you fix your history when something like that happens. This post lays out instructions on the cherry picking method."
categories: [github, open-science]
image: "cherry_pick.jpeg"
---

## What is `git cherry-pick`?

It is the act of picking a commit from one branch and applying it to another branch.  
Read more in the [official docs](https://git-scm.com/docs/git-cherry-pick)

## When should I use `git cherry-pick`?

`cherry-pick` is best used when a change has been committed onto a different branch than desired. You can *pick* commits one by one or by choose a range and move them to the desired branch. 

```
git cherry-pick <commit>
git cherry-pick <commit A> <commit B>
git cherry-pick <commit A>...<commit C>
```

### How is `cherry-pick` different than `rebase`?

`git cherry-pick` usually brings a commit from somewhere else and applies it on top of your current branch, recording a new commit, while `git rebase` reapplies commits on top of another base tip.

`cherry-pick` is simpler and less risky. `rebase` is a valuable tool, but if you don't understand what it's doing, you can get in trouble pretty easily.

`rebase` will likely be covered in a future post. 

## Git command/syntax:

When using cherry pick it is very important to look at your git log and understand what is going on.

First it can be useful to look at the branches you have. I did this with the `git branch` command and as you can see the one with the asterik and in green is the branch I am currently on. 

![image showing branches with asterik showing the branch user is on](show-branches.png)

I use `git lola` which is an alias:  `lola = log --graph --decorate --oneline --all`. I highly recommending adding this alias to your `.gitconfig`. 

![git history with circle around the commit that will be cherry-picked](lola-1.png)


Here you can see that I have the `cherry-pick-post` branch checked out, as indicated by the `HEAD` ref. I have made changes to the about section which I actually wanted to do on the main branch. So I will use `git cherry-pick` to make that happen. First you want to be sure you are on the branch that you want to put the commit on.

![image showing results of 'git status' command. Shows current branch and that there is nothing to commit.](status-on-cpp-branch.png)

I can see I am on the `cherry-pick-post` branch but I want the new commits to be created on `main`, so I will use `git switch` to go to the `main` branch. 

![git switch command shown moving the head to main branch](switch-main.png)

Now I am on the desired branch so I can go ahead and cherry-pick using the syntax `git cherry-pick <commit>`.

![pick command with previously circled commit #4ea71f7 chosen and git response shown](pick-commit-1.png)

To see what this did we will once again do `git lola`:

![git log command run showing new comnit with same caption as 4ea71f7 (update about page) on main branch](lola-after-pick1.png)

Now the `Update about page` commit is on both the `cherry-pick-post` branch and the `main` branch. Note that the commit ID on the `main` branch is a new ID, but the original commit  on `cherry-pick-post` branch has the same ID as before.

We will now push and look at the log again. 

![git push command shown at top of image followed by git lola command with 'Update about page' commit shown on origin.main, Head, main branch](push-and-lola.png)

At this point `main` appears exactly as we want it to, but `chery-pick-post` still has the unwanted commit. 

So at this point we will once again use the cherry-pick command to move forward. I will create a new branch called `cherry-pick-1` from the main branch.

![creation of new cherry-pick-1 branch using git switch -c command](new-branch.png)

Now at this point I want to take everything from the old `cherry-pick-post` branch and pick it to my new branch. 

There are 3 commits that I want so I can actually pick them all a once. 

`git cherry-pick 9e5da76 463956b 3edb3ee`

![git response to the cherry pick command listed above this image](pick-2.png)

Git gives a great summary of what is happening and shows the commits I am picking. 
To see where I am at I will do `git lola` once again.

![git log showing head on new branch containing the 3 picked comits with new commit numbers](lola-2.png)

At this point I have the 3 commits I want on my new branch so I can go ahead and push that branch. `git push -u origin cherry-pick-1`

![log after push](lola-3.png)

Now I no loger want the old branch so I will delete it using `git branch -D cherry-pick-post` this will only delete it locally, so I will also need to do `git push origin :cherry-pick-post` to delete the branch from GitHub.

Note: Git may keep untracked history for around 2 weeks so there is always time to alter if you decide you want to revive something. 

## Summary

Cherry picking is a tool for copying commit(s) from one branch to another.
It is important to remember that this is a powerful tool and you should proceed with caution when using it to copy a commit(s) to a different branch. 
Learning `cherry-pick` is a useful step on the way to learning about `rebase` - which will be covered in this space soon. 
