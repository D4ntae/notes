A system of heap management that prevents memory erros at compile time thus removing the need for garbage collection and runtime checks

Rules of ownership
- All heap data must be owned by exactly one variable
- Data is deallocated if its owner goes out of scope
- Ownership can be transferred by moves which happen on assignments and function calls
- Heap data can only be accessed through its current owner, not a previous one
- Ownership is a compiler concept it doesnt exist in the final compiled assembly

#### Examples
```rust
let s = String::from("Hello"); // s is the owner of hello
let s2 = s; // Ownership is transferred to s2

println!("{}", s); // No longer valid code as data can't be accessed from a previous owner

-----
fn to_uppercase(mut s2: String) {
	// make uppercase
	s2
}

let s = String::from("Hello");
let s3 = to_uppercase(s);

// First s owns the string "Hello", next ownership is transferred to the argument s2, and the data is now mutable but s can no longer access it. After the function is over the ownership is transferred to s3 which is now the final owner. 

```


### References
----
References are a way to avoid transferring ownership on every move like sending a parameter to a function.
```rust
fn length(s1: &String) -> i32 {
	s1.len();
}
let s = String::from("Hello");
println!("{}", s);
// This is valid code as ownership is not transferred to the s1 argument as s1 is a reference to s.

// s is a pointer to the actuall data "Hello" and s1 is a pointer to s
// s1 -> s -> "Hello"
// To get "Hello" from s1 you need to dereference s1 twice **s1 == "Hello"
```

Some rules of references
- If a reference to a variable exists that variable can only be read
- If a mutable reference to a variable exists that variable cannot be used in any way