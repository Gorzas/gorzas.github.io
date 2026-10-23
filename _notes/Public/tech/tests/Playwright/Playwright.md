---
title: Playwright
feed: show
tags: test typescript
created: 07-10-2026
updated: 23-10-2026
type: note
growth: seedlings
---

## Good practices

### Usage of getByRole

The recommended path for accessing data of the DOM is using `getByRole` instead of using old ways to access data like `data-test` attributes or even using specific ids or class names (like `test-` prefixes or any other strategy the team has).

An example of accessing an input element in the DOM using `getByRole`:

```
await page.getByRole('checkbox', { name: 'Subscribe' }).check();
```

Using `getByRole` allows the developer to use the page as an user with assistive technology browsers the application. This way is an **early way to find accessibility issues** in the application. [[Playwright]] docs also advises that this doesn't replaces accessibility tests.


## References

- [Playwright Docs - Locate by role](https://playwright.dev/docs/locators#locate-by-role)
- [17 Playwright Best Practices That Actually Matter in QA](https://testdino.com/blog/playwright-best-practices)
