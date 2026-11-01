# 📐 Low-Level Design (LLD) & Machine Coding

Low-Level Design (LLD) assesses your ability to write modular, extensible, testable, and maintainable object-oriented code under timed constraints (usually 90–120 minutes in machine coding rounds).

---

## 🗂️ Sub-sections

1. **[Design Patterns in Java](./design-patterns/README.md)**: Creational, Structural, and Behavioral patterns with idiomatic Java implementations.
2. **[Classic Machine Coding Problems](./problems/README.md)**: Standard problem statements, UML class diagrams, and end-to-end working solutions.

---

## 🏛️ SOLID Principles (The Foundation)

### 1. Single Responsibility Principle (SRP)
*A class should have one, and only one, reason to change.*
- **Violation:** A `User` class managing both user profile data and database persistence/validation.
- **Solution:** Split into `User`, `UserRepository`, and `UserValidator`.

### 2. Open / Closed Principle (OCP)
*Software entities should be open for extension, but closed for modification.*
- **Solution:** Use interfaces and strategy/polymorphic dispatch. Adding a new payment type or notification channel should only require creating a new class implementing an interface, never editing existing `switch-case` blocks.

### 3. Liskov Substitution Principle (LSP)
*Subtypes must be substitutable for their base types without altering program correctness.*
- **Classic Counterexample:** `Square` extending `Rectangle` where setting width alters height.
- **Rule of Thumb:** If an override throws `UnsupportedOperationException`, it violates LSP.

### 4. Interface Segregation Principle (ISP)
*Clients should not be forced to depend upon interfaces that they do not use.*
- **Solution:** Favor many small, client-specific interfaces (e.g., `Printable`, `Scannable`, `Faxable`) over one large bloated interface (`Machine`).

### 5. Dependency Inversion Principle (DIP)
*High-level modules should not depend on low-level modules. Both should depend on abstractions.*
- Depend on interfaces rather than concrete implementations (e.g., depend on `PaymentGateway`, not `StripePaymentGatewayImpl`).

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
- [ ] Is input validation handled cleanly (e.g., `null`, boundary values, invalid states)?
- [ ] Are appropriate design patterns applied naturally (not forced)?
- [ ] Is mutable state protected across concurrent threads (`ConcurrentHashMap`, `Atomic*`, `synchronized`, `ReentrantReadWriteLock`)?
- [ ] Is the code runnable from a `main()` driver with clean console outputs?

