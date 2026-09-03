# Multithreaded Rust Web Server

A minimal multithreaded HTTP server built with standard Rust, following Chapter 21 of [*The Rust Programming Language*](https://doc.rust-lang.org/book/).

## Features

- **TCP Handling:** Listens for connections via `TcpListener` and manual stream parsing.
- **Custom Thread Pool:** Distributes incoming jobs across worker threads via an `Arc<Mutex<mpsc::Receiver>>`.
- **Graceful Shutdown:** Implements `Drop` on `ThreadPool` to finish active tasks.

## Quick Start

```bash
cargo run
```

Visit in your browser:

* `http://127.0.0.1:7878` (renders `hello.html`)
* `http://127.0.0.1:7878/sleep` (simulates blocking request)
* `http://127.0.0.1:7878/unknown` (renders `404.html`)

## Future Ideas

* Add more documentation to `ThreadPool` and its public methods.
* Add tests of the library’s functionality.
* Change calls to `unwrap` to more robust error handling.
* Use `ThreadPool` to perform some task other than serving web requests.
* Find a thread pool crate on [crates.io](https://crates.io/) and implement a similar web server using the crate instead. Then, compare its API and robustness to the thread pool we implemented.
