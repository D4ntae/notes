#### Hello World
----
```rust
fn main() {
	println!("Hello World");
}
```

#### Command line usage
----
```bash
# Compilation
rustc helloworld.rs
# Or better
cargo new <project-name> OR cargo init
cargo run helloworld.rs
```

#### IO handling and importing packages
----
```rust
// io is handled by std::io
use std::io;
```

#### Variables
----
```rust
// Variables are by default immutable
let apples = 5; // immutable
let mut bananas = 5; // mutable

// Const variables must be type-annotated and can be declared in global scope, let cannot
const apples: i32 = 5;

```

#### Data Types
----
Integers
- signed and unsigned from 8 to 128 bits
- arch type is 64bit if machine is 64bit and 32bit if machine is 32bit
- can be written with and _ to make it more readable eg. ```98_123 ```

Floats
- can be f32 or f64
- default is f64

Booleans
- self-explenatory, true and false

Chars
- Unicode encoded scalars, supports all unicode characters

Tuples
- fixed lenght
- can contain different data types
```rust
// Accessing example
let x: (i32, f32, i8) = (3_000, 4.5, 52);
let a: i32 = x.0;
let b: f32 = x.1;
```

Arrays
- fixed length
- stack allocated
- must all be same type
```rust
// Array examples
let arr: i32 = [1, 2, 3, 4];

// Creates an array of 10 zeros
let zeros: i32 = [0; 10];
```

