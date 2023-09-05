---
title : Rust - Basic Concepts
feed: show
tags: rust
date : 29-05-2023
updated: 05-09-2023
type: note
growth: seedlings
---

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

### Tools

- Databases:
  - SQLx: https://github.com/launchbadge/sqlx
