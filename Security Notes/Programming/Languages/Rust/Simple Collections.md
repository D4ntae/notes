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

#### Strings
```rust
// Creating a string
let mut s = String::new();
let s = "text".to_string();
let s = String::from("text");

// Updating a string
let mut s = String::new();
s.push_str("text"); // append to string

// Strings are UTF-8 encoded
// To loop over a string use <string>.chars()
let mut s = String::from("Džungla");
for c in s.chars() {
	println!("{}", c);
}
```

#### Hashmap
```rust
use std::collections::HashMap;

let mut scores = HashMap::new();

scores.insert(String::from("Blue Team"), 10);
scores.insert(String::from("Yellow Team"), 50);
```