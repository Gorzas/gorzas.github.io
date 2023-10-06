---
title: Cypress
feed: show
tags: javascript tests
date: 06-06-2023
updated: 04-10-2023
type: note
---

### Common commands in Cypres

**Type in an input**

```javascript
cy.get('[data-test-input="input"]').type('Example text')
```

**Assert sent data to API**
```javascript
cy.intercept(
  {
    pathname: "/categories",
    method: "POST",
  },
  (req) => {
    const {
      body: { category },
    } = req;

    expect(category.name).to.be.equal("Name");

    req.reply({
      body: { category: { id: "1" } },
    });
  }
);
```


### Check an element exists in view

```javascript
cy.get('[data-test-element="element"]').should('exist')
```

### Run Cypress without stopping on first failure

```
cypress run ----auto-cancel-after-failures false --record
```

TBD It may require add configuration parameters in Cypress Cloud.

### Load an static JSON fixture in an intercept

A real use case could be that we have two intercepts: one for collection and a different one for the specific element; and we want to retrieve the specific element from the collection JSON to avoid code repetition.

```
cy.fixture("blog/posts").then((json) => {
  cy.intercept(
    {
      pathname:
        "/blog/post/1",
      method: "GET",
    },
    (req) => {
      req.reply({ post: json.posts[0] });
    }
  );
});
```

### Notes
- Write about good practices in Cypress/tests architectures
