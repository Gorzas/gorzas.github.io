---
title: HTML to PDF
feed: show
tags: html java
created: 01-10-2026
updated: 01-10-2026
type: note
growth: seedlings
---

### Working with openhtmltopdf

I'm currently working with [openhtmltopdf](https://github.com/danfickle/openhtmltopdf) in [[Java]] to create a PDF using an [[HTML]] template (the base platform is an [[Apache Velocity]] template).

The tool I'm using has some characteristics that only apply to it but not a general rule.

#### Uses deprecated CSS rules

The [new CSS rules for fragmentation](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Fragmentation) doesn't work with [openhtmltopdf](https://github.com/danfickle/openhtmltopdf).

Instead, I have to use the old ones: [page-break-after](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/page-break-after), [page-break-before](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/page-break-before) and [page-break-inside](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/page-break-inside).

I unknown the compatibility with [other rules](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/box-decoration-break) related with fragmentation.

#### Custom CSS properties

The current library uses a bunch of [custom CSS properties](https://github.com/danfickle/openhtmltopdf/wiki/Custom-CSS-properties) that comes from the original code.

- `-fs-table-paginate: paginate`: allows to split the table into two pages repeating the table headers in the second page.

### References

- [openhtmltopdf - Custom CSS properties](https://github.com/danfickle/openhtmltopdf/wiki/Custom-CSS-properties)
- [MDN - page-break-before](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/page-break-before)
