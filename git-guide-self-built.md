# Git, GitHub, and Workflow

## What Is Git

`Git` is a local tool you install on your PC which help you keep track of changes in a code project. Git organize each project as a folder (including all its subfolders). Once you run command `git init` in a particular folder, Git starts a repository within this folder, which will include all the files in this folder and its subfolders and the change histories for each file.

It is normal for Git to feel abstract at first. To understand how Git actually records and manages history within a folder/repository. We start with some fundamental concepts in Git:

- **Git repository/repo** : refers to a project folder with all its contents and change histories.
  
- **Commit**: History is recorded by Git as commits. Each commit is a full screenshot of the contents of project folder at a given time. 
  
  Believe it or not, a commit has everything, a full screenshot of the folder, not just the incremental, at the time the commit is created. (except those specified to be ignored in a repository setting file `.gitignore`). But you should create as many commits as you'd like without worrying over-growing repo size, since Git compress the storage of commits by their incremental changes.

  However, this effective compression for storage only happens to pure text files (code files like .cs .py .txt etc.). Binary files like docx, Excel, PPT, PDF, do not have this benefits, since Git cannot compare their changes. If you store binary files in Git and change them often. The repository size can grow very big.

  When git initial a repository, it creates a hidden subfolder `.git` which stores everything git needs to remember the history of this repository. If you simply delete this folder, you wipe out the history and the folder will no longer be recognized by Git as a managed repository.


## How to do version control with Git Commit

After you initiate a repo in a project folder with `git init`, you start building the project by adding code files. After certain amount of work, you are ready to save the first screenshot (commit) of the project. Here is what you would do:

Before creating a commit, you first choose which changes to include, and stage them into a **staging area** called **index**. Then you run command `git commit` with a message to turn the staging area into a commit.

```bash
git add <file-name>  // add certain file to staging area. Or
git add .            // add all files to staging area. more commonly used.

git commit -m "your commit message"
```

`git add` puts your selected file changes into the staging area, i.e. Index.

`git commit` creates a new commit from what is currently in the index.


- **Commit message**: a short text that describes what this commit is about.


- **Worktree / working tree** :  the actual directory of files you see and edit on disk. I can be identical to the Index (staging area), but once you start editing files, it will differ from staging area, until next time you run `git add .` which add all files in `working tree` to index. Once Index is changed, it differs from the commit where HEAD is pointing to, until you commit your stage area to a new commit, then last commit and and index become identical. Note here, the index (staging area is not emptied, it just have no difference/changes from the commit snapshot.)

- **Index (also called the Staging area)** is an intermediate snapshot of your project that sits between your working files and the next commit. It's where you prepared your next commit. It can contain only part of the last batch of work (you may organize certain edits into Index for the next coming commit, and save the rest for a future commit.)
  

Git has three key layers:

1. HEAD (current commit / branch pointer)
2. Index (staged snapshot, to be created as next commit)
3. Working directory (your files on disk)



    ```text
    Working directory (your files)
    ↓
    ↓  <- git add .    (dot . matches all file and subfolders)
    ↓
    Index (staging area)
    ↓
    ↓  <- git commit -m 'message'
    ↓
    Repository (commits / HEAD)
    ```

So each snapshot in Git history is created by a **Edit/Stage/Commit** mini workflow. 

Note: Directly working with git commands can be confusing. We recommend using your IDE (like Visual Studio or VS Code) UI in creating commits.



After a while working in the project by yourself, you will likely get a line of commit history:


  ```text
  A1B2C3D ------> E4F5G6H -----> 8A9B0C1 -----> x28nsiusn
  1st commit      add login      fix bug        add feature xxx
  ```

Each commit also has its own unique hash ID. This is the long string of letters and numbers Git uses to identify that commit. A commit also saves the commit message and the author and time of creation.

You can go back (restore) the working directory to any of the commits in the history. This is the power of Git!



## When code start diverge (main and feature branch)

At first, you keep developing the code base and creating commits one by one, each commit is the parent of the commit following it, and you get a linear history. Often this linear history is your main development line, usually called `main`.

```text
A ---- B ---- C (main)
```

After some commits, you release the current version at one commit location.

Now you want to try a new feature, but you do not want to disturb the released code on `main`. So you create another branch from the latest commit on the main develop line.

- **Branch**: a symbolic pointer to a commit in Git history.

- **main**: usually the default branch name in a repository. (this main or master branch, the name suggested something special, like the confusing remote named 'origin', but they are just the name of a branch or pointer, it can be anything, nothing specially about it. But you do want to name your branches according to their intended purpose in the Git workflow you adapt).

- **HEAD**: a special pointer that tells Git what branch or commit you are currently on (your working folder is in the snapshot state of that commit). When you are working on `main`, `HEAD` points to `main`.

A branch does not copy the whole repository. It is just a name/label that points to a commit.

```text
A ---- B ---- C (main <- HEAD)
```

If you create a new commit while `HEAD` is on `main`, `main` moves forward to the new commit.

```text
A ---- B ---- C ---- D (main <- HEAD)
```

