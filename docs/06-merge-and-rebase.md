# 06. Merge and Rebase

This chapter should remove fear, not just define commands.

## Merge

Merging combines histories by creating a merge commit when needed.

Good beginner framing:

- merge preserves the shape of parallel history
- merge is often the simpler mental model

## Rebase

Rebasing replays commits onto a new base so history appears as if the work started from a later point.

Good beginner framing:

- rebase changes commit history
- rebase can make history cleaner
- rebase requires more care than merge

## Recommended Team Guidance

If your team wants a simple default, this is a reasonable position:

- use pull requests to merge reviewed work into `main`
- allow local rebasing to keep a feature branch current
- avoid rebasing branches that other people are actively using unless everyone understands the consequences

## What This Chapter Should Clarify

- when merge is the safer choice
- when rebase is helpful
- why force-push may appear after a rebase
- why "clean history" and "safe collaboration" need to be balanced

