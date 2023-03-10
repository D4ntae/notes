#### Closures
- simmilar to lambda functions
```rust
let add_one = (|x| {x + 1});
let x = 2;
let y = add_one(x);

// Closures implement some of three trains
// Fn - immutable can be called multiple times
// FnMut - mutable can be called multiple times
// FnOnce - immutable can only be called once

// Can be used as function parameters
```

#### Iterators
