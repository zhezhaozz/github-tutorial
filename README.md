# Collaborative development using Git and GitHub

This is a tutorial about collaborative development using Git and GitHub I made for my lab and the Academia Cafe community. This repository was inspired and modified from the git tutorial created by [romankouz](https://github.com/romankouz/git_tutorial). I will give more details for each of following topics during presentations.

## Getting Started

1. Click Fork button on the upper-right corner to fork this repository. 
2. At your **terminal**, move to desired directory and type
```
% git clone https://github.com/your-username/github-tutorial.git
```
Now you have downloaded the project from the **remote** repository to your **local** repository. The local repository is where you and your teammates work independently, which means your own machine. The remote repository is where individual contributions are integrated into team project.

## The Basics

 - `git status`
 - `git add`
 - `git commit`
 - `git push`
 - `git pull`
 - ...
 
Above commands record any modification you make at your local repository and "push" these changes to the remote repository.

Reversely, if the remote repository has been updated, you can use `git pull` command to "pull" the updated version of project to your local repository.
 
## Working with Branches

When you type `git branch` in terminal, the output will look like this

```zsh
% git branch
* main
```
It means that the project right now has only one branch, the main branch. The main branch is normally where the final product is stored at. 

> __Warning__ You and your colleagues should always avoid pushing changes directly to the remote main branch. This will potentially cause merge conflicts (I will cover this later). Resolving merge conflicts and reverting commits that are already pushed to the main branch in remote repository can be confusing and difficult.

Assuming you and your teammate B are working on a project together, you both have cloned this project on local machines. Common practices suggest that you shouls always leave the main branch along and work on your own branches. Here is how you can create a new branch

```zsh
% git branch branch_a
% git branch
  branch_a
* main
```

Now you have created a new branch called `branch_a`. Note that the `*` means that you are still on the main branch. Make sure that you "checkout" the new branch before making any changes

```zsh
% git checkout branch_a
Switched to branch 'branch_a'
% git branch
* branch_a
  master
```

You can also use this one-line code to achive above action

```zsh
% git checkout -b branch_a
Switched to a new branch 'branch_a'
```

This command will create a new branch and automatically checkout the branch for you.

Now you can make any change on your new branch without affecting the main branch. You can experiment new features, make mistakes, destroy, or screw over your team project, knowing that there is always a main branch for backup. 

### Merge updated project to your local repository

Let's say your teammate B make some changes and pushed to the remote repository. Your boss is very happy and merged the new change into the main branch (on remote repository). How can you update your local repository to reflect new changes?

The answer is switching to the main branch and type `git pull` to pull all new changes. Switch back to you `branch_a` branch and use `git merge` to merge the new changes from main branch to "branch_a" branch.

What if your teammate B's branch (branch_b) has not been merged into the main branch (on remote repository), but you want to revise some of her bugs and integrate her new features into your own branch locally? You can achieve this by typing

```zsh
% git fetch origin branch_b
% git checkout branch_b
```

`git fetch` will fetch new changes from the remote repository without merging into your local repository. 

Then you can fix the bug, checkout to your branch "branch_a", and type


```zsh
% git merge branch_b
```

Now you have merged all changes from "branch_b" to "branch_a".















