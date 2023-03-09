```rust
// Example
fn largest<T>(list: &[T]) -> &T {}

struct Point<T> {
	x: T,
	y: T,
}

impl<T> Point<T> {

}
```

#### Traits
- simmilar to interfaces
```rust
pub trait Summary {
	fn summarize(&self) -> String;
}
```