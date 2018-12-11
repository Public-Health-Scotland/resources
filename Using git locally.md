Contents?

# Introduction

The [git](https://git-scm.com/) software is used by GitHub in order to provide a [distributed version control and code management system](https://www.atlassian.com/git/tutorials/what-is-version-control), as well as additional features such as facilitating code reviews, logging and assigning issues and controlling access. We recommend that git is used along with a code repository such as GitHub (or Gitea, Gogs, GitLab, etc) and that the [GitHub workflow](https://github.com/NHS-NSS-transforming-publications/GitHub-guidance) is followed. This is particularly important for collaborative projects. However, git can also be used locally on your own machine in order to keep track of your files and folders while you work on a project. This step-by-step guide walks you through how to do this for an R project, but the same principles apply no matter what kind of files you are working with. 

# Step-by-step guide

## Step 1: Install git!

Git is a freely available open-source software. If you are working for PHI then please contact IT to request that git be made available on your machine for installation (NB: have checked if this is indeed the case with IT). 

## Step 2: Initialise git in your project folder

Navigate to the local folder you wish to apply git to, right click and select 'Git Bash Here'. This will open a command-line interface from where you can run all your git commands, plus other standard unix commands (e.g. `cd` to change directory, `ls` to list all items in the current folder, etc):

![](https://i.imgur.com/HJkiqQs.png)

In the command line enter `git init`. Git is now initiliased inside this folder and will track any files and folders within it. 

![](https://i.imgur.com/2kQGtHE.png)

You will notice that you are now on the 'master' branch. For set-up purposes, we will continue to work on the master branch, but note that **it is good practice to do any work in a separate branch which is later merged into the master when ready**.

## Step 3: Create a new R project

Create a new R project inside the folder - the easiest way to do this is to open RStudio, select 'New Project...' -> 'Existing Directory' -> select the folder where git is initialised. The 'Git' tab in the Environment pane should become available. You will also be able to access the .gitignore file from within RStudio. For more on .gitignore please see the [TPP GitHub guidance repository](https://github.com/NHS-NSS-transforming-publications/GitHub-guidance).

![](https://i.imgur.com/h39Sjn1.png)

![](https://i.imgur.com/Vyo0alA.png)

![](https://i.imgur.com/UBaHIp8.png)

## Step 4: Commit changes

You have now made some changes to the folder and git will recognise this. In Git Bash enter `git status`:

![](https://i.imgur.com/lu4GDFa.png)

Git has recognised two new untracked files highlighted in red - the .gitignore file and the RStudio project. In order to track these files we must first stage the files using `git add <file name>`. Either stage each file individually (`git add .gitignore` and `git add project.R`), or use `.` to stage all files where changes have been detected by git (`git add .`). **Please use this latter command with caution - it is usually safer to stage each file or folder sepratately**.

![](https://i.imgur.com/9LDLpuk.png)

Finally, a set of staged changes can be committed using `git commit -m <commit message>`:

![](https://i.imgur.com/1bFyg99.png)

Ensure your commit message is [concise, meaningful and written in the imperative mode](https://github.com/erlang/otp/wiki/writing-good-commit-messages). Git has now stored a snapshot of your project folder and its contents at this point in time. In future, you could look back through old versions of the folder via your commits and, if necessary, revert to a previous version.

## Step 5: Create a branch

One of the key features of git is branches. When it is first created, a branch is simply an exact copy of your original folder and its contents (the master branch). As you work on a branch it will change over time, but the master branch remains the same as it was before the branch was created. This means that you always retain a master copy of your project on the master branch and only merge changes into it when you are satisfied that they are ready. To create a branch use `git branch <name of branch>`:

![](https://i.imgur.com/guleKWY.png)

From now on we will refer to this kind of branch as a "working branch". To switch to this new working branch use `git checkout <name of branch>`:

![](https://i.imgur.com/KkY5mAI.png)

You will see via Git Bash that you are now on your working branch - inside RStudio you will also see the branch name in the Git tab.

![](https://i.imgur.com/m8K5ZEQ.png)

## Step 6: Make and commit changes on your working branch

For example, create a new R script inside the R project and add some code, staging and committing as you work.

SCREENSHOTS OF FURTHER CHANGES (CREATING A SCRIPT AND ADDING CODE TO IT)

You can see that these changes have not been added to the master branch by switching back and inspecting the contents of the folder. You can also use `git diff <master branch> <working branch>` to preview differences between branches. Below, I have switched back to the master branch and, using this command, can see the differences between the two branches:

SCREENSHOT OF GIT DIFF

## Step 7: Merge changes into the master branch

When you are happy with the changes to your project on your working branch and want them to be included in the master branch, use `git merge <working branch>`:

SCREENSHOT OF GIT MERGE

## Step 8: Delete branch

Now that you are finished with your working branch delete it using `git branch -d <branch name>`:

SCREENSHOT OF GIT BRANCH -D

There is no need to have long-living branches; when you want to make further changes to your project, simply create a new working branch. Deleting working branches after merging will significantly reduce your risk of a merge conflict (see below)

# Top tips
e.g. commit often, delete branches after merging, write good commit messages, can have multiple branches for fixing multiple features, git init on existing projects, what to do if you needs help
Something about merge conflicts - won't cover here but refer to David's info

# Further resources
Git Bash cheatsheet
TPP version control page (especially for time travel info)
TPP GitHub guidance
http://rogerdudler.github.io/git-guide/ 

*get someone new to try these steps and see if there are any problems/what the git log looks like*
