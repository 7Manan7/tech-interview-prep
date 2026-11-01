# 📐 Low-Level Design (LLD) & Machine Coding

Low-Level Design (LLD) assesses your ability to write modular, extensible, testable, and maintainable object-oriented code under timed constraints (usually 60–90 minutes in machine coding rounds).

---

## 🗂️ Guides & Sub-sections

1. 📖 **[LLD & Machine Coding Master Guide](./lld-guide.md)**: Comprehensive deep-dive covering all 7 pillars with full explanations, complete Java code solutions, UML diagrams, concurrency patterns, and database schemas.
2. 🎨 **[Design Patterns in Java](./design-patterns/README.md)**: Quick reference matrix of Gang of Four (GoF) patterns, with complete code in the **[Design Patterns Implementation Guide](./design-patterns/patterns-guide.md)**.
3. 💻 **[Classic Machine Coding Problems](./problems/README.md)**: High-frequency problem index and cheat sheet, with detailed solutions in the **[Case Studies Deep-Dive](./problems/case-studies.md)**.

---

## 🏛️ The 7 Pillars of Low-Level Design

| # | Pillar | Focus & Key Concepts | Deep Dive |
|---|---|---|---|
| 1 | **Object-Oriented Modeling** | Four OOP pillars, Rich Domain Model vs. Anemic Model, Aggregation vs. Composition, Rich Enums, UML Diagrams | [Section 1](./lld-guide.md#1-object-oriented-modeling--class-relationships) |
| 2 | **Core Design Principles** | SOLID (SRP, OCP, LSP, ISP, DIP) with Bad vs. Good Java refactoring, DRY, KISS, YAGNI | [Section 2](./lld-guide.md#2-core-software-design-principles) |
| 3 | **Design Patterns (GoF)** | Creational (Singleton, Factory, Builder), Behavioral (Strategy, Observer, State, CoR, Command), Structural (Decorator, Adapter, Facade, Proxy) | [Section 3](./lld-guide.md#3-high-frequency-design-patterns-gang-of-four) |
| 4 | **Concurrency & Thread-Safety** | `volatile`, `synchronized`, `ReentrantLock`, `ReadWriteLock`, CAS atomics, `ConcurrentHashMap`, fine-grained resource locking | [Section 4](./lld-guide.md#4-concurrency--thread-safety-the-sde-2-differentiator) |
| 5 | **Machine Coding Architecture** | 6-tier package structure (`models`, `repositories`, `strategies`, `services`, `exceptions`, `Main`), in-memory secondary indexing | [Section 5](./lld-guide.md#5-machine-coding-architecture--execution-6090-minute-rounds) |
| 6 | **Database & API Extensions** | Relational mapping (1NF–3NF SQL schema), Optimistic (OCC) vs. Pessimistic (`FOR UPDATE`) locking, REST contracts | [Section 6](./lld-guide.md#6-database-schema--api-contract-extensions) |
| 7 | **Categorized Case Studies** | 21 problems across Booking, State Machines, Marketplaces, Turn-Based Games, and Backend Infrastructure | [Section 7](./lld-guide.md#7-must-practice-lld-case-studies-by-category) |

---

## 🏛️ SOLID Principles (Quick Overview)

### 1. Single Responsibility Principle (SRP)
*A class should have one, and only one, reason to change.*
- **Violation:** A `User` class managing both user profile data and database persistence/validation.
- **Solution:** Split into `User`, `UserRepository`, and `UserValidator`.

### 2. Open / Closed Principle (OCP)
*Software entities should be open for extension, but closed for modification.*
- **Solution:** Use polymorphic interfaces and strategy dispatch. Adding a new payment type or vehicle type requires creating a new class, never editing existing `switch-case` blocks.

### 3. Liskov Substitution Principle (LSP)
*Subtypes must be substitutable for their base types without altering program correctness.*
- **Violation:** A subtype throwing `UnsupportedOperationException` for an inherited method (e.g. `ReadOnlyFile` extending `File`).
- **Solution:** Segregate interfaces (`ReadableFile`, `WritableFile`).

### 4. Interface Segregation Principle (ISP)
*Clients should not be forced to depend upon interfaces that they do not use.*
- **Solution:** Favor many small, client-specific interfaces (`Printable`, `Scannable`) over one large bloated interface (`SmartDevice`).

### 5. Dependency Inversion Principle (DIP)
*High-level modules should not depend on low-level modules. Both should depend on abstractions.*
- **Solution:** Inject interface dependencies via constructors rather than calling `new ConcreteClass()` inside services.

---

## ⏱️ Machine Coding Round: Step-by-Step Framework (90 Minutes)

```
00-15 min: Clarify Requirements & Define Functional Scope
15-25 min: Identify Core Entities, Value Objects & Relationships
25-35 min: Define Enums, Interfaces, and Contracts (APIs)
35-65 min: Implement Core Business Logic & State Transitions
65-75 min: Add Concurrency Controls (Thread Safety) & Edge Case Validations
75-90 min: Write Driver/Main class with test cases verifying all acceptance criteria
```

### Essential Checklist for LLD Interviews
- [ ] Are class and variable names clear and self-documenting?
- [ ] Is input validation handled cleanly at the service boundary?
- [ ] Are appropriate design patterns applied naturally (not forced)?
- [ ] Is mutable state protected across concurrent threads (`ConcurrentHashMap`, `Atomic*`, `synchronized`, `ReentrantLock`)?
- [ ] Are in-memory lookup maps used instead of linear scans?
- [ ] Is the code runnable from a `main()` driver with clean console outputs?
