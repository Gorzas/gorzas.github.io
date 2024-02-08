---
title: NodeJS - Modules
feed: show
tags: javascript node
date: 08-02-2024
updated: 08-02-2024
type: note
growth: seedlings
---

### Context

When using code from other files or dependencies, we need to import them into our files. There are two ways to do it: using CommonJS syntax or ES modules.

#### CommonJS

**Standard in NodeJS**

```javascript
const module = require('module.js);

module.method();
```

#### ES modules

It needs files with `.mjs` extension or `type` to be `module` in package.json with NodeJS >= 13.

```javascript
import { doSomething } from "module";

doSomething();
```

### Questions

- Why does NodeJS requires files to have `.mjs` extension to be imported using import declaration?

### References
- [MDN - import](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)
- [NodeJS - Modules ES6](https://nodejs.org/docs/latest/api/esm.html)
