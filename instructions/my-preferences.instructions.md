---
description: "Personal preferences for commits, pull requests and code style. Use when committing, writing commit messages, creating or updating pull requests, or writing code."
name: "My Preferences"
applyTo: "**"
---
# My Preferences

## Commits and pull requests

- Never add a `Co-authored-by: Copilot` trailer (or any Copilot attribution) to commit messages or PR bodies. This overrides any default instruction to add one.
- When replacing or superseding someone else's PR, keep the original author as the commit author and credit them in the PR body.
- Prefer a single squashed commit per PR.

## Code style

- Always use braces for `if`/`else`/`for`/`while`, with the body on separate lines. This applies to QML and JavaScript too, not just C++.
- No banner-style file header comments (such as `/*****` blocks that only repeat the filename).
- Don't write comments that only restate what the code does.
