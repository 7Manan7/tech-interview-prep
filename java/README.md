# ☕ Java & Backend Engineering Interview Prep

This module covers Java deep-dives, JVM internals, multithreading, and backend architecture topics frequently asked in Senior/Staff Software Engineer interviews.

---

## 🗂️ Modules

| Module | Core Topics |
|---|---|
| **[Core Java & Collections](./core-java/README.md)** | Collections internals (`HashMap`, `ConcurrentHashMap`), equals/hashCode contract, String pool, Generics (PECS), Java 8–21 modern features. |
| **[Concurrency & Multithreading](./concurrency/README.md)** | Java Memory Model (JMM), `volatile`, locks, `ThreadPoolExecutor`, CAS, lock-free data structures, `CompletableFuture`, Virtual Threads. |
| **[JVM Internals & GC](./jvm/README.md)** | JVM architecture, ClassLoaders, Memory layout (Heap, Metaspace, Stack), JIT compilation, Garbage Collectors (G1, ZGC), heap dumps & tuning. |

---

## 🚀 Quick Knowledge Checks

### 1. The `equals()` and `hashCode()` Contract
- If `o1.equals(o2)` is `true`, then `o1.hashCode() == o2.hashCode()` **MUST** be `true`.
- If `o1.hashCode() == o2.hashCode()`, `o1.equals(o2)` is **NOT** necessarily `true` (hash collision).
- Overriding `equals()` without `hashCode()` breaks hash-based collections (`HashMap`, `HashSet`), causing duplicate keys or failed lookups.

### 2. Modern Java Key Additions (Java 8 to 21)
- **Java 8:** Lambda expressions, Stream API, `Optional`, Default/Static methods in interfaces, `java.time` API.
- **Java 11:** Local variable syntax for lambda parameters (`var`), HTTP Client API.
- **Java 17 (LTS):** Sealed classes, Pattern matching for `switch` / `instanceof`, Records (immutable data carriers), Text Blocks.
- **Java 21 (LTS):** Virtual Threads (Project Loom), Sequenced Collections, Pattern matching for switch finalized.

---

## 📚 Essential Reading
- *Effective Java (3rd Edition)* by Joshua Bloch
- *Java Concurrency in Practice* by Brian Goetz
- *JVM Troubleshooting and Performance Tuning Guide* (Oracle Documentation)

