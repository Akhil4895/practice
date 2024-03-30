# Installation & Setup

* Download git for windows


## Setup
* List all git config settings
```
git config --global --list
```

* Set username
```
git config --global user.name "<value>"
```

* Set email

```
git config --global user.name "<value>"
```
## Git & Notepad++

### Setup notepad++ path
* Find notepad++ file location
* Copy path
* Open Env variables > System variables > paste path.
* Save
* Close terminal and reopen.
* Type notepad++ should open notepad++ application


### Setup alias in git for Notepad++

* open `gitbash`
* type `notepad++ .bash_profile`
* add the following to the file ```alias npp='notepad++.exe -multiInst -nosession'```

Set notepad as default editor
* ```git config --global core.editor "notepad++.exe -multiInst -nosession"```



## Install P4Merge(Meld - IBM alternative)

* Download p4merge from google
* During installation deselect all except `visual merge`
* complete installation

### Setup path just like notepad++
* Set path in environment variables 
* Set application as default for `diff` or `merge`
  ```git config --global merge.tool p4merge
  ---
     git config --global mergetool.p4merge.path "<path to location of app>"
  ```

* remove prompt from merge tool
  ```git config --global mergetool.prompt false```

* Add alias to git
```git config --global alias.hist "log --online --graph --decorate --all" ```

# Authentication to Github SSH/HTTPS

## Generate SSH key

* Go to home directory
* Check if there is `.ssh` directory in home
    * if not create one `mkdir .ssh`
* `cd .ssh`
* Create SSH key
    * `ssh-keygen -t rsa -C "<email>"`
        * `-t` type
        * `rsa` type of rsa
        * `-C` common name
* select location(press *enter* for default)
* Enter passphrase/can go w/o one as well
* `ls -al` should return two new files
* open `*.pub` file and copy entire content

## Add key in github ssh key authentication

## Verify authentication
* go to ssh folder
* ssh -T git@github.com (Enter)



## Create a repo
```git init <repo name>```

## Add existing folder to git
```git init```

## Local repo states
* working directory
* staging area
* repository

## Local Commit
* `git status` to get status of repo,
* `git add <filename>` gets file to staging area.
* `git add .` to stage all files.
* `git commit -m <"message">`
* `git commit -am <"commit message">` add modified files to staged and commit.

## Commit log/history
* `git log` (or) `git show`
* `git log --oneline`
* `git log --oneline --graph --decorate --all`
   * `oneline` --> oneline/simplified
   * `graph` --> asteric based graph hierarchy 
   * `decorate` --> which commits are part of which branches and other labels within repo
   * `all` --> history of all branches available

`git ls-files` shows files tracked by git


## revert changes:
* `git reset HEAD <filename>` unstage changes
* `git checkout -- <file name>` revert/undo changes and move to last commit


## Rename & delete

### Within Git
* `git mv <old name> <new name>` renames file
* `git rm <file name>` removes file from git

### Outside of git

* use bash mv command to rename file. Then git assumes file is deleted.
* `git add -u` u --> update
* `git add -A` checks for all types of modifications possible which is recognize file being renamed rather deleted.

## Git ignore
* create `.gitignore` file and add files or expression
    Ex: `*.log`


1. Compare differences
2. Branching, Merging & Conflict Resolution
3. Milestones
4. Work in Progress
5. Time Travel
6. Others

## Compare branches:
* `git diff` to compare with HEAD
* `git diff <commit hash> <commit hash>` to compare two commits.

## Branching 
* Fast forward
    * Simplest case
    * Like never Branched(commits to destination)
    * Can be disabled
* Automatic
    * non conflicting merge detected
    * Preserves both timelines
    * Merge commit to destination
* Manual
    * Automatic merge not possible
    * Conflict merge state
    * Changes saved in Merge Commit
* Special Markers
    * Like 'pointers'
    * HEAD
        * Points to last commit of Current branch
        * Can be moved(Advanced)

### Merge branch
```git merge <branch name>```

### Delete branch
```git branch -d <branch name>```

## Git tags
* `git tag --list` list tags
* `git tag <tag name>` create a tag at current commit.
* `git tag -d <tag name>` delete tag
* `git tag -a <v1.0> -m "<commit mesage>"` -a annotated -m message
    * `git show <v1.0>` shows commit/tag info of tag `1.0`

## Stash
* `git stash` save local changes without committing
* `git stash list` Lists all stashed instances that aren't reverted
* `git stash pop` apply last stash

## Reset & Reflog
* go back to previous commit
```git reset <commit id> --(soft|default|hard)```
* `git reflog` shows all actions taken.


## Connecting remote repo to local
* Create a repo in github/gitlab
* copy path and run
    * `git remote add origin <url>`
* `git remote -v` to check URL

## Push local repo to github
* `git push -u origin master --tags`
    * `-u` tracking branch relationship b/w local & remote
    * `origin` name of remote repo
    * `master` name of the branch we will push up
    * 

## Git default branch:
* `git branch -m main` to change default branch from *master* to *main*

## Change default repository of git using config
* `git config --global init.defaultBranch main` --> Changes default branch to main

## Update git url:
* `git remote set-url origin <url>`

## `git show <sha>` to view complete details of old/specific commit



* `git checkout -b <branch name>`   Create new branch
* `git push -u origin <branch name>` update a tracking remote branch from local
* `git branch -d <branch name>`     delete local branch
* `git fetch -p`                    (Prune) checks for any stale/deleted branches
* `git branch -a`                   List all branches
* `git push origin :<branch name>`  delete remote branch from local
* `git pull --rebase`               Pull with rebase pulls remote commits and add local commits
* `git tag -a v0.1-alpha -m "Release 0.1 (Alpha)" 85fe102` Add annotated tag to a old commit
* `git push origin <tag name>`      Push tag to remote
* `git push --tags`                 Push all tags
* `git tag -d v0.2-alpha`           delete a tag locally
* `git push origin :v0.2-alpha`     push deleted tag to remote
* `git tag -f <tag name> <hash>`    move tag to new commit
    * `git push --force origin unstable` force push tag to remote
* `` We can compare repo at different points using github UI within create PR page.


* `git clean -f` Remove untracked files
* `git clean -fd` Remove untracked directories

[Reference link](https://stackoverflow.com/questions/1146973/how-do-i-revert-all-local-changes-in-git-managed-project-to-previous-state) [^1]