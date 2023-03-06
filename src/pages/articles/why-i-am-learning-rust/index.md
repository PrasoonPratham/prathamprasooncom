---
title: "Why I am learning Rust "
summary: A Pythonista decides to learn the most loved programming language of 2023.
date: 2023-02-05
# weight: 2
tags: ["Programming"]
categories: ["Programming"]
author: "Pratham Prasoon"
---

### Introduction

Rust has become one of the fastest-growing and most loved programming languages, with its popularity only increasing with each passing year. I have been following Rust's progress with great interest, and I've finally decided to take the plunge and start learning it.

Here's why and how I'm learning this beast of a programming language in 2023.

### Why Rust?

Python and JavaScript/TypeScript are my go-to languages for building web apps, backends, ML models, and anything I want. However, recently I've wanted to learn something that's more low-level and faster. 

That's how I got to learning Rust.

Rust is called by many the modern replacement for C++.
It is designed for systems programming, with a focus on safety, performance, and concurrency. 

Here are some features of Rust that make it incredibly nice to work with:

#### 💾 Memory safety

Rust has a strong focus on preventing common programming errors such as null or dangling pointer references, which can lead to memory safety issues such as buffer overflows and data races.

```rust
// Memory safety is ensured through the use of a borrow checker.
// It checks for references to memory that have been freed
// or are otherwise invalid.

//This will not compile due to the borrow checker
let mut x = vec! [1, 2, 3] ;
let y = &x[0];
x.push(4) ;

// To fix the error, you could use let y = &x[0], after the push
```

#### ⛓️ Concurrency

Rust has built-in support for concurrent programming, making it easier to write efficient and correct concurrent code.

```rust
use std::thread;

fn main() {

    let handle1 = thread::spawn (// {
    // code for thread 1 to execute
        println!("Thread 1");
    });

    let handle2 = thread::spawn (// {
    // code for thread 2 to execute
        println!("Thread 2");
    });

// wait for both threads to finish
handlel.join().unwrap();
handle2.join().unwrap();

```

#### 🏃‍♂️ Performance

Rust code can be as fast as C or C++ code, but with the added safety guarantees provided by the language.

Here's a Fibonacci sequence up to 35 that takes ~103ms to run.


``` rust
use std::time::Instant;

fn fibonacci_rust(n: i32) -> i32 {
    if n < 2 {
        return n;
    } else {
        return fibonacci_rust(n-1) + fibonacci_rust(n-2);
    }
}

fn main() {
    let start = Instant::now();
    let result = fibonacci_rust(35);
    let end = Instant::now();
    println! ("Rust : { :?}" , end.duration_since(start));
}

// Rust: 102.221ms

```

Compare that to Python, which takes ~2s.
Rust is 20x faster!

```python
import time

def fibonacci_python(n):
    if n < 2:
        return n
    else:
        return fibonacci_python(n-1) + fibonacci_python(n-2)

start = time.time()
result = fibonacci_python(35)
end = time.time()
print("Python: ", end-start)

# Python: 2.000000238418579

```

#### 💪 Strong type system

Rust has a strong type system that helps to catch errors at compile time rather than at runtime.

```rust
// In Rust, all variables have a specific type, and the type must be specified at compile time.
// This is known as a "strong type system."

let x: i32 = 42; // x is an i32 (32-bit signed integer)
let y: f64 = 3.14; // y is a f64 (64-bit floating point number)

fn main() {
    // Attempting to assign a value of incorrect type to a variable will result in a compile-time error.
    // For example, the following line will not compile:
    // let z: i32 = 3.14; // error: expected i32, found f64

    // You can also assign a value without specifying its type, and the type of the variable will be inferred
    // from the value.
    let a = 42; // a is i32
    let b = 3.14; // b is f64

    // However, if you want to change the type of a variable, you need to explicitly cast it.
    let c: f32 = a as f32;

    // c is now a f32, and the value of a is casted to f32.
}

```


### Use cases

Rust is used in a bunch of places like:

- Parts of the Linux Kernel
- Gecko, the JavaScript engine running Firefox. 
- Blockchain smart contracts for Solana

...and my favorite, running full-fledged Rust applications in the browser using WebAssembly.

### How to learn Rust?

If you want to get started with Rust, here are some awesome free resources:

- The Rust Programming Language Book: https://doc.rust-lang.org/book/
- Rust by Example: https://doc.rust-lang.org/stable/rust-by-example/
- Rustlings: https://github.com/rust-lang/rustlings


If you're looking for something more advanced, the Rust Cookbook is a great resource: https://rust-lang-nursery.github.io/rust-cookbook/

### Conclusion

Rust is a great language to learn, and I'm excited to see where it goes in the future. I hope you enjoyed this post, and if you have any questions, feel free to reach out to me on Twitter: [@PrasoonPratham](https://twitter.com/PrasoonPratham)
