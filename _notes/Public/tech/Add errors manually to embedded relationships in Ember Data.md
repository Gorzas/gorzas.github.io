---
title: Add errors manually to embedded relationships in Ember Data
feed: show
tags: JavaScript EmberJS
date: 22-06-2023
updated: 22-06-2023
type: note
growth: buddling 
---

### Issue

> Uncaught Error: Attempted to handle event `becameInvalid` on <model-name:6315DE1CE9DB9CE94775F4D4> while in state root.loaded.saved.

```javascript
log(parent.currentState.stateName); // root.loaded.updated.invalid
parent.children.forEach((child) => log(child.currentState.stateName)); // root.loaded.saved
```

This issue happens when we try to add errors manually to a record (usually, a belongsTo/hasMany relationship) but the record hasn't changed from the API data, so Ember's state machine says the record is valid.

### Solution

In Ember v4.6, the issue would be solved only by upgrading because [state machine is removed from the framework](https://github.com/emberjs/data/pull/7971).

But, if this situation isn't possible, a workaround must be done. It would need to change the state of the record manually before add the errors:

```javascript
model.send('becomeDirty');

model.errors.add(attr, message);
```

### Notes

> I think that Ember Data considers the record in a pristine state and throws that error since it assumes it can't have errors (without local changes) because it is synced with the backend?

- According to a comment in EmberJS Discord, this issue could be fixed in [v4.6.0+](https://blog.emberjs.com/ember-4-6-released).

### References

- [Attempted to handle event `becameInvalid` while in state 'root.loaded.saved' - StackOverflow 2015](https://stackoverflow.com/questions/27698496/attempted-to-handle-event-becameinvalid-while-in-state-root-loaded-saved) *old reference, still working until Ember v4.6*
- [How to manually set an object state to clean (saved) using ember-data](https://stackoverflow.com/questions/13342250/how-to-manually-set-an-object-state-to-clean-saved-using-ember-data/23344215#23344215)
- [PR with Ember state machine removal in v4.6](https://github.com/emberjs/data/pull/7971)
