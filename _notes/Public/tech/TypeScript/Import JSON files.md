---
title: Import JSON files
feed: show
tags: typescript
date: 15-05-2024
updated: 15-05-2024
type: note
growth: buddling
---

## Problem

[[TypeScript]] doesn't support by default resolving JSON modules because it needs to infer the static type of the JSON file. In [[NodeJS]] projects, it's common practice to import static JSON files so this could bring us to a situation of linting errors.

An example of the error shown:

```
Cannot find module './settings.json'. Consider using '--resolveJsonModule' to import module with '.json' extension.
```

In the [documentation](https://www.typescriptlang.org/tsconfig/#resolveJsonModule) there isn't a clear example of how to solve this issue.

## Solution

Update the `tsconfig.json` with the parameter `resolveJsonModule` set to `true`.

```
// tsconfig.json
{
  "compilerOptions": {
    // ...
    "resolveJsonModule": true,
    // ...
  },
  "include": [
    // ...
  ]
}
```

## References

- [TSConfig - resolveJsonModule](https://www.typescriptlang.org/tsconfig/#resolveJsonModule)
