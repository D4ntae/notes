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

impl Summary for <Type name> {
	fn summarize(&self) -> String {
		// code here
	}
}

// Default implementation
pub trait Summary {
	fn summarize(&self) -> String {
		String::from("Read more...")
	}
}

// Traits as function arguments
pub fn notify(item: &impl Summary) {
	println!("{}", item.summarize());
}

pub fn notify<T: Summary>(item1: &T, item2: &T) {}

fn some_function<T, U>(t: &T, u: &U) -> i32
where
    T: Display + Clone,
    U: Clone + Debug,
{}
```

#### Lifetimes
```rust

// The lifetime of the return is based on the lifetime of the second argument
fn do_something<'a>(str1: &str, str2: &'a str) -> &'a str {
	
}
```