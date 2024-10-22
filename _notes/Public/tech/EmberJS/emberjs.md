---
title : EmberJS
feed: show
tags: JavaScript framework
date : 30-05-2023
updated: 10-10-2024
type: note
growth: seedlings
---

## Ember Tools

**[Glint](https://typed-ember.gitbook.io/glint)**

Typechecker for Ember templates (Components, Helpers and Modifiers) similar to tsc in [[TypeScript]]. It specially oriented to Glimmer components in TypeScript, but it can work with classic components or using a different [component manager](https://github.com/emberjs/rfcs/blob/master/text/0213-custom-components.md). Also, it could be used with JavaScript but JSDoc types info is recommended (otherwise, it won't do type checking). There is a [VSCode extension](https://marketplace.visualstudio.com/items?itemName=typed-ember.glint-vscode) available allowing features like autocompletiong or link files inside the IDE. 

**[Ember Deploy](http://ember-cli-deploy.com/)**

**TODO** add new syntax about:
- Glimmer (template tags)
- SchemaRecord (and deprecations of Adapters, Serializers, Models and Transforms)
- Embroider? (roadmap?)
- Move Glint to their own article

## Tracked properties

Currently, [tracked properties](https://guides.emberjs.com/release/upgrading/current-edition/tracked-properties/) aren't compatible with [JSON.stringify](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify). This could be a problem in two situations:
- when sending data to an API (it isn't going to send tracked properties)
- when duplicating an object with [JSON.parse(JSON.stringify(o)](https://stackoverflow.com/questions/24744474/json-parsejson-stringifyx-purpose) hack.

A possible solution to this issue could be to add the following code inside the base class with tracked properties:

```javascript
export class BaseClass {
   toJSON() {
        // fields that are @tracked don't work with JSON, fix that. https://github.com/ember-learn/guides-source/issues/1138
        // Implemented based off of this https://stackoverflow.com/a/50785428/1148118
        const jsonObj = Object.assign({}, this);
        const proto = Object.getPrototypeOf(this);
        for (const key of Object.getOwnPropertyNames(proto)) {
            const desc = Object.getOwnPropertyDescriptor(proto, key);
            const hasGetter = desc && typeof desc.get === 'function';
            if (hasGetter) {
                jsonObj[key] = this[key];
            }
        }
        return jsonObj;
    }
}
```
[Source](https://github.com/ember-learn/guides-source/issues/1138)

### TODO

- Further work about cloning an object could be required (like creating a util function to do this same behaviour instead a patched inner method to the class).
- A better solution when sending data to the API could be to use Ember Data and Ember Data Models attributes. But, as currently Ember Data Models are in the path of deprecation, more research could be needed about it.
- Regarding [[Digital Gardens]], this text could require its own note and reorganization work.

## Typical issues

- [[Deprecate array prototype extensions]]

### Links to review
- [Ember Roadmap: from @action to arrow functions](https://github.com/emberjs/rfcs/pull/1045)

### Important Resources

- [Ember Primitives](https://ember-primitives.pages.dev/)
- [Glimmer tutorial](https://tutorial.glimdown.com/)

### References
- [Ember upgrade](https://cli.emberjs.com/release/basic-use/upgrading/)
- [Using Ember Template tag](https://guides.emberjs.com/release/components/template-tag-format/)
- [Octane @tracked properties in native classes models do not JSON.stringify](https://github.com/ember-learn/guides-source/issues/1138)
