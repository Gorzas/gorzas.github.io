---
title: Add errors manually to embedded relationships in Ember Data
feed: show
tags: JavaScript EmberJS
date: 22-06-2023
updated: 22-06-2023
type: note
growth: seedlings
---

### Issue

> Uncaught Error: Attempted to handle event `becameInvalid` on <model-name:6315DE1CE9DB9CE94775F4D4> while in state root.loaded.saved.

```javascript
log(parent.currentState.stateName); // root.loaded.updated.invalid
parent.children.forEach((child) => log(child.currentState.stateName)); // root.loaded.saved
```

### Notes

> I think that Ember Data considers the record in a pristine state and throws that error since it assumes it can't have errors (without local changes) because it is synced with the backend?

- According to a comment in EmberJS Discord, this issue could be fixed in (v4.6.0+)[https://blog.emberjs.com/ember-4-6-released].

### References

- (Attempted to handle event `becameInvalid` while in state 'root.loaded.saved' - StackOverflow 2015)[https://stackoverflow.com/questions/27698496/attempted-to-handle-event-becameinvalid-while-in-state-root-loaded-saved] *old reference*
