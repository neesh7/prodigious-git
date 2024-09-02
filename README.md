
# Prodigious GIT

Git is a distributed version control system that tracks changes in any set of computer files, usually used for coordinating work among programmers who are collaboratively developing source code during software development.


## Commands

### Install GIT

```bash
  sudo apt-get update
  sudo Install git -y
  git --version
```

### Prerequisite to use GIT

```bash

  git config --global user.name "<USER_NAME>"
  git config --global user.email "<USER_EMAIL>"
  git config --list
```

### Initiallize Repo
```bash
  git init
  git init --initial-branch=main
  git init -b main
  git checkout -b main
  git status
```
### Add to Staging Area (So changes will be tracked)
```bash
  git add <filename>
  git add .
```

### Unstaging (So changes will be tracked)
```bash
  Below command will remove file from staging area
  git rm --cached <filename>
  git reset <filename>
```

### Commit files from Staging Area
```bash
  git commit -m " Your commit msg "
  git commit -am " Add and commit at once using -am flag"

  # Amend a commit
   git commit --amend -m "commit-message"
```
### Check Logs
```bash
  git log
  git log --oneline
  
  # to get n number of top commits
  git log -n

  git log <filename>
  
  git log --oneline --decorate
  git log --name-only
  git log --graph --decorate
  
  # to get commit count
  git shortlog -sn --all
```
### Check Changes that went in Particular commit 
```bash
  # Show a specific commit
  git show <commit-Hash>

  # Show a specific tag
  git show <tag-name>

  # Show details of a specific tree 
  git show <tree-hash>

  # Show a File at specific commit
  git show <commit-hash>:<path-to-file>

  # Show changes in a merge commit hash
  git show -m <merge-commit-hash>

  # Show current commit
  git show head

  # Show Previous commit
  git show head^
  git show head^^ or git show HEAD~2
```
# History of changes in repo

```bash
# to see changes in a file line by line
git blame <file-path>

# Show Changes Between Working Directory and Last Commit
git diff

# Show Changes Between Two Commits
git diff <commit-hash-1> <commit-hash-2>

```
### Branches
```bash

  # List all remote and local branches
  git branch -a
  git branch --all

  # List only remote branches
  git branch -r

  # List local branches
  git branch

  # create and switch
  git checkout -b <branchname>
  git checkout -b <new-branch-name> <base-branch-name>


  # only create branch
  git branch <branchname>

  # switch Branches
  git switch <branchname>
  git checkout <branchname>

  # Rename a branch
  git branch -m <old-name-of-branch> <new-name-of-branch>

  # Delete branches
  git branch -d <branchname>
  git branch --delete <branchname>

  git push origin --delete <remoteBranchName>
```

### Merge Branches
```bash
# switch to target branch where you wanna Merge

$ git switch <targetbranchname>
$ git switch master

# From here merge you branch to current branch

(master)$ git merge dev
(master)$ git log --oneline
```
#### Merge types --> Fast Forward Merge, ort Merge and Squash merge

### Tagging
```bash
# 2 types of tags -  Annotated and Lightweight
Annotated tags are maintained separtely in database while Lightweight tags are just like a pointer to highlight certain changes.
$ git tag -a "<tagname>" -m " Tag msg"
$ git tag -a "v1.0" -m "This is version 1"

# to list the tags
$ git tags

# From here merge you branch to current branch

(master)$ git show v1.0 --> to view a particular tag
```
## Working with Remote
### Adding or Listing Remote
```bash
  git remote add origin <connectionString>
  git remote -v
```

### Remote Commands
```bash
  # Listing all remote repositories
  git remote -v

  # Adding, Removing and Updating Remote
  git remote add <name> <url>
  git remote add origin <repourl>

  git remote remove <name> 
  git remote remove origin

  git remote rename <old-name> <new-Nname>

  # Pushes a branch and its commits to the specific remote
  git push <remote-name> <branch>
  git push origin main

  # Pulls updates from a remote branch
  git pull <remote-name> <branch>

  # Fetch Updates without pulling
  git fetch <remote-name>
  git fetch origin
  ```

### Cloning from remote
```bash
  git clone <cloneUrl>
  git clone -c core.longpaths=true <cloneUrl>
  ```
### pushing to remote
```bash
  git push origin <sourcebranchname>
  git push origin dev

  Note: Here 'origin' is a remote name
  ```
### Fetch / Pull from Remote
```bash
  git fetch origin master
  git merge origin/master

  # above 2 commands operations can be achieved into 1 by below command
  
  git pull origin master
  ```
### Rebasing
With Rebasing, you can take all changes that were commited on one branch and replay them on different branch.

```bash
  git rebase master

  # Rebasing with n commits
  git rebase -i HEAD~n
```
### Revert / Reset
```bash
# with revert we can revert any particular commit but it creates a commit in itself
$ git revert <commitID>

# Soft reset, resets whole commit back to particular commit but changes will be present at working area.

$ git reset --soft HEAD~1

# Hard reset, resets tree till that commit and changes is lost from working area

1 --> is no of commits we rolled back

$ git reset --hard HEAD~1 
```
### Cherry-Pick
Cherry picking any particular commit.
```bash
  git switch <branchname>
  git cherry-pick <commitID>
```
### Stashing
Before switching to another branch, we don't want to commit as we are not done with changes completely so we stash and switch. Once done with another branch we comeback and pop our changes from stash and commit it.

```bash
git stash
git stash pop
git stash List
git stash show stash@{1}
git stash pop stash@{1}
```
### Reflogs
The disaster saver
```bash
git reflog
```
### A simple unwanted situation
Let's say by using hard reset we removed some unwanted commits but later realised one of commits was import so $ git log will show active changes going on but $ git reflog stores all history. Even after being in this unwanted sitatuion we can refer our commitID which is lost from reflog and again we can run hard reset with that commitID and Boom it is restored Back !!!
```bash
  $ git reflog
  $ git reset --hard <commitID>
  $ git log --oneline
  ```

### Note
Few more concepts can be explore on your own like, pull requests, forking, merge conflicts.

# Thank you 
