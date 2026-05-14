---
title: Proper use of line-height
feed: show
tags: css best-practices accessibility
date: 14-05-2026
updated: 14-05-2026
type: note
growth: seedlings
---

### Problems

The [line-height](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/line-height) property in [[CSS]] allows different values. It can be set using **px**, a **number**, **percentage** or even keywords (**normal**, inherit...). But not all of these options are optimal for usage when using **line-height**.

### Solution

For [[Accessibility]], [MDN guide](https://developer.mozilla.org/en-US/) propose the following applications:

- **Use a unitless value** (like **1.5**) to avoid strange behaviours when zooming the website. Using a unitless value (maybe it would apply for percentage too) allows to **line-height** property to scale properly.
- A minimum value of **1.5** is recommended to use in main paragraph texts. This would help people with low vision conditions or Dyslexia to follow the text.

### References 

- [MDN - Accessibility with line-height](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/line-height#accessibility)
