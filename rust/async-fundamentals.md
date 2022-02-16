## Asynchronous Programming

Asynchronous programming (or _async_) is a concurrent programming model that allows large number of tasks to be run on a relatively small number of OS threads, while maintaining the look and feel of synchronous code through the _async/await_ syntax. 

This concurrency model is best suited for IO-bound workloads. I.e., applications/programs where tasks spend a significant amount of time waiting for responses to I/O calls. E.g., networking applications. Async programming is not suited to CPU-bound workloads, i.e., tasks that spend the majority of their time using the CPU and would be faster if the CPU were faster.

#### Alternatives to Asynchronous Programming

Programming languages support different concurrent programming models. These include:

- *OS Threads:* These don't require any change to the programming model, which makes them easy to express concurrent tasks with. But, they come with a relatively high performance overhead, and It is also difficult to share data among threads. Their performance overhead can be mitigated by thread pools, but even that is not sufficient for massive IO-bound workloads.

- *Event-driven programming:* This involves use of callbacks to handle events. This can lead to verbose code and a non-linear workflow.

- *Coroutines:* Like threads, these are easy to express tasks in. Like async, they are performant. However they abstract away low-level details that are important in systems programming and custom runtime implementation. Coroutines are good choice for IO-bound workloads in application programming. Languages that support coroutines include Kotlin and Golang.

- *Actor model:* TODO??

## 