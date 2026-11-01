# ☕ JVM Internals & Performance Tuning

Understanding the Java Virtual Machine (JVM) internals, memory layout, Just-In-Time (JIT) compilation, and Garbage Collection (GC) behavior is a key requirement for senior engineering interviews.

---

## 🏛️ 1. JVM Architecture & Runtime Data Areas

```text
┌──────────────────────────────────────────────────────────────────┐
│                     Class Loader Subsystem                       │
│       Loading (Bootstrap, Platform, App) -> Linking -> Init      │
└─────────────────────────────────┬────────────────────────────────┘
                                  ▼
┌──────────────────────────────────────────────────────────────────┐
│                       JVM Memory Areas                           │
│  ┌───────────────────────┐  ┌─────────────────────────────────┐  │
│  │   Metaspace (Native)  │  │           Heap Memory           │  │
│  │ Class metadata, pools │  │   Young (Eden, S0, S1) & Old    │  │
│  └───────────────────────┘  └─────────────────────────────────┘  │
│  ┌─────────────────────────────────────────────────────────────┐ │
│  │ Per-Thread: Thread Stack (Frames) | PC Register | Native    │ │
│  └─────────────────────────────────────────────────────────────┘ │
└─────────────────────────────────┬────────────────────────────────┘
                                  ▼
┌──────────────────────────────────────────────────────────────────┐
│                       Execution Engine                           │
│     Interpreter  |  JIT Compiler (C1, C2)  |  Garbage Collector  │
└──────────────────────────────────────────────────────────────────┘
```

### Memory Areas Breakdown
- **Heap Memory (Shared):** Stores all object instances and arrays. Divided into Young Generation (Eden, Survivor spaces S0 & S1) and Old / Tenured Generation.
- **Metaspace (Native Memory, Java 8+):** Stores class metadata, bytecode, static variables, and method tables. Replaced PermGen; expands dynamically up to OS memory (unless constrained by `-XX:MaxMetaspaceSize`).
- **Thread Stack (Per-Thread):** Stores stack frames for method invocations, primitive local variables, and object references. Sized via `-Xss`.
- **Program Counter (PC) Register:** Holds current execution address of bytecode instructions.

---

## 🚀 2. JIT (Just-In-Time) Compilation & Optimizations

The JVM begins by interpreting bytecode. Hot methods (identified by execution counters) are compiled to native machine code at runtime.

### Key JIT Optimization Techniques
1. **Tiered Compilation:** Combines quick C1 compiler (basic optimizations, quick startup) with C2 server compiler (aggressive optimizations, high peak throughput).
2. **Method Inlining:** Replaces method calls with method bodies, eliminating function call overhead and enabling further optimizations.
3. **Escape Analysis:** Determines if an object reference escapes the current method or thread.
   - If not escaped: The JVM can perform **Scalar Replacement** (allocating fields on the stack or in registers, bypassing heap allocation entirely) and **Lock Elision** (eliminating redundant synchronization).

---

## 🧹 3. Garbage Collection (GC) Mechanisms

### The Weak Generational Hypothesis
Most allocated objects have a very short lifespan (die shortly after creation). Therefore, heap is partitioned:
1. **Young Generation (Eden + S0 + S1):** Collected via Minor GC. Fast copying algorithm.
2. **Old Generation:** Objects surviving multiple GC rounds (tenuring threshold, default 15) are promoted here. Collected via Major / Full GC.

### Garbage Collector Comparison

| Collector | Target Workload | Algorithm / Architecture | Pause Characteristics | Flag |
|---|---|---|---|---|
| **Parallel GC** | High batch processing throughput | Multi-threaded generational collector | High throughput, longer Stop-The-World (STW) pauses | `-XX:+UseParallelGC` |
| **G1 GC (Default Java 9+)** | General purpose server apps | Heap partitioned into equal regions (~1–32MB), concurrent marking, incremental evacuation | Target predictable pause times (`-XX:MaxGCPauseMillis=200`) | `-XX:+UseG1GC` |
| **ZGC (Scalable Low-Latency)** | Microservices & large heaps (up to 16 TB) | Colored pointers & load barriers; all phases concurrent (marking, evacuation, reference processing) | Sub-millisecond pause times (< 1ms) | `-XX:+UseZGC` |
| **Shenandoah** | Low-latency server apps | Brooks pointers / load-reference barriers, concurrent compaction | Ultra-low pause times independent of heap size | `-XX:+UseShenandoahGC` |

---

## 🔍 4. Diagnosing OutOfMemoryErrors (OOM)

| Exception | Root Cause | Diagnosis & Resolution |
|---|---|---|
| `java.lang.OutOfMemoryError: Java heap space` | Heap full; objects cannot be collected due to memory leak or undersized heap. | Inspect heap dump using Eclipse MAT or JProfiler. Check `-Xmx`. |
| `java.lang.OutOfMemoryError: Metaspace` | Too many dynamic classes generated (CGLIB, reflection, classloader leaks). | Set `-XX:MaxMetaspaceSize`. Check class unload logs (`-Xlog:class+unload=info`). |
| `java.lang.OutOfMemoryError: Unable to create new native thread` | OS thread limit reached or system out of native memory. | Inspect thread count (`jstack` / `ps -eLf`). Optimize thread pools or switch to Virtual Threads. |

### Essential JVM Command-Line Diagnostic Tools
```bash
jps -l                  # List running Java processes with PID
jstat -gcutil <pid> 1000 # Inspect GC utilization every 1 second
jstack -l <pid>         # Generate thread dump (analyze deadlocks, blocked threads)
jcmd <pid> GC.heap_dump /path/dump.hprof # Generate live heap dump
```

