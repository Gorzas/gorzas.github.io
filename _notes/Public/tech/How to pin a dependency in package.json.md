---
title: How to pin a dependency in package.json
feed: show
tags: javascript
date: 08-08-2023
updated: 08-08-2023
type: note
growth: seedlings
---

Add the following code into `package.json` file:

```
"resolutions": {
  "dependency": <pinned version>
}
```

### Example
```
"resolutions": {
  "miragejs": "~0.1.46",
  "@embroider/macros": "^1.9.0",
  "@embroider/util": "^1.9.0",
  "ember-cli-babel": "^7.26.1",
  "@fortawesome/fontawesome-svg-core": "1.2.35"
}
```
