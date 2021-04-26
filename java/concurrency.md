## Concurrency Primitives.

Brief description of the low-level building blocks of concurrent programming in Java.

### Process and Threads.

A process is a self-contained execution environment with it's own complete set of basic runtime resources. Each process has its own memory space, and at least one thread. A process can be seen as a single program or an application. Most implementations of the JVM run as a single process, although applications can create other processes using a `ProcessBuilder`.

Threads are known as _lightweight processes_. A thread exists within a process and shares the resources of the process, including open files, with other threads. This makes for efficient, and potentially problematic communication.

Each thread is associated with a `Thread` object. There are two strategies for using objects of this class:
* Instantiate it to directly create and manage threads.
* Pass it to a `Executor`


There are two ways to define code that will run in a thread: Implement `Runnable` or subclass `Thread`. Implementing runnable is more flexible since your class can extend another class too.
`Thread` itself already implements `Runnable`, but extending it means your class cannot be of any other type.

See [Instantiating A Thread](https://docs.oracle.com/javase/tutorial/essential/concurrency/runthread.html)

`Thread.join()` causes one thread to wait for the completion of another. 

### Synchronization

Threads communicate by sharing access to fields and object references. This can lead to thread [thread interference](https://docs.oracle.com/javase/tutorial/essential/concurrency/interfere.html) and [memory consistency errors](https://docs.oracle.com/javase/tutorial/essential/concurrency/memconsist.html)

Synchronization is the way to mitigate these problems. But, itself can lead to other issues like deadlock, [starvation and livelock](https://docs.oracle.com/javase/tutorial/essential/concurrency/starvelive.html)

Synchronized methods can be used to prevent interference and memory consistency errors. Once a thread calls an object method that is marked as `synchronized`, no other thread can call any synchronized method on the same object until the first thread is done executing.

Every object has an intrinsic lock associated with it. When a thread calls a synchronized method, it acquires a lock on the object and doesn't release that lock until it returns(either successfully or through an uncaught exception). Any other thread that tries to acquire the lock before it's released will block.

Deadlock is situation where two or more threads are blocked forever, waiting for each other. 

## High Level Concurrency API.

A brief overview of the higher level APIs for concurrent programming in Java. 

### Executors

Executors help us to separate thread creation and management from the rest of the code. The Java API provides three exector interfaces.

* `Executor` - For running simple tasks.
* `ExecutorService` - extends `Executor` with features for managing both tasks and the executor itself. Provides a `submit()` method that accepts `Callable`s which define tasks that return a result.
* `ScheduledExecutorService` - extends `ExecutorService` with methods for running tasks after a delay or repeatedly.

Also, see [Fork/Join](https://docs.oracle.com/javase/tutorial/essential/concurrency/forkjoin.html)

### Thread Pools

Most `Executor` implementations use _thread pools_ which are a collection of resusable _worker threads_ that are independent of the `Runnable` or `Callable` tasks that they execute.

This approach minimizes the overhead incurred from creating and destroying new thread objects.



#### References

* [Java Lanaguage Tutorials | Concurrency](https://docs.oracle.com/javase/tutorial/essential/concurrency/index.html)
