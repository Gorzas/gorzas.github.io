---
title : Data down, actions up
feed: show
tags: JavaScript framework EmberJS architecture
date: 28-11-2024
updated: 28-11-2024
type: note
growth: seedlings
---

## Context

**Data Down, Actions Up (DDAU)** is the fundamental pattern in [[EmberJS]] framework.

- Data is fetched in parent components (ideally, in Routers or Controllers) and the data is passed to the child components throught their attributes.
- Actions are handled in child components but sent back to parent elements if they require to modify the current state of the application. This way, there's a single source of truth of the state of the WebApp.

In different frameworks, this pattern is called [one-way-data flow](https://react.dev/learn/thinking-in-react).

### References

- [Thinking in React](https://react.dev/learn/thinking-in-react)
- [Ember tutorial: Working with Data](https://guides.emberjs.com/release/tutorial/part-1/working-with-data/)
