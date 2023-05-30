---
title : Running rendering tests with Ember Engines and Mirage
feed: show
tags: JavaScript framework
date : 30-05-2023
---

When upgrading from [[EmberJS]] 3.25 to 4.X, I removed old code deprecations and I have the following error while running `ember t -s`:

> This test relies on a deprecated test setup that is no longer supported by EmberData. To resolve this you will need to be on a recent version of @ember/test-helpers AND your tests must use `setApplication()` instead of `setResolver()` and `module()` with `setup*Test()`instead of `moduleFor*()`. [deprecation id: ember-data:legacy-test-helper-support]

### Problem

There's no much information in Google about this issue. [Documentation is currently outdated](https://ember-engines.com/docs/testing-integration) and error prompt doesn't give any clue about how to fix it.

### Solution

The usage of `engineResolverFor` [it was deprecated](https://github.com/ember-engines/ember-engines/pull/812/files) in `ember-engines: v.0.9.0` and it has incompatibility issues with latest versions of [[EmberJS]]. The new API for testing engines was in [this thread](https://github.com/ember-engines/ember-engines/pull/653) but there wasn't no info in the official docs.

To solve it:
- remove the usage of `engineResolverFor`
- use new `setupEngine` API.

**before**

```javascript
import { module, test } from 'qunit';
import { setupRenderingTest } from 'ember-qunit';
import hbs from 'htmlbars-inline-precompile';
import engineResolverFor from 'ember-engines/test-support/engine-resolver-for';

const modulePrefix = 'my-engine';
const resolver = engineResolverFor(modulePrefix);

module('Integration | Component | example-component', function (hooks) {
  setupRenderingTest(hooks, { resolver });
  setupMirage(hooks);

  test('...', async function(assert) {
```

**after**

```javascript
import { module, test } from 'qunit';
import { setupRenderingTest } from 'ember-qunit';
import { render, click } from '@ember/test-helpers';
import hbs from 'htmlbars-inline-precompile';
import { setupEngine } from 'ember-engines/test-support';

const modulePrefix = 'my-engine';

module('Integration | Component | example-component', function (hooks) {
  setupRenderingTest(hooks);
  setupEngine(hooks, modulePrefix);
  setupMirage(hooks);

  test('...', async function(assert) {
```
