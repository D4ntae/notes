Use to represent diffrent finite states of some data
```rust
// IP address can be V4 or V6
enum IPAddr {
	V4,
	V6,
}

let home = IPAddr::V4;

// Types can also have data associated with them
enum IPAddr {
	V4(u8, u8, u8, u8),
	V6(String),
}

let home = IPAddr(127, 0, 0, 1);
let loopback = IPAddr("::1");


```