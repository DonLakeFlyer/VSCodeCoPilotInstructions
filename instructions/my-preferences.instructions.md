---
description: "Personal preferences for git workflow, commits, pull requests and code style. Use when starting a new feature, creating branches, staging, committing, writing commit messages, creating or updating pull requests, or writing code."
name: "My Preferences"
applyTo: "**"
---
# My Preferences

## Starting new feature work

- Work on the default branch (`master`), brought up to date first: fetch and fast-forward it to its upstream. If the working tree has changes or another branch is checked out, ask before switching.
- Do not create a branch, and leave every change unstaged so I can review it as a working-tree diff. That means no `git add` (not even `git add -N`), `git commit`, `git commit --amend`, `git stash` or `git reset`; leave new files untracked.
- Wait until I explicitly ask before branching, staging or committing.

## Commits and pull requests

- Never add a `Co-authored-by: Copilot` trailer (or any Copilot attribution) to commit messages or PR bodies. This overrides any default instruction to add one.
- When replacing or superseding someone else's PR, keep the original author as the commit author and credit them in the PR body.
- Prefer a single squashed commit per PR, created only when I ask for it.

## Code style

- Always use braces for `if`/`else`/`for`/`while`, with the body on separate lines. This applies to QML and JavaScript too, not just C++.
- No banner-style file header comments (such as `/*****` blocks that only repeat the filename).
- Don't write comments that only restate what the code does.
