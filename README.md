# Tutorial 1: Timer

## Experiment 1.1: Original timer from the book

### What I did
I implemented a simple asynchronous timer and executor based on the Rust Async Book. The program creates a `TimerFuture`, spawns it into a custom executor, waits for two seconds, and then continues execution.

The program prints howdy first because the async task starts running when the executor polls it. After that, TimerFuture::new(Duration::new(2, 0)).await returns Poll::Pending, so the executor waits until the waker is called. The timer thread sleeps for two seconds, marks the shared state as completed, and wakes the task. After being woken, the task is polled again and prints done. This shows that a future does not complete immediately, but needs to be driven by an executor.

### How to run

```bash
cargo run


