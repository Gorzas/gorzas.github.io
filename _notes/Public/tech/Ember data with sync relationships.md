---
title: Ember data with sync relationships
feed: show
tags: EmberJS JavaScript
date: 20-06-2023
updated: 20-06-2023
type: note 
growth: seedlings 
---

After upgrading [[EmberJS]] from 3.25 to 3.28, I started to have issues with relationships with Ember Data inside Ember Tests. The hasMany relationships were empty.

I have the following configuration:

- Ember v3.28
- [Ember Cli Mirage](https://github.com/miragejs/ember-cli-mirage) v2.0.0
- Ember Data was loading most of the relationships using **sync** loading

### What's sync loading?

In Ember Data, we understand as sync loading when we load a record with all of its relationships.

**Example**

We have a custom webapp with two main resources: posts and categories, and we want to access to **one specific post**. The ideal way in the example to load this data is having **two different** endpoints per resource: `GET /posts/:id:` and `GET /categories`.

In an async way of work, `GET /posts/:id` would look like this using a REST approach:

```json
{
  "post": {
    [data]
    "categories": [1, 2, 3] // categories ids
  }
}
```
*in this case we would require to call `GET /categories` too*

In a **sync way** of work, we would only have one API point for achieve this:

```json
// GET /posts/:id:
{
  "post": {
    [data]
    "categories": [
      {
        "id": 1,
        "label": "tech"
      }
    ] // categories data
  }
}
```

### Working with sync relationships in Ember >3.28

We need to define **serializer** and **model**. Since Ember 3.28, it requires the model to specify when a `hasMany` relationship is **async**.

**serializer**
```javascript
export default class Post extends Serializer {
  attrs = {
    categories: { embedded: 'always' },
  };
```

**model**
```javascript
import Model, { attr, hasMany, belongsTo } from '@ember-data/model';

export default class Post extends Model {
  ...

  @hasMany('categories', { async: false, inverse: null }) categories
```

### Differences between sync and async relationships

From docs:

> In contrast to async relationship, accessing a sync relationship will always return the record (Model instance) for the existing local resource, or **null**. But it will error on access when a related resource is known to exist and it has not been loaded.

This means, **a sync relationship could be empty**, so it needs to be treated with care when accessing to its properties.

### Note

- Using **async** or **sync** relationships in Ember Data depends of the necessities of the webapp. **There isn't an ideal path of work to solve every problem**, it depends of the context of work.

### References
- (Ember Data hasMany docs)[https://api.emberjs.com/ember-data/3.28/functions/@ember-data%2Fmodel/hasMany]
