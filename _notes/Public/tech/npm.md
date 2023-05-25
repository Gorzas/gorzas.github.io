---
title : NPM
feed: show
date : 24-05-2023
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
