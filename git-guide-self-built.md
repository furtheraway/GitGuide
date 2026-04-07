# Git, GitHub, and Workflow

## What Is Git

`Git` is a local tool you install on your PC which help you keep track of changes in a code projects. Git organize each project as a folder (including all its subfolders). Once you run command `git init` in a particular folder, Git starts a repository within this folder, which will include all the files in this folder and its subfolders and the change histories for each file.

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


- **Worktree / working tree** :  the actual directory of files you see and edit on disk.

- **Index (also called the Staging area)** is an intermediate snapshot of your project that sits between your working files and the next commit. It's where you prepared your next commit. It can contain only part of the last batch of work (you may organize certain edits into one commit, and save the rest for the next commit.)



    ```text
    Working directory (your files)
    ↓
    ↓  <- git add .
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





## When code start diverge (main and feature branch)

At first, you keep developing the code base and creating commits one by one, each commit is the parent of the commit following it, and you get linear history. Often this linear history is your main development line, usually called `main`.

After some commits, you release the current version at one commit location.

Now you want to try a new feature, but you do not want to disturb the released code on `main`. So you create another branch from the latest commit on the main develop line.

- **Branch**: a symbolic pointer to a commit in Git history.

- **main**: usually the default branch name in a repository.

- **HEAD**: a special pointer that tells Git what branch or commit you are currently on.

A branch does not copy the whole repository. It is just a name that points to one commit.

When new commits are created on that branch, the branch pointer moves forward to the new latest commit.

When you are working on `main`, `HEAD` points to `main`.

```text
HEAD -> main -> C
```

If you create a new commit while `HEAD` is on `main`, `main` moves forward to the new commit.

```text
HEAD -> main -> D
```

Example:

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

