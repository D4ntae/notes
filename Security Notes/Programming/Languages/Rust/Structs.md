A nicer to use C struct
```rust
struct User {
	email: String,
	username: String,
	active: boolean,
	sign_in_count: u64,
}

let user1 = User {
	email: String::from("someone@example.com"),
	username: String::from("someone"),
	active: true,
	sign_in_count: 1,
};

// if fields should be able to change the whole struct must be mutable
// shorthand notation can be used to instantiate fields of the same name
// if a struct is created from another struct and the fields used do not implement the copy trait the original struct is no longer valid


// Tuple sturcts

struct Color(i32, i32, i32);
let black = Color(0, 0, 0);
black.0 // access

struct User {
	email: String,
	username: String,
	active: boolean,
	sign_in_count: u64,
}

// impl block is used to implement struct methods
impl User {
	fn log_out(&self) {
		self.active = false;
	}

	// Associated function without self in params is called with User::create_user() like a static function in c++
	fn create_user(name: String, email: String) -> User {
		User {
			name,
			email,
			active: true,
			sign_in_count: 1,
		}
	}
}
```

