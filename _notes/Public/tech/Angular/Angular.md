---
title: Angular
feed: show
tags: javascript typescript angular
date: 21-01-2025
updated: 07-05-2025
type: note
growth: seedlings
---

## Good practices

- Use [standalone components](https://angular.dev/reference/migrations/standalone) instead of [NgModules](https://angular.dev/guide/ngmodules/overview).
- Use [control flow](https://angular.dev/guide/templates/control-flow) in templates instead of [NgIf](https://angular.dev/api/common/NgIf) directive.
- Use [input](https://angular.dev/guide/components/inputs#configuring-inputs) for passing data parameters to components instead of [@Input](https://angular.dev/guide/components/inputs#declaring-inputs-with-the-input-decorator).
- Use public attributes for components and avoid using `public` keyword to enforce concision. \[*TODO: add references*\]

## The future of Angular

- There are talks about removing `ngOnInit` lifecycle hook but further investigation needs to be done about this. [More info](https://angular.love/component-initialization-without-ngoninit-with-async-pipes-for-observables-and-ngonchanges)

**TODO**

- How to solve children routing inside standalone components?
- Move Best Practices into specific article

## Signals

**TODO** Move to an independent post.

- [Angular Signals: Best practices around exposing Signals](https://blog.angulartraining.com/angular-signals-best-practices-around-exposing-signals-5385452150a1)

## Moving a native fetch into an RxJS Observable

**TODO** create an specific RxJS page
**TODO** create an specific page for this issue

```
return new Observable((observer: Subscriber<T>) => {
  fetch(url)
    .then((response) => response.json())
    .then((data) => {
      observer.next(data);
      observer.complete();
    })
    .catch((err) => observer.error(err));
});
```

## Issues

- [Angular doesn't support .env files by default](https://vikky.dev/angular-and-environment-files) => R&D best solution to work with .env files

## References
- [Best Practices - Tips for Project Structure and Organization](https://www.thinkitive.com/blog/angular-best-practices-tips-for-project-structure-and-organization/)
- [Angular - Styleguide](https://angular.dev/style-guide)
- [Angular - Prettier configuration](https://medium.com/@sehban.alam/almost-perfect-prettier-settings-for-your-angular-projects-a-step-by-step-guide-f7492943e53d)