After create a new branch called "feature-x", and "checkout" it. 

```text
main:    A ---- B ---- C
                       ^
                    released
```

Then a new feature branch is created from commit `C`:

```text
main:    A ---- B ---- C
                       \
feature-x:              D ---- E
```

Now the code history has diverged.

`main` still points to commit `C`.

`feature-x` points to commit `E`.

If you switch to `feature-x`, then `HEAD` points to `feature-x` instead.

```text
main            -> C
HEAD -> feature-x -> E
```

This is why Git history is not always one straight line. It can become a tree.


## What git cherry-pick is

git cherry-pick takes the changes introduced by a specific commit and applies them as a new commit on your current branch.

It does not move or copy the original commit. It creates a new commit with:

- the same changes (diff)
- a different commit hash
- a different parent (your current branch)


## How to use reset to squash history commits





```text
A ---- B ---- C ---- D (main <- HEAD)
```

### better to think of Git history as a graph of connected dots(commits, snapshots) than different lines of branches, since branch is just a pointer to a commit in the graph. The connected commits are directional, each commit has its parent (most commits have one parent, merge commit have two, squash merge has one.)

why we focus on commit instead of a branch? since a commit can be involved in the history of multiple branch lines. E.g, if you merge branch B into branch A (you can do this only when you are on branch A, i.e. A is checked out), then the newly created merge commit M will be where branch A (and the HEAD) now pointing to. Branch B still point to where it was.

Git merge should be read as "merge branch B **into** A" or "merge branch A **into** B", not "merge branch A **and** B". It is directional. `merge B into A` and `merge A into B` will produce different commits even though there is no conflicts in merge. If you `merge B into A`, which produce a merge commit M1 on branch A (git only move the current branch pointer, B is not aware about M1 yet), and then immediately `merge A into B`, it will fast forward B to M1 (now both A).

### Traditional merge has two parents commits, and the newly create merge commit carries history from both parents with it. But squash merge only has one parent, the commit where `merge --squash` is called. (remember branch is just a pointer to a commit.)


### When we merge two commits(branches), particularly when we `--allow-unrelated-histories`, we should not expect Git make it just work, we need to resolve conflicts (if not resolved, that conflict section will be missing), and we even need to inspect all the auto-merged sections!!(in one forced un-related history merge, we observed that old old old deleted sections come back into the merge result. Not surprisingly, its unrelated history. That's probably the reason git all auto commit by default if there is no conflict.)

### in VS Git UI, show commit details != compare two commits, particularly in a merge. 

Talk about the differences between `git reset` and `git checkout`
* git reset → moves the branch to a commit
* git checkout → moves your working position to a commit (possibly detaching HEAD)

---
---
---


## Commands to be used in the workflow charts




--


```bash
# Merge a remote branch to local

git fetch <remote-name>  # fetch commit history from a remote to local, which is basically updating local knowledge about the state of the remote, very safe operation. e.g. git fetch gitlab

git branch -r

git checkout main  # you can only merge to the branch you are currently on, so we need to checkout the target branch first.

git merge <remote-name>/<branch>

git merge gitlab/main
```


```bash
# add, view, and push to a remote

# git remote add <name> <url>
git remote add origin https://github.com/user/repo.git 
# origin as a remote name can actually be a very confusing, we recommend name it where it is hosted, like GitHub, Github1, gitlab etc. 
git remote add gitlab https://gitlab.com/user/repo.git

# push a local branch to remote
git push <remote-name> <local-branch-name>:<remote-branch-name> # full syntax
git push gitlab main # is short for
git push gitlab main:main # When you omit :<remote-branch>, Git assumes: push the local branch to a remote branch of the same name (main here)
# Unlike 'git merge' only let you merge into your current branch, 'git push' don't care which local branch you're on. You always need to specify which branch to push.



Your current branch = irrelevant

# merge a remote branch into local current branch
git fetch <remote-name>
git merge <remote-name>/<remote-branch-name>


# display remotes configured
git remote -v
git remote show <remote-name>

# show which local branch is tracked with which remote branch
git branch -vv

```

```bash
# How to squash a branch into a new squashed branch

O---A---B---C---D  main

git switch -c <squashed-branch-name> # create and switch to a new branch pointing to the same commit your current branch is on.
git reset --soft O # reset the newly created branch to a old commit
git commit -m "Squashed A-D" # created a new squashed commit S

# it produce
O---S           new-branch
 \
  A---B---C---D main


```

```bash
# Some tricks

git diff <commit1> <commit2>

git diff --stat main feature # --stat shows summary # then inspect individual files with diff.


# Testing a merge without committing

git switch main
git merge --no-commit --no-ff feature
git merge --abort

```

```bash
# squash merge

git merge --squash feature # A squash merge does not create a commit automatically.

git commit  -m "Squashed changes from feature" # you must commit manually after inspection.
```


```bash
# fast-forward in merge happens

git checkout main
git merger feature

# will result both main and feature branches point to D, and no new merge commit created.

main:    A ── B
feature:       └── C ── D

```

