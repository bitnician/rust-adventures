# Day 1: Overview of Rust’s Features

let's make sure why we learn rust and what makes Rust unique and the use cases where it shines.

Before talking about Rust, there are a few concepts that i believe every developer must understand:

## Garbage Collection (GC):

It is an automatic memory management feature used in many programming languages. It identifies and reclaims memory that a program no longer uses, preventing memory leaks.

How It Works

1. Allocation:

   • When a program creates objects or data structures, memory is allocated for them on the heap.

2. Garbage Identification:

   • GC periodically scans memory to find data that is no longer referenced by the program.

3. Reclaiming Memory:

   • The identified memory is reclaimed, making it available for reuse.

Some languages like Java, Python, JavaScript, PHP use GC to manage memory automatically. In these languages, you don’t need to worry about freeing memory manually, as GC handles it but there are some Disadvantages.
The GC process may interrupt the program execution, causing delays, especially in real-time or performance-critical applications (e.g., games). also, The scanning and reclaiming process uses CPU cycles, which can impact performance.

Rust avoids garbage collection entirely. Instead, It uses ownership and borrowing to manage memory safely at compile time. This eliminates GC pauses and reduces runtime overhead.

## Concurrency:

Concurrency is the ability of a program to perform multiple tasks simultaneously or handle multiple operations in overlapping time periods.

### Concurrency vs. Parallelism

• Concurrency: Managing multiple tasks that are running independently but not necessarily at the same time. for example, A web server handling multiple client requests at the same time or A video player downloading a video while playing it.

• Parallelism: Executing multiple tasks simultaneously on different processors/cores.

In programming languages, concurrency is achievable via `Threads` and `Async/Awai`.
A thread is a lightweight unit of execution. Programs can use multiple threads to run tasks concurrently. C/C++ uses thread.
Languages like JavaScript use asynchronous programming to manage concurrency without threads.

**Concurrency in Rust:**

Rust provides:

• Threads: Safe and efficient thread management.

• Async/Await: Lightweight concurrency for IO-bound tasks.

## Data Race:

A data race occurs when 1)two or more threads access the same memory location, 2) At least one thread modifies the data and 3) There’s no mechanism to prevent simultaneous access.

In this case, Results can vary between program runs and accessing invalid or incomplete data can cause a crash.
In the below example, If `thread1` and `thread2` run simultaneously, their operations on shared_data can overlap, leading to incorrect results.

    int shared_data = 0;

    void thread1() {
        shared_data++;
    }

    void thread2() {
        shared_data--;
    }

Rust eliminates data races through its ownership system. it means, Only one thread can modify data at a time (enforced via mutable borrowing rules). If multiple threads need to access the same data, Rust ensures it’s either immutable or properly synchronized.

1.  Core Features of Rust

    1. Memory Safety Without Garbage Collection:

       • Rust prevents common memory bugs at compile time (e.g., null pointer dereferencing, use-after-free).
       • Instead of relying on a garbage collector (like Java or Python), Rust uses an ownership model.

    2. Zero-Cost Abstractions:

       • Rust abstractions (e.g., iterators, pattern matching) are designed to be as efficient as handwritten low-level code.

    3. Concurrency Without Data Races:

       • Rust’s ownership and borrowing rules ensure that programs are thread-safe by default.

    4. Type Safety and Expressiveness:

       • Rust has a strong and expressive type system with features like enums, traits, and pattern matching.

    5. Cross-Platform Development:

       • With tools like Cargo, Rust makes it easy to build and deploy on different platforms.

2.  Use Cases for Rust

    1. System Programming:

       • Writing operating systems, device drivers, or embedded systems. Example: TockOS.

    2. Web Development:

       • High-performance APIs and web frameworks like Rocket and Actix.

    3. Game Development:

       • Building games and game engines with frameworks like Bevy.

    4. Blockchain:

       • Many blockchain projects (e.g., Polkadot) are written in Rust due to its performance and safety.

    5. CLI Tools:

       • Building fast, reliable command-line applications. Example: ripgrep.

## Getting Started With Rust

Rust has an official toolchain installer called rustup. Follow these steps:

1.  Open a terminal.
2.  Run the following command, This will install rustup and the Rust compiler (rustc):

        curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

3.  Restart your terminal and verify the installation:

        rustc --version

    You should see the installed version of Rust.

To test Rust code properly, you’ll want to create a project using Cargo, Rust’s package manager and build system. Open your terminal and create a new project:

    cargo new rust-learning
