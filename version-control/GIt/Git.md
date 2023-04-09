## Basics

Git is a free and open-source version control system, originally created by Linus Torvalds in 2005. Unlike older centralized version control systems such as SVN and CVS, Git is distributed: every developer has the full history of their code repository locally. This makes the initial clone of the repository slower, but subsequent operations such as commit, blame, diff, merge, and log dramatically faster.

Git also has excellent support for branching, merging, and rewriting repository history, which has led to many innovative and powerful workflows and tools. Pull requests are one such popular tool that allows teams to collaborate on Git branches and efficiently review each other's code. Git is the most widely used version control system in the world today and is considered the modern standard for software development.

## How Git works

Here is a basic overview of how Git works:

1. Create a "repository" (project) with a git hosting tool (like GitHub, GitLab, Bitbucket)
2. Copy (or clone) the repository to your local machine
3. Add a file to your local repo and "commit" (save) the changes
4. "Push" your changes to your main branch
5. Make a change to your file with a git hosting tool and commit
6. "Pull" the changes to your local machine
7. Create a "branch" (version), make a change, commit the change
8. Open a "pull request" (propose changes to the main branch)
9. "Merge" your branch to the main branch

## How to configure Git

To verify this, you can run this command on the command line: 
``` sh
git --version
```
This shows you the current version installed on you PC.

+ The next thing you'll need to do is to set your username and email address. Git will use this information to identify who made specific changes to files.

To set your username, type and execute these commands: 
``` sh
git config --global user.name "YOUR_USERNAME"
```
and
``` sh
git config --global user.email "YOUR_EMAIL"
```
Just make sure to replace `"YOUR_USERNAME"` and `"YOUR_EMAIL"` with the values you choose.

## Git Basic Commands

``` sh
git init (Initialize the repo)

git status (View the status of all the files)

git add . (Add all files uncommited files)

git add "filename" (Add a single uncommitedfile)

git commit -m "message here"

git remote add origin "origin url"

git branch -M main

git push -u origin main

git checkout -b "branchname"
```
