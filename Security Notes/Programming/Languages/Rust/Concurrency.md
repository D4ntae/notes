```rust
use std::thread;

thread::spawn(|| /* some code */); // call thread::spawn and send it a closure


// Sending messages
use std::sync::mpsc;
use std::thread;

let (tx, rx) = mpsc::channel();
thread::spawn(move || {
	let val = String::from("Hi");
	tx.send(val).unwrap();
})

let received = rx.recv().unwrap();

```