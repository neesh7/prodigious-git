
# Prodigious GIT

Git is a distributed version control system that tracks changes in any set of computer files, usually used for coordinating work among programmers who are collaboratively developing source code during software development.


## Commands

### Install GIT

```bash
  sudo apt-get update
  sudo Install git -y
  git --version
```
### Initiallize Repo
```bash
  git init
  git status
```
### Add to Staging Area (So changes will be tracked)
```bash
  git add <filename>
  git add .
```
### Commit files from Staging Area
```bash
  git commit -m " Your commit msg "
  git commit -am " Add and commit at once using -am flag"
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
  git show <commit-Hash>
```

### Branches
```bash

  # List all remote and local branches
  git branch -a

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
  git branch <old-name-of-branch> <new-name-of-branch>

  # Delete branches
  git branch -d <branchname>
  git branch --delete <branchname>
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
## Working with Remote
### Adding or Listing Remote
```bash
  git remote add origin <connectionString>
  git remote -v
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