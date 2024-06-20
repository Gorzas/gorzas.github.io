---
title: git
feed: show
tags: git
date: 03-07-2023
updated: 12-06-2024
type: note
growth: seedlings
---

## Tools

### Husky

A [[JavaScript tools]] to use git hooks in JavaScript projects.

#### Commit without running hooks

Specially useful when it's needed to commit some WIP code.

It needs to use `-n/--no-verify` option:

```bash
git commit -m "WIP" -n
```

**Open questions about Husky**

- What does this tool that doesn't do standard Git hooks?

## References

- [Husky](https://typicode.github.io/husky/)
- [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)

