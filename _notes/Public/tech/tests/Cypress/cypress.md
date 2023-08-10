---
title: Cypress
feed: show
tags: javascript tests
date: 06-06-2023
updated: 10-08-2023
type: note
---

### Check an element exists in view

```javascript
cy.get('[data-test-element="element"]').should('exist')
```

### Run Cypress without stopping on first failure

```
cypress run ----auto-cancel-after-failures false --record
```

TBD It may require add configuration parameters in Cypress Cloud.


### Notes
- Write about good practices in Cypress/tests architectures
