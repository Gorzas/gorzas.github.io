---
title : NPM
feed: show
tags: npm
date : 24-05-2023
updated: 18-04-2024
type: note
growth: seedlings
---

## Adding dependency from specific commit

```
"devDependencies": {
  ...
  "external-library": "github.com:<user>/<library>.git#<commit_id>
  ...
}
```

Example:

```
"devDependencies": {
  ...
  "ember-power-select-with-create": "github.com:Gorzas/ember-power-select-with-create.git#278c909427a521b7b6d2770140bf8be983fa21b4",
  ...
}
```

## EACCESS error when global install

```
sudo chown -R $(whoami) $(npm config get prefix)/{lib/node_modules,bin,share}
```
