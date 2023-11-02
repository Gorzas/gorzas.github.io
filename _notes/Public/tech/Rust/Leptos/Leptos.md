---
title : Leptos
feed: show
tags: rust, frameworks
date : 29-05-2023
updated: 02-11-2023
type: note
growth: seedlings
---

### Install Cargo Leptos

for Windows Subsystem Linux and `Cargo Leptos` v0.2 ([repository](https://github.com/leptos-rs/cargo-leptos)]:

1. Install Rust: `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`
2. Install dependencies:
  2.1. `sudo apt install build-essential`
  2.2. `sudo apt install pkg-config` 
  2.3. `sudo apt install libss-dev`
3. Install **Cargo Leptos**: `cargo install --locked cargo-leptos` 
    

### Things to look for

What does the following code means?

```rust
#[derive(Clone, Debug, PartialEq, Eq, Serialize, Deserialize)]
#[cfg_attr(feature = "ssr", derive(sqlx::FromRow))]
```

Why do I need `create_resource` function?

- code: https://github.com/leptos-rs/leptos/blob/main/leptos_reactive/src/resource.rs#L77

### Ideas

- Add docs about my architecture and way of work using Leptos.

### References

- [Leptos repository](https://github.com/leptos-rs/leptos)
- [Roadmap v0.5.x](https://github.com/leptos-rs/leptos/issues/1147)
- [Leptos Book](https://leptos-rs.github.io/leptos/)

