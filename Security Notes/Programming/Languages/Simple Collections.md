#### Vectors
```rust
let v: vec<i32> = Vec::new();

// Or through a macro
let v = vec![1, 2, 3];

// Operations
let mut v = vec![1, 2, 3];
v.push(4); // append

// Vector indexing returs a reference and .get(index) returns an Option refernce 
```