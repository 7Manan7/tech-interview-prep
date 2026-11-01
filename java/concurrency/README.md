# 🧵 Java Concurrency & Multithreading

Concurrency is one of the most critical interview topics for Java backend engineers. This guide covers theoretical concepts, memory model specifications, practical concurrency utilities, and modern concurrency patterns.

---

## 🧠 1. Java Memory Model (JMM) & Thread Safety

### The Visibility Problem & `volatile`
- Modern CPUs use multi-level hardware caches (L1, L2, L3). Without memory barriers, writes in one core may remain in local CPU cache and never be seen by another core.
- **`volatile` keyword guarantees:**
  1. **Visibility:** Changes made by one thread are immediately flushed to main memory and visible to all other threads.
  2. **Ordering (Prevents Instruction Reordering):** Introduces memory barriers (Happens-Before guarantee).
  3. **Note:** `volatile` does **NOT** guarantee atomicity (e.g., `count++` is read-modify-write and still requires synchronization or atomic primitives).

### The Happens-Before Relationship
- A write to a `volatile` variable happens-before every subsequent read of that variable.
- An unlock on a monitor happens-before every subsequent lock on the same monitor.
- A call to `Thread.start()` happens-before any action in the started thread.

---

## 🔒 2. Synchronization & Locks

### `synchronized` vs `ReentrantLock`

| Feature | `synchronized` | `ReentrantLock` |
|---|---|---|
| **Mechanism** | Built-in language monitor (implicit lock acquisition & release) | Explicit API (`lock.lock()`, `lock.unlock()` in `finally`) |
| **Fairness** | Non-fair only | Configurable fair / non-fair |
| **Interruptible** | No (thread blocks indefinitely) | Yes (`lockInterruptibly()`) |
| **Timed Try-Lock** | No | Yes (`tryLock(timeout, unit)`) |
| **Multiple Conditions**| Single condition per object (`wait()`, `notify()`, `notifyAll()`) | Multiple condition variables per lock (`lock.newCondition()`) |

### `ReentrantReadWriteLock` & `StampedLock`
- **`ReadWriteLock`:** Multiple threads can read concurrently; only one thread can write (exclusive).
- **`StampedLock` (Java 8+):** Offers optimistic reading mode which avoids full lock acquisition if no write occurred during the read block.

---

## ⚡ 3. Atomic Operations & Lock-Free Programming

Java uses CPU-level atomic instructions (**Compare-And-Swap / CAS**):
- Classes: `AtomicInteger`, `AtomicLong`, `AtomicBoolean`, `AtomicReference`.
- In high-contention scenarios, `LongAdder` / `DoubleAdder` out-perform `AtomicLong` by striping counters across multiple internal cells to reduce thread contention.

---

## ⚙️ 4. Thread Pools & `ThreadPoolExecutor`

Never create raw threads manually (`new Thread().start()`) in production backend services.

### Core Architecture of `ThreadPoolExecutor`

```java
ThreadPoolExecutor executor = new ThreadPoolExecutor(
    corePoolSize,          // Minimum number of threads kept alive
    maximumPoolSize,       // Maximum number of threads allowed
    keepAliveTime, unit,   // Idle thread timeout for threads > corePoolSize
    workQueue,             // BlockingQueue<Runnable> holding submitted tasks
    threadFactory,         // Custom factory (naming threads, daemon status)
    rejectionHandler       // Action when queue is full and threads == maximumPoolSize
);
```

### Task Submission Lifecycle
1. If `activeThreads < corePoolSize`: Create new worker thread to run task.
2. If `activeThreads >= corePoolSize`: Offer task to `workQueue`.
3. If `workQueue` is full and `activeThreads < maximumPoolSize`: Spawn new thread.
4. If `workQueue` is full and `activeThreads == maximumPoolSize`: Execute rejection policy (`AbortPolicy`, `CallerRunsPolicy`, `DiscardPolicy`, `DiscardOldestPolicy`).

### Thread Pool Sizing Formula
- **CPU-bound tasks:** `threads = number_of_available_cores + 1`
- **I/O-bound tasks (DB, REST calls):** `threads = number_of_available_cores * (1 + Wait_Time / CPU_Time)`

---

## 🚀 5. Modern Concurrency: Virtual Threads (Java 21+)

### Virtual Threads vs Platform Threads
- **Platform (OS) Threads:** 1:1 mapping with OS kernel thread. Heavyweight (~1 MB stack), expensive context switching, limited to a few thousand per JVM.
- **Virtual Threads (Project Loom):** $M:N$ mapping. Lightweight user-mode threads managed by the JVM runtime (~few KBs). When a virtual thread executes blocking I/O (e.g., HTTP call, JDBC query), the JVM unmounts it from the carrier OS thread, allowing millions of concurrent tasks.

```java
// Create a virtual thread executor
try (var executor = Executors.newVirtualThreadPerTaskExecutor()) {
    executor.submit(() -> {
        // High-throughput, non-blocking I/O
    });
}
```

