## Asynchronous Programming

Asynchronous programming (or _async_) is a concurrent programming model that allows large number of tasks to be run on a relatively small number of OS threads, while maintaining the look and feel of synchronous code through the _async/await_ syntax. 

This concurrency model is best suited for IO-bound workloads. I.e., applications/programs where tasks spend a significant amount of time waiting for responses to I/O calls. E.g., networking applications. Async programming is not suited to CPU-bound workloads, i.e., tasks that spend the majority of their time using the CPU and would be faster if the CPU were faster.

#### Alternatives to Asynchronous Programming

Programming languages support different concurrent programming models. These include:

- *OS Threads:* These don't require any change to the programming model, which makes them easy to express concurrent tasks with. But, they come with a relatively high performance overhead, and It is also difficult to share data among threads. Their performance overhead can be mitigated by thread pools, but even that is not sufficient for massive IO-bound workloads.

- *Event-driven programming:* This involves use of callbacks to handle events. This can lead to verbose code and a non-linear workflow.

- *Coroutines:* Like threads, these are easy to express tasks in. Like async, they are performant. However they abstract away low-level details that are important in systems programming and custom runtime implementation. Coroutines are good choice for IO-bound workloads in application programming. Languages that support coroutines include Kotlin and Golang.

- *Actor model:* TODO??

## Async/Await

`async/.await` is the Rust langauge feature for writing asynchronous code with the look and feel of synchronous code. 

`async` makes a function return an implementation of the `Future` trait. Calling a blocking function in a synchronous operation would cause the whole thread to be blocked, but a `Future` would yield control of the thread, and allow other `Future`s to run. 

```rust
async pub process_something() -> i32 {
    // This returns a Future that has to be run on an executor.
    // TODO: What happens if a `Future` is used in synchronous Rust?
}
```

`.await` is used inside an `async` function to wait for the completion of another. This doesn't block the thread, instead it is freed up for the executor to run another `Future`.

```rust
async pub do_another_thing() {
    // Once .await is called, the thread is yielded for other Futures to use.
    let x = process_something().await;
}
```

`Future`s have to be run on an executor, otherwise nothing happens(??).
