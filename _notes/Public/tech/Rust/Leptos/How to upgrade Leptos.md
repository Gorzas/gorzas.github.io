---
title: How to upgrade Leptos
feed: show
tags: leptos rust
date: 19-09-2023
updated: 19-09-2023
type: note
growth: seedlings
---

1. Open `Cargo.toml`. It should show something like the following code:
```
[workspace]

[package]
name = "stories52"
...

[lib]
crate-type = ["cdylib", "rlib"]

[dependencies]
leptos = { version = "0.4.9", default-features = false, features = [
  "serde",
] }
leptos_actix = { version = "0.4.9", optional = true }
leptos_meta = { version = "0.4.9", default-features = false }
leptos_router = { version = "0.4.9", default-features = false }
...
```
2. Modify manually the version for the following libraries:
  - leptos
  - leptos_actix
  - leptos_meta
  - leptos_router
3. Make sure you have the latest version of [[Rust]]: `rustup update`
4. Run `cargo build`.

### Example

Before:

```
futures = "0.3"
gloo-net = { version = "0.2", features = ["http"] }
leptos = { version = "0.4.9", default-features = false, features = [
  "serde",
] }
leptos_actix = { version = "0.4.9", optional = true }
leptos_meta = { version = "0.4.9", default-features = false }
leptos_router = { version = "0.4.9", default-features = false }
log = "0.4"
```

After:

```
futures = "0.3"
gloo-net = { version = "0.2", features = ["http"] }
leptos = { version = "0.5.0-rc2", default-features = false, features = [
  "serde",
] }
leptos_actix = { version = "0.5.0-rc2", optional = true }
leptos_meta = { version = "0.5.0-rc2", default-features = false }
leptos_router = { version = "0.5.0-rc2", default-features = false }
log = "0.4"
```

   
