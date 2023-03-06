
```rust
fn main() {
	println!("Hello World");
}
```

```bash
# Compilation
rustc helloworld.rs
# Or better
cargo new <project-name> OR cargo init
cargo run helloworld.rs
```

```rust
// io is handled by std::io
use std::io;

// Variables are by default immutable
let apples = 5; // immutable
let mut bananas = 5; // mutable



```