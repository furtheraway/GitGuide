# 02. Git vs GitHub

This distinction should be explicit because many workflow misunderstandings start here.

## Git

Git is the version control system running on your machine and in repositories shared with others.

Git is responsible for:

- tracking changes
- recording commits
- managing branches
- merging or rebasing history
- syncing history between repositories

## GitHub

GitHub is the hosting and collaboration layer around Git repositories.

GitHub is responsible for:

- repository hosting
- pull requests
- code review discussions
- branch protection and permissions
- issue tracking and project coordination

## Simple Rule Of Thumb

- If you are manipulating history, branches, commits, or sync behavior, that is Git.
- If you are discussing, reviewing, approving, or managing collaboration around changes, that is usually GitHub.

## Why This Matters

People often blame Git for problems that are really workflow or platform issues, and vice versa.

Examples:

- a merge conflict is a Git problem
- an approval rule is a GitHub policy
- a force-push is a Git action with team policy implications
- a pull request review comment is a GitHub discussion attached to Git commits

