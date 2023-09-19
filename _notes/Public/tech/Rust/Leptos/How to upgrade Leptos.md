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
version = "0.0.1"
edition = "2021"

[lib]
crate-type = ["cdylib", "rlib"]

[dependencies]
actix-files = { version = "0.6", optional = true }
actix-web = { version = "4", features = ["macros"], optional = true }
cfg-if = "1.0"
chrono = "0.4.24"
console_log = "0.2"
console_error_panic_hook = "0.1"
futures = "0.3"
gloo-net = { version = "0.2", features = ["http"] }
leptos = { version = "0.4.9", default-features = false, features = [
  "serde",
] }
leptos_actix = { version = "0.4.9", optional = true }
leptos_meta = { version = "0.4.9", default-features = false }
leptos_router = { version = "0.4.9", default-features = false }
log = "0.4"
serde = { version = "1", features = ["derive"] }
serde_json = "1.0"
simple_logger = "4.0"
sqlx = { version = "0.6.2", features = [
	"runtime-tokio-rustls",
	"sqlite",
], optional = true }
wasm-bindgen = "0.2"
web-sys = { version = "0.3.60", features = ["Storage"] }
```
2. Modify manually the version for the following libraries:
   2.1. leptos
   2.2. leptos_actix
   2.3. leptos_meta
   2.4. leptos_router
3. Run `cargo build`.

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

   
