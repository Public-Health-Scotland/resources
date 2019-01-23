# Using git locally

## Contents
- [Introduction](#introduction)
- [Step-by-step guide](#step-by-step-guide)
- [Top tips](#top-tips)
- [Further resources](#further-resources)

# Introduction

The [git](https://git-scm.com/) software is used by GitHub in order to provide a [distributed version control and code management system](https://www.atlassian.com/git/tutorials/what-is-version-control), as well as additional features such as facilitating code reviews, logging and assigning issues and controlling access. We recommend that git is used along with a code repository such as GitHub (or Gitea, Gogs, GitLab, etc) and that the [GitHub workflow](https://github.com/NHS-NSS-transforming-publications/GitHub-guidance) is followed. This is particularly important for collaborative projects. However, git can also be used locally on your own machine in order to keep track of your files and folders while you work on a project. This step-by-step guide walks you through how to do this for an R project, but the same principles apply no matter what kind of files you are working with. 

**IMPORTANT:** These instructions should **only be used on projects on your local machine or your personal network folder**, and not on shared network folders as RStudio will not integrate with git properly on these. These instructions are also **not intended for collaboration** - although collaboration and peer review is an important aspect of using version control, we do not currently have the organisation-wide infrastructure required to host this on a GitHub-like platform. It is possible to collaborate using git alone, but this requires a very specific set-up in order to work properly, which is not detailed here. In future we may add further instructions for collaborative working.

# Step-by-step guide

Throughout this guide, <> has been used to indicate text that should be edited by the user with your specific details.

## Step 1: Install git!

Git is a freely available open-source software. If you are working for PHI then please contact IT to request that git be made available on your machine for installation. 

## Step 2: Initialise git in your project folder

Navigate to the local folder you wish to apply git to, right click and select 'Git Bash Here'. This will open a command-line interface from where you can run all your git commands, plus other standard unix commands (e.g. `cd` to change directory, `ls` to list all items in the current folder, etc):

![](https://i.imgur.com/HJkiqQs.png)

In the command line enter `git init`. Git is now initiliased inside this folder and will track any files and folders within it. 

![](https://i.imgur.com/2kQGtHE.png)

You will notice that you are on the 'master' branch. For set-up purposes, we will continue to work on the master branch, but note that **it is good practice to do any work in a separate branch which is later merged into the master when ready**.

## Step 3: Configure your username and email (if using git for the first time)

**Note that this is a one-time step, the first time you use git.** So that git recognises who you are from now on, use the following commands to configure your username and email:

`git config --global user.email <NHS email address>`

`git config --global user.name <your name>`

You can check the current user details using:
`git config --global user.email`

## Step 4: Create a new R project

Create a new R project inside the folder - the easiest way to do this is to open RStudio, select 'New Project...' -> 'Existing Directory' -> select the folder where git is initialised. The 'Git' tab in the RStudio Environment pane should become available. You will also be able to access the .gitignore file from within RStudio. For more on .gitignore please see the [TPP GitHub guidance repository](https://github.com/NHS-NSS-transforming-publications/GitHub-guidance).

![](https://i.imgur.com/h39Sjn1.png)

![](https://i.imgur.com/Vyo0alA.png)

![](https://i.imgur.com/UBaHIp8.png)

## Step 5: Commit changes

You have now made some changes to the folder and git will recognise this. In Git Bash enter `git status`:

![](https://i.imgur.com/lu4GDFa.png)

Git has recognised two new untracked files highlighted in red - the .gitignore file and the RStudio project. In order to track these files we must first stage them using `git add <file name>`. Either stage each file individually (`git add .gitignore` and `git add project.R`), or use `.` to stage all files where changes have been detected by git (`git add .`). **Please use this latter command with caution - it is usually safer to stage each file or folder separately**. Note that if your file names contain spaces you will need to put single speech marks (e.g. `'file name'`) around it.

![](https://i.imgur.com/9LDLpuk.png)

Finally, a set of staged changes can be committed using `git commit -m <commit message>`:

![](https://i.imgur.com/1bFyg99.png)

Ensure your commit message is [concise, meaningful and written in the imperative mode](https://github.com/erlang/otp/wiki/writing-good-commit-messages). Git has now stored a snapshot of your project folder and its contents at this point in time. In future, you could look back through old versions of the folder via your commits and, if necessary, revert to a previous version.

## Step 6: Create a branch

One of the key features of git is branches. When it is first created, a branch is simply an exact copy of your original folder and its contents (the master branch). As you work on a branch it will change over time, but the master branch remains the same as it was before the branch was created. This means that you always retain a master copy of your project on the master branch and only merge changes into it when you are satisfied that they are ready. To create a branch use `git branch <name of branch>`:

![](https://i.imgur.com/guleKWY.png)

From now on we will refer to this kind of branch as a "working branch". To switch to this new working branch use `git checkout <name of branch>`:

![](https://i.imgur.com/KkY5mAI.png)

Note that these two steps can be done via one command (`git checkout -b <name of branch>`). You will see in Git Bash that you are now on your working branch - inside RStudio you will also see the branch name in the Git tab.

![](https://i.imgur.com/m8K5ZEQ.png)

## Step 7: Make and commit changes on your working branch

Here I have created a new script inside the R project and set up the script according to the [PHI R project template](https://github.com/Health-SocialCare-Scotland/r-project-structure) in order to start coding:

![](https://i.imgur.com/cXS6eFx.png)

This involved creating a new R script inside the R project and adding some code, staging and committing as I worked:

![](https://i.imgur.com/KLEUITH.png)

You can see that these changes have not been added to the master branch by switching back and inspecting the contents of the folder. You can also use `git diff <master branch> <working branch>` to preview differences between branches. Below, I have switched back to the master branch and, using this command, can see the differences between the two branches (additions will be highlighted in green, deletions in red):

![](https://i.imgur.com/0RVQFzP.png)

## Step 8: Merge changes into the master branch

When you are happy with the changes to your project on your working branch and want them to be included in the master branch, switch back to the master branch and use `git merge <working branch>`:

![](https://i.imgur.com/M7iN75N.png)

Note that you must switch back to the branch *into which* you want to merge changes.

## Step 9: Delete branch

Now that you are finished with your working branch delete it using `git branch -d <branch name>`:

![](https://i.imgur.com/gMQIFEk.png)

There is no need to have long-living branches; when you want to make further changes to your project, simply create a new working branch. Deleting working branches after merging will significantly reduce your risk of a merge conflict (see below).

## Step 10: Lather, rinse, repeat!

Continue working in this way, creating a working branch in order to make a set of changes to your code (via `git add` and `git commit`). When you are happy with these changes, merge into the master branch and delete the working branch. To see a history of commits on a certain branch use `git log`:

![](https://i.imgur.com/jjkg6bf.png)

Each commit is assigned a 40-character id (or 'hash'). This id is completely unique and allows you to identify each commit and what the folder and its contents looked like at a particularly point in time. As stated above, if required you can roll back a project to a previous commit - for more information on time travelling with git see the [version control page](https://github.com/NHS-NSS-transforming-publications/resources/blob/master/version-control.md) in this repository. 

# Top tips

The following are some tips to keep in mind when working with git:

- The steps above assume that you are starting an R project from scratch, but you can also initiliase git on an existing project folder.
- Commit often. Your commits are your project history, so create them frequently (after completing a section of code, before lunch, at the end of the day, etc).
- [Write good commit messages](https://github.com/erlang/otp/wiki/writing-good-commit-messages) which are succinct, meaningful and written in the imperative mode (i.e. "Add x, y, z" not "Added x, y, z"). 
- Delete branches after merging. This reduces the risk of merge conflicts and keeps your work set-up tidy.
- Merge conflicts occur when git cannot merge the same line from one branch into another. We won't cover merge conflicts in detail here, and they are unlikely to occur if you are working by yourself, but be aware that they can happen. If a merge conflict does occur then git will open the Git Bash Editor where you can resolve the conflict by chosing what code should be merged. This editor can be hard to exit so [this blog post](https://code.likeagirl.io/help-i-was-using-git-to-commit-some-code-and-now-the-window-has-changed-and-i-dont-know-what-s-9348a27e145b) may be helpful (the editor can open in other circumstances, such as if you are editing a commit message, so this is a handy link to favourite!). 
- It is possible to have multiple branches for fixing multiple features or working on different parts of your project, but be aware that this may increase the chance of a merge conflict. 

If you need help using git then there are a number of links to helpful online resources below. Please also feel free to get in touch with the Transforming Publishing team (nss.isdtransformingpublishing@nhs.net) if you have any questions.

# Further resources

- [Git Bash cheatsheet](https://github.com/NHS-NSS-transforming-publications/GitHub-guidance/blob/master/gitbash-cheatsheet.md) for frequently used git commands.
- [TPP version control page](https://github.com/NHS-NSS-transforming-publications/resources/blob/master/version-control.md) for links to fantastic online blogs, videos and courses on version control in general, git and GitHub specifically, and time travelling with git.
- [TPP GitHub guidance](https://github.com/NHS-NSS-transforming-publications/GitHub-guidance) for using git with GitHub for collaborative working and best practice/security guidance.
- [A great blog on getting started with git and Git Bash](http://rogerdudler.github.io/git-guide/).
