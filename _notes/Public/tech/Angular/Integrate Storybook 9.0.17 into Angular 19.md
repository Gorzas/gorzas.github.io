---
title: Integrate Storybook 9.0.17 into Angular 19
feed: show
tags: storybook angular
date: 17-07-2025
updated: 17-07-2025
type: note
growth: seedlings
---

## Problem

There is an [error in the version 9.0.17 of Storybook](https://github.com/storybookjs/storybook/issues/31975) that breaks [Storybook](https://storybook.js.org/) installation into a webapp with [Angular v19](https://angular.dev/) installed. Even when the issue should be fixed in the [last version of @storybook/angular](https://github.com/storybookjs/storybook/pull/32012), this isn't deployed yet and even more errors were showing after fixing this one.

An example of the issue happening (got from the refeered link):

```
[error] Error [ERR_UNSUPPORTED_DIR_IMPORT]: Directory import '/path/to/project/node_modules/@storybook/angular/dist/builders/start-storybook' is not supported resolving ES modules imported from /path/to/project/node_modules/@angular-devkit/architect/node/node-modules-architect-host.js
Did you mean to import "/path/to/project/node_modules/@storybook/angular/dist/builders/start-storybook/index.js"?
    at finalizeResolution (node:internal/modules/esm/resolve:259:11)
    at moduleResolve (node:internal/modules/esm/resolve:933:10)
    at defaultResolve (node:internal/modules/esm/resolve:1169:11)
    at ModuleLoader.defaultResolve (node:internal/modules/esm/loader:542:12)
    at ModuleLoader.resolve (node:internal/modules/esm/loader:510:25)
    at ModuleLoader.getModuleJob (node:internal/modules/esm/loader:239:38)
    at ModuleLoader.import (node:internal/modules/esm/loader:472:34)
    at defaultImportModuleDynamicallyForScript (node:internal/modules/esm/utils:227:31)
    at importModuleDynamicallyCallback (node:internal/modules/esm/utils:249:12)
    at eval (eval at loadEsmModule (/path/to/project/node_modules/@angular-devkit/architect/node/node-modules-architect-host.js:256:14), <anonymous>:3:1)
```

## Solutions

#### Install last version of @storybook/angular.

I used the current last version available of the library, even when it's an alpha version. As not being something the customer is going to use and even (in our case) isn't something that's currently in production (just starting), I can use it without any worries. I add command with [pnpm](https://pnpm.io/) as it's the current package manager using in my current project:

```
pnpm create storybook@9.1.0-alpha.8
```

But this fix didn't work out, it just let me to change the error prompt (so I knew there were some advances but not all the issues were fixed). There were two new errors showing at the same time.

One was about [Chai](https://www.chaijs.com/) library not found:

```
Cannot find namespace 'Chai'
```

The other one was about a non generic type:

```
Type 'Uint8Array' is not generic
```

### Install Chai library and add it into tsconfig

As far as [I have read](https://github.com/storybookjs/storybook/issues/32017), Chai library shouldn't be used in `@storybook/angular` library, but `storybook` core installs it [by default](https://github.com/storybookjs/storybook/blob/v9.0.17/code/core/package.json#L441-L442). [I've suggested to the Storybook team](https://github.com/storybookjs/storybook/issues/32017#issuecomment-3078004209) a possible solution, but as I know very little about both libraries (Storybook and Angular), specially about the internal code and functionality, my suggestion is very possible to not solve the issue.

As a workaround until the core team fixes the issue, [a solution that's working](https://github.com/storybookjs/storybook/issues/32017#issuecomment-3078025114) is to install chai library:

```
 pnpm add -D @types/chai
```

And add Chai configuration into Storybook's `tsconfig' file:

```
"compilerOptions": {
    "types": ["node", "chai"],
    [...]
  },
```

### Add "skipLibCheck": true to fix generic type error

Just today I've found out that [it's a possible bug related with versions <5.7 of TypeScript](https://github.com/mozilla/pdf.js/issues/19152#issuecomment-2654551772), so updating TypeScript and Angular should be enough (I haven't tested it). But, as it's a large application, I can't update Angular or TypeScript without synchronazing with team and it requires a major efford to check everything is still working fine. Anyway, I haven't digged deeper in this issue, so I still don't know what's causing this issue and why it gets fixed this way.

A workaround until we update the base code is to add the following instructions into the `tsconfig` of Storybook. As being part of an internal tool and even not be this into production, there are no major concerns about what I do here:

```
  "compilerOptions": {
    [...]
    "skipLibCheck": true,
    "lib": ["ES2022", "DOM"]
  },
```
