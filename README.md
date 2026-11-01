# 🚀 Tech Interview Prep: Java & Backend Engineering

A curated, comprehensive guide and code repository for cracking Technical Software Engineering Interviews (SDE I, SDE II, SDE III / Staff). Covers Data Structures & Algorithms, Low-Level Design (Machine Coding & Design Patterns), High-Level System Design, and Core Java / Concurrency / JVM internals.

---

## 📚 Repository Map

| Section | Focus Area | Key Highlights |
| :--- | :--- | :--- |
| **[🧩 Data Structures & Algorithms (DSA)](./dsa/README.md)** | Problem Solving & LeetCode Patterns | • Complete [NeetCode 150 Java Solutions](./dsa/neetcode150.md) with code & explanations<br>• Two Pointers, Sliding Window, DP, Trees, Graphs |
| **[📐 Low-Level Design (LLD)](./lld/README.md)** | Object-Oriented Design & Machine Coding | • Complete [LLD Master Guide](./lld/lld-guide.md) (All 7 Pillars with code & schemas)<br>• [Gang of Four Design Patterns](./lld/design-patterns/README.md) & [Implementations](./lld/design-patterns/patterns-guide.md)<br>• [Categorized Case Studies](./lld/problems/README.md) & [Solutions](./lld/problems/case-studies.md) |
| **[🏛️ High-Level Design (HLD)](./hld/README.md)** | Distributed Systems & Architecture | • System Design Framework & Scaling Strategies<br>• Caching, DB Sharding, Message Queues, CAP Theorem<br>• Case Studies (URL Shortener, Chat App, Ride Sharing, Netflix) |
| **[☕ Java & Backend Engineering](./java/README.md)** | Language Deep Dive & Concurrency | • Core Java, Collections internals & Java 8–21 features<br>• [Multithreading & Concurrency](./java/concurrency/README.md) (Locks, ThreadPools, Virtual Threads)<br>• [JVM Internals & Performance](./java/jvm/README.md) (Memory Model, GC algorithms, JIT) |

---

## 🗂️ Directory Structure

```text
tech-interview-prep/
├── README.md
├── dsa/
│   ├── README.md                 # DSA strategy, patterns, complexity cheat sheet
│   └── neetcode150.md            # NeetCode 150 in Java (code, tests & explanations)
├── lld/
│   ├── README.md                 # LLD overview, SOLID, 7 pillars & 90-min checklist
│   ├── lld-guide.md              # Complete 7-pillar master guide with code solutions
│   ├── design-patterns/
│   │   ├── README.md             # GoF patterns reference matrix
│   │   └── patterns-guide.md     # Production-grade Java pattern implementations
│   └── problems/
│       ├── README.md             # Categorized problem index & 5 archetypes
│       └── case-studies.md       # Case studies deep-dive with code & algorithms
├── hld/
│   └── README.md                 # System design framework, components & case studies
└── java/
    ├── README.md                 # Java overview & core concepts
    ├── core-java/                # Collections, OOP concepts, Memory & Streams
    ├── concurrency/              # Multithreading, synchronizers, thread pools & lock-free
    └── jvm/                      # ClassLoaders, JVM memory model & Garbage Collectors
```

---

## 🎯 12-Week Preparation Roadmap

```
Week 01-04: Data Structures & Core Algorithms (NeetCode 150 + Patterns)
Week 05-06: Core Java Deep Dive & Concurrency (Memory Model, Thread Safety, ExecutorService)
Week 07-08: Object-Oriented Design & Design Patterns (SOLID + GoF in Java)
Week 09-10: Machine Coding Practice (90-minute timed LLD problems)
Week 11-12: High-Level System Design (Components, Trade-offs & Real-World Architectures)
```

### 1. Data Structures & Algorithms
- Master the fundamental patterns (Sliding Window, Two Pointers, Fast & Slow Pointers, Monotonic Stack, Backtracking, Graph Traversals, Top-Down & Bottom-Up DP).
- Complete the 150 problems in [`dsa/neetcode150.md`](./dsa/neetcode150.md).

### 2. Java & Concurrency Mastery
- Understand `HashMap` / `ConcurrentHashMap` internal bucketing, treeification, and resizing.
- Master Java Memory Model (JMM), `volatile`, `synchronized`, `ReentrantLock`, `Condition`, `AtomicInteger`, and `CompletableFuture`.
- JVM architecture: Heap, Metaspace, Stack, JIT compilation, and Garbage Collection (G1, ZGC).

### 3. Low-Level Design (LLD) & Machine Coding
- Implement working, extensible, modular code under timed constraints (usually 90-120 minutes).
- Apply SOLID principles naturally (Single Responsibility, Open-Closed, Strategy pattern, State pattern, Factory, Observer).

### 4. High-Level Design (HLD)
- Master back-of-the-envelope estimations (QPS, storage, bandwidth).
- Design resilient distributed architectures using CDN, Load Balancers, API Gateways, Distributed Caching (Redis), Relational vs NoSQL DBs, and Message Queues (Kafka/RabbitMQ).

---

## 🛠️ How to Contribute & Use

1. **Clone the repository:**
   ```bash
   git clone https://github.com/7Manan7/tech-interview-prep.git
   cd tech-interview-prep
   ```
2. **Explore topic by topic:** Each folder contains self-contained explanations, code implementations, diagrams, and runnable examples.
3. **Run Java solutions locally:** Each solution in `dsa/neetcode150.md` includes a runnable `main` method.

---

## 📄 License
This repository is open-sourced under the MIT License.

