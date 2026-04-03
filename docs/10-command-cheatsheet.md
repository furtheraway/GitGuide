# 10. Command Cheatsheet

This file should stay secondary to the conceptual chapters.

Commands make more sense after the workflow is clear.

## Start New Work

```bash
git switch main
git pull
git switch -c my-topic-branch
```

## Save Progress

```bash
git status
git add .
git commit -m "Describe the change"
```

## Share Work

```bash
git push -u origin my-topic-branch
```

## Update Your Branch

```bash
git fetch origin
git merge origin/main
```

Alternative if your team is comfortable with rebase:

```bash
git fetch origin
git rebase origin/main
```

## Inspect State

```bash
git status
git log --oneline --graph --decorate
git diff
```

## Fix Simple Mistakes

```bash
git restore .
git restore --staged .
git commit --amend
git revert <commit>
```

## Note

When you expand this cheatsheet, keep each command tied to a scenario and a risk level. That makes it more useful than a flat list.

