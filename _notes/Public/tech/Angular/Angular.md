---
title: Angular
feed: show
tags: javascript typescript angular
date: 21-01-2025
updated: 03-04-2025
type: note
growth: seedlings
---

## Good practices

- Use [standalone components](https://angular.dev/reference/migrations/standalone) instead of [NgModules](https://angular.dev/guide/ngmodules/overview).
- Use [control flow](https://angular.dev/guide/templates/control-flow) in templates instead of [NgIf](https://angular.dev/api/common/NgIf) directive.
- Use [input](https://angular.dev/guide/components/inputs#configuring-inputs) for passing data parameters to components instead of [@Input](https://angular.dev/guide/components/inputs#declaring-inputs-with-the-input-decorator).
- Use public attributes for components and avoid using `public` keyword to enforce concision. \[*TODO: add references*\]

**TODO**

- How to solve children routing inside standalone components?
- Move Best Practices into specific article

## Issues

- [Angular doesn't support .env files by default](https://vikky.dev/angular-and-environment-files) => R&D best solution to work with .env files

## References
- [Best Practices - Tips for Project Structure and Organization](https://www.thinkitive.com/blog/angular-best-practices-tips-for-project-structure-and-organization/)
- [Angular - Styleguide](https://angular.dev/style-guide)
- [Angular - Prettier configuration](https://medium.com/@sehban.alam/almost-perfect-prettier-settings-for-your-angular-projects-a-step-by-step-guide-f7492943e53d)
