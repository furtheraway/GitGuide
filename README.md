# GitGuide

A shared Git and GitHub ramp-up guide for collaborators who need a practical, common way of thinking about version control.

## Purpose

This project exists to reduce friction, not to document every Git command.

The guide should help collaborators:

- understand what Git is and what GitHub is
- build a shared mental model for branches, commits, pull requests, merges, and rebases
- follow a team workflow without having to memorize advanced internals first
- recover from common mistakes without panic

## Audience

This guide is for people who:

- are new to Git and GitHub
- have used Git before but still feel uncertain
- need a common vocabulary with teammates
- care more about safe daily collaboration than about mastering every edge case

## Editorial Principles

- Explain concepts in plain language before showing commands.
- Prefer mental models over memorization.
- Teach the day-to-day workflow first, then the exceptions.
- Standardize team vocabulary where ambiguity causes confusion.
- Keep the guide practical: "what it is", "why it matters", "what to do".

## Suggested Reading Order

1. [Guide Index](docs/index.md)
2. [A Shared Mental Model](docs/01-a-shared-mental-model.md)
3. [Git vs GitHub](docs/02-git-vs-github.md)
4. [Core Concepts](docs/03-core-concepts.md)
5. [Daily Workflow](docs/04-daily-workflow.md)
6. [Branches and Pull Requests](docs/05-branches-and-pull-requests.md)
7. [Merge and Rebase](docs/06-merge-and-rebase.md)
8. [Fixing Mistakes](docs/07-fixing-mistakes.md)
9. [Team Agreements](docs/08-team-agreements.md)
10. [Glossary](docs/09-glossary.md)
11. [Command Cheatsheet](docs/10-command-cheatsheet.md)

## Repository Structure

```text
.
|-- README.md
`-- docs/
    |-- index.md
    |-- 01-a-shared-mental-model.md
    |-- 02-git-vs-github.md
    |-- 03-core-concepts.md
    |-- 04-daily-workflow.md
    |-- 05-branches-and-pull-requests.md
    |-- 06-merge-and-rebase.md
    |-- 07-fixing-mistakes.md
    |-- 08-team-agreements.md
    |-- 09-glossary.md
    `-- 10-command-cheatsheet.md
```

## Writing Strategy

The best version of this guide will probably not read like a textbook. It should read like an onboarding companion:

- start with "what is happening"
- then show "what we do on this team"
- then show "what to do when something goes wrong"

That sequence reduces anxiety better than starting with low-level internals.

## Next Drafting Priorities

- write the shared mental model in your own language
- decide your team's preferred workflow before writing detailed command examples
- add screenshots only after the terminology is stable
- keep examples small and realistic

