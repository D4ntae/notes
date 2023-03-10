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

The Option\<T\> enum
- used instead of null to signify a variable that might not have a value
- must be resolved
- safer than null

The match statement
```rust
enum Coin {
	Penny,
	Nickel,
	Dime,
	Quarter
}

fn value_in_cents(coin: Coin) {
	match coin {
		Coin::Penny => 1, // these are called arms
		Coin::Nickel => 5,
		Coin::Dime => 10,
		Coin::Quarter => 25,
	}
}


// Example with Option<T>
fn plus_one(x: Option<i32>) -> Option<i32> {
	match x {
		None => None,
		Some(i) => Some(i + 1),
	}
}


```

#rust