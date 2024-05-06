---
title: Deprecate array prototype extensions
feed: show
tags: javascript emberjs
date: 06-05-2024
updated: 06-05-2024
type: note
growth: seedlings
---

## Context

In [[EmberJS]] v5.0, the Array prototype extensions were deprecated. They were needed to adapt Arrays into reactivity system but aren't needed anymore. This included a bunch of customized methods to Arrays, like `mapBy` or `pushObject`, were docs suggest to move to native methods instead or use solutions like [[lodash]].

## Problem

In the docs ([RFC](https://rfcs.emberjs.com/id/0848-deprecate-array-prototype-extensions/), [Deprecation guide](https://deprecations.emberjs.com/ember-data/v4.x#toc_ember-data-deprecate-array-like)) there's lack of info about what's deprecated and how to transition to the new syntax.

## Solution

The issue is because each one of the deprecations is different but both of them have a similar solution and structures affected. All the info about how to migrate to new API could be found in [this link](https://github.com/smilland/deprecation-app/blob/deprecate-array-prototype-extensions/content/ember/v5/deprecate-array-prototype-extensions.md).


## References
- [RFC Deprecate array prototype extensions](https://rfcs.emberjs.com/id/0848-deprecate-array-prototype-extensions/)
- [Ember Deprecations page - Deprecate Array Like](https://deprecations.emberjs.com/ember-data/v4.x#toc_ember-data-deprecate-array-like)
- [Transition to new Array APIs (pending to be merged)](https://github.com/smilland/deprecation-app/blob/deprecate-array-prototype-extensions/content/ember/v5/deprecate-array-prototype-extensions.md)
