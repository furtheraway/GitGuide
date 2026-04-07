# Git, GitHub, and Workflow

## What Is Git

`Git` is a local tool you install on your PC which help you keep track of changes in a code projects. Git organize each project as a folder (including all its subfolders). Once you run command `git init` in a particular folder, Git starts a repository within this folder, which will include all the files in this folder and its subfolders and the change histories for each file.

It is normal for Git to feel abstract at first. To understand how Git actually records and manages history within a folder/repository. We start with some fundamental concepts in Git:

- **Git repository/repo** : refers to a project folder with all its contents and change histories.
  
- **Commit**: History is recorded by Git as commits. Each commit is a full screenshot of the contents of project folder at a given time. 
  
  Believe it or not, a commit has everything, a full screenshot of the folder, not just the incremental, at the time the commit is created. (except those specified to be ignored in a repository setting file `.gitignore`). But you should create as many commits as you'd like without worrying over-growing repo size, since Git compress the storage of commits by their incremental changes.

  However, this effective compression for storage only happens to pure text files (code files like .cs .py .txt etc.). Binary files like docx, Excel, PPT, PDF, do not have this benefits, since Git cannot compare their changes. If you store binary files in Git and change them often. The repository size can grow very big.

  When git initial a repository, it creates a hidden subfolder `.git` which stores everything git needs to remember the history of this repository. If you simply delete this folder, you wipe out the history and the folder will no longer be recognized by Git as a managed repository.


    ### How a Commit is created?



- **Worktree / working tree** :  the actual directory of files you see and edit on disk.

- **Index (also called the Staging area)** is an intermediate snapshot of your project that sits between your working files and the next commit. It's where you prepared your next commit.



    ```text
    Working directory (your files)
    ↓
    Index (staging area)
    ↓
    Repository (commits / HEAD)
    ```


