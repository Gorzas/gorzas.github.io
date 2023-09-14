---
title: Observe attribute has changed
feed: show
tags: javascript debug
date: 14-09-2023
updated: 14-09-2023
type: note
growth: seedlings
---

## Context

Sometimes we could have `async` functions in our code with parameters that could be modified as a side effect in a different function. This is usually a result of a **bad architecture** in the code but we would need to debug the attribute and know where the object is changed.

An code example with this particular issue:

```javascript
async extractErrors(payload) {
  console.log(payload.errors); // [{ statusCode: '422' ... }]

  await anotherAsyncFunction() // it doesn't change "payload" or "payload.errors"

  console.log(payload.errors); // []

  return payload.errors;
}
```

As you can see in the code above, we see that `payload.errors` is an array with one element but it suddenly gets clear. We need to know where does it get modified in the code. In small apps, could be very simple but in large size applications it could require a lot of debugging to find the issue.

### Solution

We can override `errors` property to debug the code and finde where is the architecture issue. This way, we can refactor the code and avoid future situations like this.

An example of the code (for debugging purposes only):

```javascript
async extractErrors(payload) {
  Object.defineProperty(payload, 'errors', {
      set: function(val){
        // you can use:
        // debugger;
        // or
        // console.log(val);
      }
    // no need for a getter, we only need to find the "bad guy" here
  });

  await anotherAsyncFunction();

  return payload.errors;
}
```
