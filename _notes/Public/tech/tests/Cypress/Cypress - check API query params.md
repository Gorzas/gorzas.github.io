---
title: Check API query params on Cypress
feed: show
tags: cypress javascript
date: 20-11-2023
updated: 20-11-2023
type: note
growth: seedlings
---

## Context

When developing a new feature in frontend, sometimes we want to assert that the data sent to the API is valid, not only the effects after the API is resolved.

In [[Cypress]], we can intercept the API with the following syntax:

```javascript
cy.intercept(
  {
    pathname: "/api/posts",
    method: "POST",
  },
  { fixture: "api/post" } // JSON fixture
).as("createPost");
```

We usually use the same intercept syntax to a test suite, so we don't want to override it lots of times.

## Solutions

When we are using the same `intercept` syntax in a test suite or in different test files, the best approach is the following syntax:

```javascript
cy.wait("@createPost").then(({ request }) => {
  expect(request.query).to.have.property("submit");
});
```

## TODO
- What could be a solution for test query params when the API isn't intercepted? (proper E2E tests against staging) Is it needed?
- Add syntax for checking query params inside intercept syntax.
