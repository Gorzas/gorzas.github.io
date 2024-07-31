---
title: Debug a native JavaScript method
feed: show
tags:
  - javascript
date: 18-07-2023
updated: 31-07-2024
type: note
growth: seedlings
---

Write in the Chrome Inspector / Firefox Developer Tools:

```javascript
debuggingMethod = window.debugginMethod;

window.debuggingMethod = function (...arguments) {
  console.trace(arguments); // console.log
  debuggingMethod.apply(window, arguments);
}
```

- Use `function` better than `arrow function` to avoid undesired scope changes.

### Example

```javascript
replaceState = window.history.replaceState;

window.history.replaceState = function (...arguments) {
  console.trace(arguments);
  replaceState.apply(window.history, arguments);
}
```
