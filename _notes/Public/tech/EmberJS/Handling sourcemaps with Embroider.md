---
title: Handling sourcemaps with Embroider
feed: show
tags: javascript embroider emberjs
date: 09-10-2024
updated: 09-10-2024
type: note
growth: seedlings
---

## Context

In [[EmberJS]], they have replaced [Broccoli](https://github.com/broccolijs/broccoli) compilating library for [Embroider](https://github.com/embroider-build/embroider) that uses [WebPack](https://webpack.js.org/) internally.

## Problem

The interface for handling source maps in the [[EmberJS]] builder has changed, even when the old interface is still compatible with the current versions of [Embroider](https://github.com/embroider-build/embroider):

```
let app = new EmberApp(defaults, {
  sourcemaps: {
    enabled: false
  }
});
```

## Solution

We need to start using the new interface for handling source maps, it responds to [WebPack API](https://webpack.js.org/configuration/devtool/):

```
const { Webpack } = require('@embroider/webpack');
return require('@embroider/compat').compatBuild(app, Webpack, {
  packagerOptions: {
    webpackConfig: {
      devtool: false 
    }
  }
});
```

## References

- [HTTP Header Sourcemap](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/SourceMap)
- [Use a sourcemap](https://firefox-source-docs.mozilla.org/devtools-user/debugger/how_to/use_a_source_map/index.html)
- [WebPack - devtool DOCS](https://webpack.js.org/configuration/devtool/)
- [Embroider](https://github.com/embroider-build/embroider)
