# 08. Team Agreements

This file should become your team's source of truth for workflow decisions.

Without this, people may understand Git individually but still collaborate inconsistently.

## Decisions Worth Making Explicit

- which branch is the default protected branch
- whether work always happens through pull requests
- whether merge commits, squash merges, or rebases are preferred
- whether force-push is allowed on personal branches
- how branch names should look
- how commit messages should look
- what reviewers are expected to check
- when a pull request is ready for review

## Example Agreements

These are starter defaults, not mandatory answers:

- `main` is the protected branch
- direct pushes to `main` are not allowed
- each task gets its own branch
- pull requests should stay focused on one topic
- squash merge is preferred for small, self-contained work
- force-push is allowed only on your own branch and only when no one else depends on it

## Why This Chapter Matters

Many Git problems in teams are really policy ambiguity problems.

When people say "Git is confusing", they often mean:

- I do not know what our team expects
- I do not know which history style we prefer
- I do not know what is safe versus merely possible

