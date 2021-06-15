# Hello Rust

# Installation

use rushup installer

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

this will install `cargo` the rust package manager, it will allow you to

- new project → `cargo new PROJECT`
- build → `cargo build`
- run → `cargo run`
- test → `cargo test`
- build document → `cargo doc`
- publish library to [crates.io](http://crates.io) → `cargo publish`

# New project

```bash
cargo new hello-rust
cd hello-rust
tree
> hello-rust
> |- Cargo.toml
> |- src/
>    |- main.rs

cargo run
> Compiling hello-rust v0.1.0 (/Users/ag_dubs/rust/hello-rust)
>     Finished dev [unoptimized + debuginfo] target(s) in 1.34s
>      Running `target/debug/hello-rust`
> Hello, world!
```

# Add dependencies

just like Elixir, you need to update manifest file → `Cargo.toml`

```toml
[dependencies]
ferris-says = "0.2"
```

then run `cargo build` to install dependencies

# Let's add more logic in code

```rust
use ferris_says::say;
use std::io::{stdout, BufWriter};

fn main() {
    let stdout = stdout();
    let message = String::from("Hello Rustaceans!");
    let width = message.chars().count();
    let mut write = BufWriter::new(stdout.lock());
    say(message.as_bytes(), width, &mut write).unwrap();
}
```

then run!

```bash
cargo run
----------------------------
| Hello fellow Rustaceans! |
----------------------------
              \
               \
                 _~^~^~_
             \) /  o o  \ (/
               '_   -   _'
               / '-----' \
```

# What?

- `use ferris_says::say;` → importing library to use
- `::` are like `.` in Java or `->` in PHP :D
- `mut` → actually all variable in Rust are immutable, but we can make it mutable by adding `mut` before variable name
- `let mut write = BufWriter::new(stdout.lock());` → it feel like, warp `stdout` into `write`
- `say(message.as_bytes(), width, &mut write).unwrap();` → print Ferris with "Hello Fellow Rustaceans" bubble
- Rustaceans → Rust programmer
- Ferris → Rust unofficial mascot
