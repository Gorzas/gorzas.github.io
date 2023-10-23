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

### Waiting for side effects doesn't happen

Using `cy.wait(Number)` is a [bad practice according Cypress documentation](https://docs.cypress.io/guides/references/best-practices#Unnecessary-Waiting).

Imagine we have the following use case:
- we are waiting to a Promise that isn't dependable of an API query
- we are checking that some side effect hasn't happened

For example, checking that a flash message hasn't appeared after saving doing an action in a webapp. The flash message is shown under a Promise (it has a timeout) so waiting for the API isn't enough. And, as we want to check nothing has happened, the test is going to pass wrongly always as we do the check just after the API has success.

In this case, it's ok to do the following in a Cypress:
```
// eslint-disable-next-line cypress/no-unnecessary-waiting
cy.wait(TIMEOUT_FLASH_MESSAGE);

cy.get('[data-test-data="element"]', {
  timeout: 0,
}).should("not.exist");
```

### Notes
- Write about good practices in Cypress/tests architectures

### References

- [Best practices - Unnecessary Waiting](https://docs.cypress.io/guides/references/best-practices#Unnecessary-Waiting)
