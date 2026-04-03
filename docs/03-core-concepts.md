# 03. Core Concepts

This chapter should define the minimum vocabulary the team uses consistently.

## Working Tree

Your working tree is the set of files currently checked out on your machine.

## Staging Area

The staging area is where you prepare exactly what will go into the next commit.

This concept deserves extra care because many beginners skip it mentally and then do not understand why commits contain certain changes.

## Commit

A commit is a saved snapshot of staged changes, along with metadata such as author, timestamp, and message.

## Branch

A branch is a name pointing to a line of commits.

Useful phrasing for beginners:

- a branch is lightweight
- a branch moves forward as new commits are added
- switching branches changes which line of work your files reflect

## Remote

A remote is another repository Git can communicate with, such as `origin`.

## Push And Pull

- `push` sends local commits to a remote repository
- `pull` updates your local branch from a remote branch, usually by fetching and then integrating changes

## Pull Request

A pull request is a GitHub request to review and merge one branch into another.

## Recommended Teaching Order

1. working tree
2. staging area
3. commit
4. branch
5. remote
6. push and pull
7. pull request

