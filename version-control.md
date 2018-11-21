For the sake of our future selves, let's
>keep calm and apply version control methods

# General
For some background on version control methods in general:
- [Atlassian: What is version control](https://www.atlassian.com/git/tutorials/what-is-version-control)

# GitHub
- [Intro to GitHub](https://resources.github.com/webcasts/Intro-to-GitHub/) An introductory video to the GitHub workflow from GitHub themselves.
- [How to Use Git and GitHub - Udacity](https://eu.udacity.com/course/how-to-use-git-and-github--ud775) A free online course, approximate time to complete is 12 hours.
- [Conducting a full code review using GitHub](http://astrofrog.github.io/blog/2013/04/10/how-to-conduct-a-full-code-review-on-github/) There is no official way to do this using GitHub, however this handy guide talks through how to do this by creating an empty branch.

# Git
Once you are familiar with the GitHub workflow and have had a bit of practice using the integrated buttons in RStudio (see resources below), we would highly recommend trying out the command line. The integrated functionality of Git/GitHub with RStudio is excellent, but it does have some limitations. Learning a few basic git commands will give you a lot more flexibility, for example when using branches. 
- [Our own gitbash cheat sheet](https://github.com/NHS-NSS-transforming-publications/GitHub-guidance/blob/master/gitbash-cheatsheet.md)
- [Git command line cheat sheet from GitHub](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf)
- [Setting Commit Email Address](https://help.github.com/articles/setting-your-commit-email-address-in-git/) - NB: this needs to be done separately within the RStudio terminal if also committing with RStudio

# Git and GitHub with RStudio
- [DataSurg: RStudio and GitHub](http://www.datasurg.net/2015/07/13/rstudio-and-github/) 
A blog with straightforward descriptions of the steps required to get set up with Git and GitHub on RStudio.
- [Happy Git and GitHub for the useR](http://happygitwithr.com/) 
A comprehensive guide to using Git and GitHub with RStudio, including specific workflow examples and tutorials.
- [Happy Git and Github for the useR – Tutorial](https://www.rstudio.com/resources/videos/happy-git-and-gihub-for-the-user-tutorial/)
A long but *very* informative lecture by the author of Happy Git, Jenny Bryan (:raised_hands:) Includes a set-up guide, practical exercises, helpful tips (such as **_commit early and often_** and **_burn it all down_** :fire:) and a section on markdown.
- [RStudio: Version Control with Git and SVN](https://support.rstudio.com/hc/en-us/articles/200532077-Version-Control-with-Git-and-SVN)
- [RStudio: Using Projects](https://support.rstudio.com/hc/en-us/articles/200526207) You will need to get used to using R Projects for version control so this gives a brief introduction.
- [Writing good commit messages](https://github.com/erlang/otp/wiki/writing-good-commit-messages) A short, but helpful blog post on how to write helpful and informative commit messages.

# Advice on "Time travelling" with git

Use `git revert` to undo the changes made in a previous commit (this doesn’t need to be the last one). This doesn’t remove the commit, but adds a new commit that inverts the changes made previously. This is the best way to undo something as it retains all the history and you can do this within a branch and then merge it back into the master. The command is:

`git revert –n <commit ref code>`

The `–n` means "no commit" – so the changes are staged but you  then need to run `git commit –m “commit message”` to commit these changes. You can run git revert without `–n`, however this will open the git bash editor and ask you to enter a commit message - you may prefer to commit manually.

Alternatively, you can use `git reset` to roll back the repo to a specific point in time. However, this deletes commits and so doing this within a branch causes problems when you want to merge back into the master as the branch is *x commits behind*. There are only two situations where using this would be sensible: if you’re working locally and haven’t pushed your commit to GitHub yet or if something major has gone wrong in the repo and a reset is done within the master branch. The following command also gives the option to delete changes altogether or delete commits whilst keeping changes staged or unstaged:

`git reset –hard <commit ref code>`

**Remember**, this will reset the branch to the referenced commit and **delete all changes committed after this point** so :warning: use with caution!!! :warning:

For further reading on time travelling in git:

Git revert: https://www.atlassian.com/git/tutorials/undoing-changes/git-revert

Git reset: https://www.atlassian.com/git/tutorials/undoing-changes/git-reset
