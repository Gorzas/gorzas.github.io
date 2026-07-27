---
title: git
feed: show
tags: git
date: 03-07-2023
updated: 27-07-2026
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

**TODO** - separate Git from Github tools (in the references are mentioned some Github only tools)

#### Change parent branch

Sometimes it could happen that we have created a branch from _main_ but we need to apply the feature/hotfix into an older branch (e.g. a previous version of the application already deployed to the user).

The command to change the parent branch and avoid all the extra commits that are coming from _main_ is:

```
git rebase --onto <new parent> <old parent> <current branch>
```

**TODO** Do I still differenciate hotfix from bugfix? Is there any difference at all?

## References

- [Husky](https://typicode.github.io/husky/)
- [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)
- [Release Please](https://github.com/googleapis/release-please)
- [Renovate](https://github.com/renovatebot/renovate)
- [Git Cliff: generate changelog](https://git-cliff.org/)
- [Git rebase --onto an overview](https://womanonrails.com/git-rebase-onto)
