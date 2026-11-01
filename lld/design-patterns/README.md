# 🎨 Design Patterns in Java (GoF)

Design patterns are reusable solutions to common problems in software design. In technical interviews, interviewers evaluate whether you select the right pattern for a given business requirement.

> 📖 **Full Implementation Guide**: For complete, runnable Java implementations of each pattern, see **[Design Patterns Implementation Guide](./patterns-guide.md)** or the **[LLD Master Guide Section 3](../lld-guide.md#3-high-frequency-design-patterns-gang-of-four)**.

---

## 🏗️ 1. Creational Patterns
*Deal with object creation mechanisms to increase flexibility and reuse.*

| Pattern | Purpose | Common Real-World / JDK Usage | Detailed Code |
|---|---|---|---|
| **Singleton** | Ensures a class has only one instance, with a global point of access. | `Runtime.getRuntime()`, Connection Pool managers. (DCL with `volatile`, Bill Pugh, Enum). | [View Code](./patterns-guide.md#11-singleton-pattern) |
| **Factory Method** | Defines an interface for creating an object, but lets subclasses decide which class to instantiate. | `Calendar.getInstance()`, `NumberFormat.getInstance()`. | [View Code](./patterns-guide.md#12-factory-method-pattern) |
| **Abstract Factory** | Provides an interface for creating families of related or dependent objects without specifying concrete classes. | UI Toolkits (DarkThemeFactory vs LightThemeFactory), Cross-platform widget creation. | [View Code](./patterns-guide.md#13-abstract-factory-pattern) |
| **Builder** | Separates the construction of a complex object from its representation. Prevents telescoping constructors. | `StringBuilder`, `HttpRequest`, Lombok `@Builder`. | [View Code](./patterns-guide.md#14-builder-pattern) |
| **Prototype** | Creates new objects by copying an existing instance (cloning). | `Object.clone()`, Prototype beans in Spring. | — |

---

## 🧱 2. Structural Patterns
*Concerned with how classes and objects are composed to form larger structures.*

| Pattern | Purpose | Common Real-World / JDK Usage | Detailed Code |
|---|---|---|---|
| **Decorator** | Attaches additional responsibilities to an object dynamically without modifying its code. | `BufferedInputStream(FileInputStream)`, Coffee toppings, Fare surcharges. | [View Code](./patterns-guide.md#41-decorator-pattern) |
| **Adapter** | Converts the interface of a class into another interface clients expect. | `Arrays.asList()`, `InputStreamReader(InputStream)`, 3rd-party payment SDKs. | [View Code](./patterns-guide.md#42-adapter-pattern) |
| **Facade** | Provides a unified, simplified interface to a set of interfaces in a subsystem. | Spring Boot Starters, Order Placement Facade hiding Inventory, Payment, and Shipping. | [View Code](./patterns-guide.md#43-facade-pattern) |
| **Proxy** | Provides a surrogate or placeholder for another object to control access to it (lazy loading, caching, auth). | Spring `@Transactional` (AOP proxies), Hibernate Lazy Loading, Caching Proxy. | [View Code](./patterns-guide.md#44-proxy-pattern) |
| **Composite** | Composes objects into tree structures to represent part-whole hierarchies. | File system (Files and Folders), DOM trees. | — |

---

## 🔄 3. Behavioral Patterns
*Concerned with algorithms and the assignment of responsibilities between objects.*

| Pattern | Purpose | Common Real-World / JDK Usage | Detailed Code |
|---|---|---|---|
| **Strategy** | Defines a family of algorithms, encapsulates each one, and makes them interchangeable at runtime. | Payment processing (UPI / Card), Pricing strategies, Sorting (`Comparator`). | [View Code](./patterns-guide.md#21-strategy-pattern) |
| **Observer** | Defines a one-to-many dependency so that when one object changes state, all its dependents are notified automatically. | Event listeners, Kafka pub/sub consumer groups, Spring ApplicationEvent. | [View Code](./patterns-guide.md#22-observer-pattern) |
| **State** | Allows an object to alter its behavior when its internal state changes. Replaces giant nested `if-else` / `switch` checks. | Vending Machine states (NoCoin, HasCoin, Dispensing), Order status (Placed, Shipped). | [View Code](./patterns-guide.md#23-state-pattern) |
| **Chain of Responsibility** | Passes the request along a chain of handlers until one handles it. | ATM note dispensers ($100 $\to$ $50 $\to$ $20), Servlet Filters, Logging frameworks. | [View Code](./patterns-guide.md#31-chain-of-responsibility-pattern) |
| **Command** | Encapsulates a request as an object, allowing parameterization of clients with queues, requests, and undoable operations. | `Runnable`, Transaction management, Text Editor Undo/Redo. | [View Code](./patterns-guide.md#32-command-pattern) |
| **Template Method** | Defines the skeleton of an algorithm in an operation, deferring some steps to subclasses. | `HttpServlet` (`doGet()`, `doPost()`), Spring `JdbcTemplate`. | [View Code](../lld-guide.md#13-interfaces-vs-abstract-classes) |

---

## 💡 Quick Tips for LLD Rounds
1. **Don't force patterns:** Apply a pattern only when it genuinely solves extensibility or separation of concerns.
2. **Strategy vs State:**
   - **Strategy:** The client chooses the strategy upfront to execute a specific behavior.
   - **State:** The context changes its internal state transitions dynamically as events happen.
3. **Decorator vs Proxy:**
   - **Decorator:** Adds new responsibilities / features dynamically.
   - **Proxy:** Controls access, manages lifecycle, or provides caching / lazy-initialization without altering behavior.
