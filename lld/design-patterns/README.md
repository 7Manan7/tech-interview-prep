# 🎨 Design Patterns in Java (GoF)

Design patterns are reusable solutions to common problems in software design. In technical interviews, interviewers evaluate whether you select the right pattern for a given business requirement.

---

## 🏗️ 1. Creational Patterns
*Deal with object creation mechanisms to increase flexibility and reuse.*

| Pattern | Purpose | Common Real-World / JDK Usage |
|---|---|---|
| **Singleton** | Ensures a class has only one instance, with a global point of access. | `Runtime.getRuntime()`, Connection Pool managers. (Use Bill Pugh or Enum implementation). |
| **Factory Method** | Defines an interface for creating an object, but lets subclasses decide which class to instantiate. | `Calendar.getInstance()`, `NumberFormat.getInstance()`. |
| **Abstract Factory** | Provides an interface for creating families of related or dependent objects without specifying concrete classes. | UI Toolkits (DarkThemeFactory vs LightThemeFactory), Cross-platform widget creation. |
| **Builder** | Separates the construction of a complex object from its representation. Prevents telescoping constructors. | `StringBuilder`, `Locale.Builder`, Lombok `@Builder`, HttpRequest in Java 11+. |
| **Prototype** | Creates new objects by copying an existing instance (cloning). | `Object.clone()`, Prototype beans in Spring. |

---

## 🧱 2. Structural Patterns
*Concerned with how classes and objects are composed to form larger structures.*

| Pattern | Purpose | Common Real-World / JDK Usage |
|---|---|---|
| **Adapter** | Converts the interface of a class into another interface clients expect. | `Arrays.asList()`, `InputStreamReader(InputStream)`. |
| **Decorator** | Attaches additional responsibilities to an object dynamically without modifying its code. | `BufferedInputStream(FileInputStream)`, Coffee ordering with toppings. |
| **Proxy** | Provides a surrogate or placeholder for another object to control access to it (lazy loading, caching, auth, logging). | Spring `@Transactional` (AOP proxies), Hibernate Lazy Loading, `java.lang.reflect.Proxy`. |
| **Facade** | Provides a unified, simplified interface to a set of interfaces in a subsystem. | Spring Boot Starters, a simplified Order Placement Facade hiding Inventory, Payment, and Notification services. |
| **Composite** | Composes objects into tree structures to represent part-whole hierarchies. | File system (Files and Folders), DOM trees. |

---

## 🔄 3. Behavioral Patterns
*Concerned with algorithms and the assignment of responsibilities between objects.*

| Pattern | Purpose | Common Real-World / JDK Usage |
|---|---|---|
| **Strategy** | Defines a family of algorithms, encapsulates each one, and makes them interchangeable at runtime. | Payment processing (UPI / Card / NetBanking), Sorting strategies (`Comparator`). |
| **Observer** | Defines a one-to-many dependency so that when one object changes state, all its dependents are notified automatically. | Event listeners, Kafka pub/sub consumer groups, Spring ApplicationEvent. |
| **State** | Allows an object to alter its behavior when its internal state changes. Replaces giant nested `if-else` / `switch` state checks. | Vending Machine states (NoCoin, HasCoin, Dispensing), Order status (Placed, Shipped, Delivered). |
| **Command** | Encapsulates a request as an object, allowing parameterization of clients with queues, requests, and undoable operations. | `Runnable`, Transaction management, Remote controls. |
| **Chain of Responsibility** | Passes the request along a chain of handlers until one handles it. | Servlet Filters, Spring Security filter chain, logging frameworks. |
| **Template Method** | Defines the skeleton of an algorithm in an operation, deferring some steps to subclasses. | `HttpServlet` (`doGet()`, `doPost()`), Spring `JdbcTemplate`. |

---

## 💡 Quick Tips for LLD Rounds
1. **Don't force patterns:** Apply a pattern only when it genuinely solves extensibility or separation of concerns.
2. **Strategy vs State:**
   - **Strategy:** The client chooses the strategy upfront to execute a specific behavior.
   - **State:** The context changes its internal state transitions dynamically as events happen.
3. **Decorator vs Proxy:**
   - **Decorator:** Adds new responsibilities / features dynamically.
   - **Proxy:** Controls access, manages lifecycle, or provides caching / lazy-initialization without altering behavior.

