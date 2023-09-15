---
title : Rust
feed: show
tags: rust
date : 29-05-2023
updated: 15-09-2023
type: note
growth: seedlings
---

## Basic Concepts

### Creating an Array

```rust
let arr: Vec<String> = vec!["example".to_string()];
```
- Array of objects

```rust
pub struct Book {
  pub id: u16,
  pub title: String,
}

...

let arr: Vec<Story> = vec![{ id: 1, title: "The Catcher in the Rye" }]
```

**TODO** An Array and a Vector aren't the same in Rust: [Read more](https://www.cs.brandeis.edu/~cs146a/rust/doc-02-21-2015/book/arrays-vectors-and-slices.html)
**TODO** Think in moving specific learnings to their specific page

### Tools

- Databases:
  - [SQLx](https://github.com/launchbadge/sqlx)
