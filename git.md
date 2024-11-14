# Version control with Git

Git is an open source distributed version control system designed to
handle everything from small to very large projects with speed and
efficiency. This tutorial shows how to install and use Git in a local
computer and connect to a remote repository on GitHub or GitLab. The
following are great sources to learn more about Git:

- [Pro Git book](https://git-scm.com/book/en/v2)
- [Version Control with Git](http://swcarpentry.github.io/git-novice/)
- [GitHub cheat
  sheet](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf)

------------------------------------------------------------------------

## Installation

Depends on the operating system, it might be needed to [install
Git](https://git-scm.com/downloads) first. Computers with Windows
operating systems do not automatically have a Unix Shell installed. So
for Windows users, it would be better to install [Git for
Windows](https://gitforwindows.org/), which gives you access to both
Bash Shell and Git simultaneously.

When we use Git for the first time, its better to configure user name
and email by:

``` bash
$ git config --global user.name "your name"
$ git config --global user.email "your@email"
```

This will set your name and email address to all activities associated
with Git. We can find the list of adjusted configurations by
`git config --list` and to see more helps by `git config --help`.

## Git commands

As a prerequisite, first learn about the [Unix Shell](shell.html) and
basic Bash commands.

Let’s start working with Git on your local computer with an example.
First, we will make a directory and then initiate a Git repository in
the directory, and then start to add a text file and edit the file.

Open a terminal prompt and run the following commands one by one, read
the comments after hash to see what they do.

``` bash
cd ~ # change directory to home/
mkdir first_repo # create a new directory called "first_repo"
cd first_repo # change directory to home/first_repo
git init # create an empty Git repository (after that Git could track all changes in this directory)
git status # show the working tree status which tells "nothing to commit"
nano file.txt # nano text editor will create "file.txt" and open the file. Let's add the following:
>Hi! this is the first line in my new repository. # press ctrl+o to save and ctrl+x to exit
git status # say "nothing to commit but untracked files present"
```

To record all changes by Git, we need to:

- Add file contents to the index by `git add`
- Record changes to the repository by `git commit`

Use the following commands for the above steps:

``` bash
git add file.text # add file contents to the index
git status # show changes to be committed
git commit -m "Add file.txt and write the first line" # record changes to the repository, -m option add message
git show file.txt # show the most recent commit of "file.txt" 
git log # show the commit logs
```

Let’s make some changes in the `first_repo` directory to see how Git
records changes:

``` bash
nano file.txt # nano will open "file.txt"
>Hi! this is the first line in my new repository. 
>Changes in this file will record by Git. # press ctrl+o to save and ctrl+x to exit
git status # show changes not staged for commit
git diff file.txt # show changes between most recent commit and the current "file.txt"
```

Use the following to record above changes by Git:

``` bash
git add file.txt
git commit -m "Add the second line"
git show file.txt # show the most recent commit of "file.txt" 
git show HEAD~1 file.txt # show the previous commit of "file.txt" 
```

Also, we can compare changes between the current version and previous
versions. Let’s make some more changes on the `file.txt` to see how we
can compare all versions:

``` bash
nano file.txt # nano will open "file.txt"
>Hi! this is the first line in my new repository. 
>Changes in this file will record by Git. 
>This changes are new. # press ctrl+o to save and ctrl+x to exit
git diff file.txt # show changes between the most recent commit and the current "file.txt"
git diff HEAD~1 file.txt # show changes between the previous commit and the current "file.txt"
```

Record new changes by:

``` bash
git add file.txt
git commit -m "Add the third line"
git show file.txt # show the most recent commit of "file.txt" 
git show HEAD~1 file.txt # show the previous commit of "file.txt" 
git show HEAD~2 file.txt # show the previous previous commit of "file.txt" 
```

We always can restore previous versions of our work. Let assume that we
want to restore the previous version of `file.txt`:

``` bash
cat file.txt # show the content of the file 
git show HEAD~1 file.txt # show the previous commit (we want to restore this version)
git checkout HEAD~1 file.txt # restore the previous version
cat file.txt # show the content of the file
```

Again record new changes by:

``` bash
git add file.txt
git commit -m "restore the previous version"
```

Also, we can unstage an added file by using `reset` command:

``` bash
git add file.txt 
git reset file.txt # unstage added file
```

**Note:** `reset`, `checkout` and `revert` all let us undo changes in a
repository. Learn more about them in
[here](https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting).

Your local computer might be one side of your mechanism to control and
store your file versions. [GitHub](https://github.com/) and
[GitLab](https://about.gitlab.com/) are providing an infrastructure to
keep track of our files in somewhere outside the local computers. Let’s
connect to GitHub through SSH and add `first_repo` repository to it.

To connect your GitHub (or GitLab) account through SSH, you should
generate a public SSH key on your local computer and add it to your
GitHub account at `Settings > SSH Keys`. To do that open a terminal
prompt in your computer and issue:

``` bash
cd ~
ssh-keygen
```

Make sure to create a strong passphrase and remember it for latter. To
show the public key, use the following in the terminal prompt:

``` bash
cat .ssh/id_rsa.pub
```

Copy the the public ssh-key and add it to `Settings > SSH Keys` on your
GitHub account.

Now, click on “+” next to your avatar on GitHub to generate a new
repository, name it `first_repo` and do not initialize it. For next
steps, copy the SSH address of your remote repository from GitHub that
should be like `git@github.com:user/first_repo.git` - later you may find
the address under “Clone or download” tab on your repository.

To add the remote repository, open a terminal prompt on your computer
and issue:

``` bash
cd ~/first_repo
git remote add origin git@github.com:user/first_repo.git # add the remote repo
git remote -v # show the remote repository 
```

Finally, to upload your local repository to GitHub use:

``` bash
git push -u origin master
```

You can always generate and initialize a new repository on your remote
i.e. GitHub and clone to your local computer. Click on “+” next to your
avatar on GitHub to generate a new repository, call it `second_repo` and
make sure to be initialized. To clone the remote repository on your
local system with SSH, click on “Clone or download” and copy the SSH
address. Open a terminal prompt on your local computer and issue:

``` bash
cd ~
mkdir second_repo 
cd second_repo
git clone git@github.com:YourUserName/second_repo.git
```

Any changes in the `second_repo` directory will record by Git and you
can use `git push origin` to update the remote.

Another important asset of Git is collaboration with others at the same
time. One of the most effective way to collaborate without conflict, is
making new branches in addition to the `master` branch. Use the
following Git commands to make a new branch and switch between branches
:

``` bash
git branch # show all branches
git branch my_work # create my_work branch
git checkout my_work # switch to my_work branch
```

Now if we keep working on the directory, all changes will be stored at
`my_work` branch instead of `master` branch. That will prevent the
conflict between your work and others. When you finish your tasks you
can merge `my_work` branch to the `master` by:

``` bash
git merge my_work
```

Also, we can add multiple remote to a repository. To add another remote
(called `public`) to the current remote (`origin`) we can use:

``` bash
git remote add public SSH_adress 
```

Where the `SSH address` is address of the new remote (for example
another empty repo. in GitHub) - try `git remote -v` to see name and
address of remotes.

To push the repositort to `public` remote use:

``` bash
git push public master
```

Above commad will create a new branch called `master` in `public` remote
and push entire repo to the new location. Note that now we have two
remotes for the repo.

## Summary

The following Git commands are used in this article:

``` bash
man git <command> # show the manual of the command
git init # create an empty Git repository or reinitialize an existing one
git config -l # list config file
git config -e # edit config file
git status # show the working tree status
git add # add file contents to the index
git mv # move or rename a file, a directory
git rm # remove files from the working tree (local) and from the index (remote)
git rm --cached # unstage and remove paths only from the index (remote)
git log # show commit logs
git log <file_name> # show commit logs for the file
git log --patch <file_name> # combine both `git log` and `git diff` comments
git diff # show changes between commits, commit and working tree, etc
git diff --staged # show changes between commit and working tree after add
git diff HEAD # show changes between working tree and the most recent commit
git diff HEAD~n # show changes between working tree and the nth most recent commit 
git diff HEAD <file_name> # show changes between the current file and the most recent commit
git show HEAD <file_name> # show the most recent commit of a file
git show HEAD~n <file_name> # show the nth most recent commit of a file
git checkout # restore working tree files or switch branches
git checkout HEAD <file_name> # recover the version of the file recorded in HEAD
git reset <file_name> # reset (unstage/uncommit) current HEAD to the specified state
git reset --hard HEAD~1 # reset commited state to last HEAD 
git revert <commit ID> # revert some existing commits
git revert --no-commit HEAD # revert to last commit (no asking to commit at the moment)
git revert --abort # abort the revert (return to before revert)
git remote # show the remote repository (use -v floag for a verbose details)
git remote add origin <SSH_add> # add remote repository to the local repo 
git remote remove <remote_name> # remove a remote repository
git remote rename <remote_name> <new_name> # rename a remote repository
git remote set-url origin <url> # set/change remote origin
git clone # clone a repository into a new directory
git fetch # download all history from the remote tracking branches
git merge # join two or more development histories together
git pull <origin> <branch> # a combination of fetch and merge
git push <origin> <branch> # update remote refs along with associated objects
git commit # record changes to the repository
git commit --amend # edit the commit comment before push (i to insert and esc- :wq to exit)
git branch # list branches
git branch <new branch name> # create a new branch
git branch -d <branch name> # delete a branch
```

---

Copyright, [Ashkan Mirzaee](https://ashki23.github.io/index.html) | Content is available under [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/) | Sourcecode licensed under [GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.en.html)
