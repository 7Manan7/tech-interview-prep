# 🎨 Gang of Four (GoF) Design Patterns — Java Implementation Guide

A comprehensive, production-grade implementation and architectural guide for the most frequently tested Design Patterns in Low-Level Design (LLD) and Machine Coding interviews for SDE-2, SDE-3, and Staff Engineering rounds.

---

## 📑 Table of Contents

1. [Creational Patterns](#1-creational-patterns)
   - [1.1 Singleton Pattern (DCL, Bill Pugh, Enum)](#11-singleton-pattern)
   - [1.2 Factory Method Pattern](#12-factory-method-pattern)
   - [1.3 Abstract Factory Pattern](#13-abstract-factory-pattern)
   - [1.4 Builder Pattern](#14-builder-pattern)
2. [Behavioral Patterns (Tier 1)](#2-behavioral-patterns-tier-1)
   - [2.1 Strategy Pattern](#21-strategy-pattern)
   - [2.2 Observer Pattern](#22-observer-pattern)
   - [2.3 State Pattern](#23-state-pattern)
3. [Behavioral Patterns (Tier 2)](#3-behavioral-patterns-tier-2)
   - [3.1 Chain of Responsibility Pattern](#31-chain-of-responsibility-pattern)
   - [3.2 Command Pattern](#32-command-pattern)
4. [Structural Patterns](#4-structural-patterns)
   - [4.1 Decorator Pattern](#41-decorator-pattern)
   - [4.2 Adapter Pattern](#42-adapter-pattern)
   - [4.3 Facade Pattern](#43-facade-pattern)
   - [4.4 Proxy Pattern](#44-proxy-pattern)
5. [Interview Heuristics & Decision Framework](#5-interview-heuristics--decision-framework)

---

# 1. Creational Patterns

Creational patterns abstract the instantiation process, making systems independent of how their objects are created, composed, and represented.

---

### 1.1 Singleton Pattern

#### 🎯 Intent & Motivation
Ensure a class has **only one instance** throughout the entire application lifecycle and provide a global, controlled access point to it. Common production use cases include:
- Database Connection Pools & Thread Pools
- Configuration Managers & Feature Flag Registries
- Hardware Drivers & Cache Managers

#### ⚙️ Deep-Dive Mechanics & Thread-Safety Approaches

```
+--------------------------------------------------------------------------+
|                     Singleton Implementation Approaches                  |
+------------------------------+--------------------+----------------------+
| Approach                     | Thread-Safe?       | Lazy Loaded?         |
+------------------------------+--------------------+----------------------+
| 1. Double-Checked Locking    | Yes (via volatile) | Yes                  |
| 2. Bill Pugh Holder Class    | Yes (ClassLoader)  | Yes                  |
| 3. Enum Singleton            | Yes (JVM native)   | Yes (on first access)|
+------------------------------+--------------------+----------------------+
```

##### 1. Why Double-Checked Locking (DCL) Requires `volatile`:
Without `volatile`, the Java Memory Model allows compiler and CPU **instruction reordering** during object initialization. Creating an object in Java executes three distinct steps under the hood:
1. `mem = allocate();` // Allocate memory for object
2. `ctor(mem);`         // Initialize object (execute constructor)
3. `instance = mem;`    // Assign reference to the variable

If instructions are reordered to **1 → 3 → 2**:
- Thread A executes 1 and 3 (assigning the memory address to `instance` before the constructor completes).
- Thread B invokes `getInstance()`, checks `if (instance == null)`, observes `instance != null` (due to step 3), and returns the reference.
- Thread B attempts to access object fields on a **half-initialized, corrupted object**, resulting in fatal runtime crashes.
- Marking `instance` as `volatile` establishes a **happens-before memory barrier**, preventing instruction reordering across the write.

##### 2. Bill Pugh Singleton Holder:
Exploits the JVM specification's ClassLoader mechanics: inner static classes are **not loaded** when the outer class is loaded. The inner class is only loaded and initialized when `getInstance()` is called, achieving lazy loading with zero synchronization overhead.

##### 3. Enum Singleton (Effective Java Recommendation):
An `enum` singleton provides 100% thread safety, lazy initialization, and is natively immune to both **reflection attacks** (`Constructor.setAccessible(true)`) and **serialization duplication attacks** (Java guarantees enum instances cannot be duplicated via serialization).

#### 💻 Production-Ready Java Implementations

```java
import java.util.Map;
import java.util.concurrent.ConcurrentHashMap;

// Approach A: Double-Checked Locking (DCL) with volatile
public class DatabaseConnectionPool {
    private static volatile DatabaseConnectionPool instance;

    private DatabaseConnectionPool() {
        // Reflection guard: prevent instantiation via reflection
        if (instance != null) {
            throw new IllegalStateException("Instance already exists! Use getInstance().");
        }
    }

    public static DatabaseConnectionPool getInstance() {
        if (instance == null) {                         // Check 1 (no locking overhead after init)
            synchronized (DatabaseConnectionPool.class) { // Lock only during initial race
                if (instance == null) {                 // Check 2 (verify after acquiring lock)
                    instance = new DatabaseConnectionPool();
                }
            }
        }
        return instance;
    }
}

// Approach B: Bill Pugh Singleton Holder (Thread-safe without synchronization)
public class CacheRegistry {
    private CacheRegistry() {}

    private static class InstanceHolder {
        private static final CacheRegistry INSTANCE = new CacheRegistry();
    }

    public static CacheRegistry getInstance() {
        return InstanceHolder.INSTANCE;
    }
}

// Approach C: Enum Singleton (Recommended by Joshua Bloch)
public enum ConfigurationService {
    INSTANCE;

    private final Map<String, String> configs = new ConcurrentHashMap<>();

    public void setConfig(String key, String value) { configs.put(key, value); }
    public String getConfig(String key) { return configs.get(key); }
}
```

#### ⚠️ Interview Traps & Pitfalls
- **Overuse as a Global Variable**: Leads to tight coupling, hidden dependencies across classes, and difficult unit testing (mocking singletons is notoriously difficult).
- **Multiple ClassLoaders**: In enterprise container environments (e.g., OSGi or multiple webapp classloaders), each classloader can load its own copy of the singleton unless loaded by the root parent classloader.

---

### 1.2 Factory Method Pattern

#### 🎯 Intent & Motivation
Define an interface for creating an object, but **defer instantiation to subclasses or factory dispatchers**. Decouples the client caller from the concrete implementation classes, adhering strictly to the **Open/Closed Principle (OCP)**.

#### ⚙️ Deep-Dive Mechanics
- **Simple Factory vs. Factory Method**: A "Simple Factory" uses a static method with a conditional `switch-case` block. Adding a new vehicle type requires modifying the factory class (violating OCP). A true **Factory Method** pattern defines a factory interface or abstract class with an abstract `createVehicle()` method that specialized factory subclasses implement.
- **Client Decoupling**: Clients program exclusively against high-level interfaces (`Vehicle`), never referencing concrete implementations (`Bike`, `Car`, `Truck`).

#### 💻 Production-Ready Java Implementation

```java
public interface Vehicle {
    void drive();
    double getCostPerHour();
}

public class Bike implements Vehicle {
    @Override public void drive() { System.out.println("Riding motorcycle"); }
    @Override public double getCostPerHour() { return 10.0; }
}

public class Car implements Vehicle {
    @Override public void drive() { System.out.println("Driving sedan"); }
    @Override public double getCostPerHour() { return 25.0; }
}

public class Truck implements Vehicle {
    @Override public void drive() { System.out.println("Driving transport truck"); }
    @Override public double getCostPerHour() { return 60.0; }
}

// Factory Method Interface
public interface VehicleFactory {
    Vehicle createVehicle();
}

public class BikeFactory implements VehicleFactory {
    @Override public Vehicle createVehicle() { return new Bike(); }
}

public class CarFactory implements VehicleFactory {
    @Override public Vehicle createVehicle() { return new Car(); }
}

public class TruckFactory implements VehicleFactory {
    @Override public Vehicle createVehicle() { return new Truck(); }
}
```

#### ⚠️ Interview Traps & Pitfalls
- **Class Explosion**: If every simple product class requires its own dedicated factory subclass, you double the total class count. Use parameterized factory methods when subclassing overhead outweighs architectural benefits.

---

### 1.3 Abstract Factory Pattern

#### 🎯 Intent & Motivation
Provide an interface for creating **families of related or dependent objects** without specifying their concrete classes. It guarantees that client code receives compatible components belonging to the same product family (e.g., Light Theme vs. Dark Theme UI components).

#### ⚙️ Deep-Dive Mechanics
- **Product Families**: An Abstract Factory groups related factory methods together. For example, a `ThemeFactory` provides both `createButton()` and `createCheckbox()`.
- **Enforcing Consistency**: Prevents clients from accidentally combining incompatible variants (e.g., rendering a `LightButton` alongside a `DarkCheckbox`).
- **Parallel Class Hierarchies**: The factory hierarchy mirrors the product family hierarchy.

```
       +--------------------+
       |   <<interface>>    |
       |    ThemeFactory    |<---------------------+
       +--------------------+                      |
       | +createButton()    |                      |
       | +createCheckbox()  |                      |
       +---------+----------+                      |
                 ^                                 ^
                 |                                 |
     +-----------+-----------+         +-----------+-----------+
     |   LightThemeFactory   |         |    DarkThemeFactory   |
     +-----------------------+         +-----------------------+
     | +createButton(): Light|         | +createButton(): Dark |
     | +createCheckbox(): Lgt|         | +createCheckbox(): Drk|
     +-----------------------+         +-----------------------+
```

#### 💻 Production-Ready Java Implementation

```java
public interface Button { void render(); }
public interface Checkbox { void render(); }

// Light Theme Family
public class LightButton implements Button {
    @Override public void render() { System.out.println("Render Light Button"); }
}
public class LightCheckbox implements Checkbox {
    @Override public void render() { System.out.println("Render Light Checkbox"); }
}

// Dark Theme Family
public class DarkButton implements Button {
    @Override public void render() { System.out.println("Render Dark Button"); }
}
public class DarkCheckbox implements Checkbox {
    @Override public void render() { System.out.println("Render Dark Checkbox"); }
}

// Abstract Factory Contract
public interface ThemeFactory {
    Button createButton();
    Checkbox createCheckbox();
}

public class LightThemeFactory implements ThemeFactory {
    @Override public Button createButton() { return new LightButton(); }
    @Override public Checkbox createCheckbox() { return new LightCheckbox(); }
}

public class DarkThemeFactory implements ThemeFactory {
    @Override public Button createButton() { return new DarkButton(); }
    @Override public Checkbox createCheckbox() { return new DarkCheckbox(); }
}
```

#### ⚠️ Interview Traps & Pitfalls
- **Extending Product Families**: Adding a new product (e.g., `createScrollbar()`) requires modifying the `ThemeFactory` interface and all existing concrete factory implementations.

---

### 1.4 Builder Pattern

#### 🎯 Intent & Motivation
Separate the construction of a complex object from its representation, allowing the same construction process to create diverse representations.
Solves two classical anti-patterns:
1. **Telescoping Constructor Antipattern**: Multiple constructors with 4+ parameters where callers can easily swap arguments of the same type (`new Booking("user1", "res1", null, null, true, false)`).
2. **JavaBeans Mutability Antipattern**: Calling an empty constructor followed by numerous setters leaves the object in an inconsistent, mutable state across threads.

#### ⚙️ Deep-Dive Mechanics
- **Immutability**: The target object has only `getters` and private constructors, ensuring that once built, its internal state cannot be tampered with.
- **Fluent Chaining**: Builder methods return `this` to enable clean method chaining.
- **Cross-Field Invariant Enforcement**: Validation logic is placed inside the `build()` method, guaranteeing that invalid objects can never be constructed.

#### 💻 Production-Ready Java Implementation

```java
import java.time.Instant;
import java.util.Objects;

public final class ReservationRequest {
    private final String userId;
    private final String resourceId;
    private final Instant startTime;
    private final Instant endTime;
    private final String promoCode;
    private final boolean insuranceOptIn;

    private ReservationRequest(Builder builder) {
        this.userId = builder.userId;
        this.resourceId = builder.resourceId;
        this.startTime = builder.startTime;
        this.endTime = builder.endTime;
        this.promoCode = builder.promoCode;
        this.insuranceOptIn = builder.insuranceOptIn;
    }

    public String getUserId() { return userId; }
    public String getResourceId() { return resourceId; }
    public Instant getStartTime() { return startTime; }
    public Instant getEndTime() { return endTime; }
    public String getPromoCode() { return promoCode; }
    public boolean isInsuranceOptIn() { return insuranceOptIn; }

    public static class Builder {
        private final String userId;          // Mandatory
        private final String resourceId;      // Mandatory
        private Instant startTime;            // Optional / validated
        private Instant endTime;              // Optional / validated
        private String promoCode;             // Optional
        private boolean insuranceOptIn;       // Optional

        public Builder(String userId, String resourceId) {
            this.userId = Objects.requireNonNull(userId, "userId cannot be null");
            this.resourceId = Objects.requireNonNull(resourceId, "resourceId cannot be null");
        }

        public Builder timeWindow(Instant start, Instant end) {
            this.startTime = start;
            this.endTime = end;
            return this;
        }

        public Builder promoCode(String promoCode) {
            this.promoCode = promoCode;
            return this;
        }

        public Builder withInsurance(boolean optIn) {
            this.insuranceOptIn = optIn;
            return this;
        }

        public ReservationRequest build() {
            // Enforce business invariant validation
            if (startTime == null || endTime == null) {
                throw new IllegalStateException("Start and End times must both be specified.");
            }
            if (!endTime.isAfter(startTime)) {
                throw new IllegalArgumentException("End time must be strictly after Start time.");
            }
            return new ReservationRequest(this);
        }
    }
}
```

---

# 2. Behavioral Patterns (Tier 1)

Behavioral patterns characterize the ways in which classes or objects interact and distribute responsibility.

---

### 2.1 Strategy Pattern

#### 🎯 Intent & Motivation
Define a family of algorithms, encapsulate each one into a standalone class, and make them **interchangeable at runtime**. Enables the algorithm to vary independently from clients that use it.
Production use cases:
- Dynamic pricing (Surge pricing vs. Flat pricing vs. Membership discount)
- Navigation routing (Fastest route vs. Shortest distance vs. Avoid tolls)
- Cache eviction algorithms (LRU, LFU, FIFO)

#### ⚙️ Deep-Dive Mechanics
- **Eliminating Conditionals**: Replaces brittle `switch(pricingType)` statements with polymorphic method dispatch.
- **Stateful vs. Stateless Strategies**: Stateless strategy instances can be cached and reused as Singletons across multiple threads. Stateful strategies require separate instances per context.

#### 💻 Production-Ready Java Implementation

```java
import java.math.BigDecimal;
import java.time.Instant;

public interface PricingStrategy {
    BigDecimal computePrice(BigDecimal baseFare, double distanceKm, Instant requestTime);
}

public class FlatPricingStrategy implements PricingStrategy {
    @Override
    public BigDecimal computePrice(BigDecimal baseFare, double distanceKm, Instant requestTime) {
        return baseFare.add(BigDecimal.valueOf(distanceKm * 2.0));
    }
}

public class SurgePricingStrategy implements PricingStrategy {
    private final double multiplier;

    public SurgePricingStrategy(double multiplier) {
        if (multiplier < 1.0) throw new IllegalArgumentException("Surge multiplier cannot be < 1.0");
        this.multiplier = multiplier;
    }

    @Override
    public BigDecimal computePrice(BigDecimal baseFare, double distanceKm, Instant requestTime) {
        BigDecimal standard = baseFare.add(BigDecimal.valueOf(distanceKm * 2.0));
        return standard.multiply(BigDecimal.valueOf(multiplier));
    }
}

public class FareContext {
    private PricingStrategy pricingStrategy;

    public FareContext(PricingStrategy initialStrategy) {
        this.pricingStrategy = initialStrategy;
    }

    public void setStrategy(PricingStrategy strategy) {
        this.pricingStrategy = strategy;
    }

    public BigDecimal calculate(BigDecimal base, double distance) {
        return pricingStrategy.computePrice(base, distance, Instant.now());
    }
}
```

---

### 2.2 Observer Pattern

#### 🎯 Intent & Motivation
Define a **one-to-many dependency** between objects so that when one object changes state, all its registered dependents are notified and updated automatically.
Foundation for:
- Event-Driven Architecture (EDA)
- In-memory Pub/Sub messaging
- Real-time notification systems (SMS, Email, Push alerts)

#### ⚙️ Deep-Dive Mechanics
- **Push vs. Pull Model**:
  - *Push Model*: The publisher pushes complete event data in the notification method parameter.
  - *Pull Model*: The publisher passes only an event ID or `this`, and subscribers query the publisher for data they need.
- **Concurrency & Memory Leaks**:
  - **Thread-Safety**: Iterating over a list of listeners while other threads register/unregister causes `ConcurrentModificationException`. Use `CopyOnWriteArrayList` to handle concurrent additions/removals safely.
  - **The Lapsed Listener Problem**: If listeners do not unregister, the publisher retains strong references to them, preventing Garbage Collection and causing memory leaks. Always provide an `unregister()` method.

#### 💻 Production-Ready Java Implementation

```java
import java.math.BigDecimal;
import java.util.List;
import java.util.Objects;
import java.util.concurrent.CopyOnWriteArrayList;

public record OrderEvent(String orderId, String customerId, BigDecimal totalAmount) {}

public interface OrderListener {
    void handleOrderPlaced(OrderEvent event);
}

public class EmailNotificationListener implements OrderListener {
    @Override public void handleOrderPlaced(OrderEvent event) {
        System.out.println("Email sent for order: " + event.orderId());
    }
}

public class InventoryReservationListener implements OrderListener {
    @Override public void handleOrderPlaced(OrderEvent event) {
        System.out.println("Inventory reserved for order: " + event.orderId());
    }
}

public class OrderEventPublisher {
    // Thread-safe collection allowing concurrent notifications during registration
    private final List<OrderListener> listeners = new CopyOnWriteArrayList<>();

    public void register(OrderListener listener) {
        listeners.add(Objects.requireNonNull(listener, "listener cannot be null"));
    }

    public void unregister(OrderListener listener) {
        listeners.remove(listener);
    }

    public void publish(OrderEvent event) {
        for (OrderListener listener : listeners) {
            try {
                listener.handleOrderPlaced(event);
            } catch (Exception ex) {
                System.err.println("Error notifying listener: " + ex.getMessage());
            }
        }
    }
}
```

---

### 2.3 State Pattern

#### 🎯 Intent & Motivation
Allow an object to **alter its behavior when its internal state changes**. The object will appear to change its class.
Production use cases:
- Vending Machines (`NoCoin`, `HasCoin`, `Dispensing`, `SoldOut`)
- Order Fulfillment Lifecycles (`Created`, `Paid`, `Shipped`, `Delivered`)
- Media Players (`Playing`, `Paused`, `Stopped`)

#### ⚙️ Deep-Dive Mechanics
- **FSM Implementation**: Models a Finite State Machine where states are represented by dedicated classes rather than numeric flags or string constants.
- **State Transition Ownership**:
  - *State-driven*: Concrete states decide and trigger transitions on the context (`context.setState(new HasCoinState())`).
  - *Context-driven*: The context inspects return values and manages the transition table. State-driven transitions are typically favored for complex workflows.

#### 💻 Production-Ready Java Implementation

```java
public interface VendingMachineState {
    void insertCoin(VendingMachine context, int amount);
    void selectItem(VendingMachine context, String itemCode);
    void dispense(VendingMachine context);
    void cancelAndRefund(VendingMachine context);
}

public class VendingMachine {
    private VendingMachineState currentState;
    private int balance;

    public VendingMachine() {
        this.currentState = new NoCoinState();
        this.balance = 0;
    }

    public void setState(VendingMachineState state) { this.currentState = state; }
    public void addBalance(int amount) { this.balance += amount; }
    public int getBalance() { return balance; }
    public void resetBalance() { this.balance = 0; }

    public void insertCoin(int amount) { currentState.insertCoin(this, amount); }
    public void selectItem(String code) { currentState.selectItem(this, code); }
    public void dispense() { currentState.dispense(this); }
    public void cancel() { currentState.cancelAndRefund(this); }
}

public class NoCoinState implements VendingMachineState {
    @Override
    public void insertCoin(VendingMachine context, int amount) {
        context.addBalance(amount);
        context.setState(new HasCoinState());
    }
    @Override public void selectItem(VendingMachine context, String code) { System.out.println("Insert coins first."); }
    @Override public void dispense(VendingMachine context) { System.out.println("Insert coins and select item."); }
    @Override public void cancelAndRefund(VendingMachine context) { System.out.println("No balance to refund."); }
}

public class HasCoinState implements VendingMachineState {
    @Override
    public void insertCoin(VendingMachine context, int amount) {
        context.addBalance(amount);
    }
    @Override
    public void selectItem(VendingMachine context, String itemCode) {
        context.setState(new DispensingState());
        context.dispense();
    }
    @Override public void dispense(VendingMachine context) { System.out.println("Select an item first."); }
    @Override
    public void cancelAndRefund(VendingMachine context) {
        int refund = context.getBalance();
        context.resetBalance();
        context.setState(new NoCoinState());
        System.out.println("Refunded: " + refund + " cents.");
    }
}

public class DispensingState implements VendingMachineState {
    @Override public void insertCoin(VendingMachine context, int amount) { System.out.println("Dispensing in progress. Wait."); }
    @Override public void selectItem(VendingMachine context, String code) { System.out.println("Dispensing in progress. Wait."); }
    @Override
    public void dispense(VendingMachine context) {
        System.out.println("Item dispensed!");
        context.resetBalance();
        context.setState(new NoCoinState());
    }
    @Override public void cancelAndRefund(VendingMachine context) { System.out.println("Cannot cancel during dispensing."); }
}
```

---

# 3. Behavioral Patterns (Tier 2)

---

### 3.1 Chain of Responsibility Pattern

#### 🎯 Intent & Motivation
Avoid coupling the sender of a request to its receiver by giving **more than one object a chance to handle the request**. Chain the receiving objects and pass the request along the chain until an object handles it or the chain terminates.
Production use cases:
- Logging frameworks (Log4j, SLF4J severity filtering)
- HTTP Middleware / Servlet Filters (`FilterChain.doFilter()`)
- ATM Cash note dispensing (\$100 → \$50 → \$20 → \$10)

#### ⚙️ Deep-Dive Mechanics
- **Chain Construction**: Each node contains a reference to the next handler (`nextLogger`).
- **Processing Variants**:
  - *Terminating*: Only one handler consumes the request (e.g. ATM dispensing).
  - *Fallthrough / Filter*: Every handler that meets criteria processes the request, then forwards to the next node (e.g. logging and security middleware).

#### 💻 Production-Ready Java Implementation

```java
public abstract class Logger {
    public static final int INFO = 1;
    public static final int DEBUG = 2;
    public static final int ERROR = 3;

    protected final int level;
    protected Logger nextLogger;

    public Logger(int level) {
        this.level = level;
    }

    public void setNextLogger(Logger nextLogger) {
        this.nextLogger = nextLogger;
    }

    public void logMessage(int level, String message) {
        if (this.level <= level) {
            write(message);
        }
        if (nextLogger != null) {
            nextLogger.logMessage(level, message);
        }
    }

    protected abstract void write(String message);
}

public class ConsoleLogger extends Logger {
    public ConsoleLogger(int level) { super(level); }
    @Override protected void write(String message) { System.out.println("[CONSOLE] " + message); }
}

public class FileLogger extends Logger {
    public FileLogger(int level) { super(level); }
    @Override protected void write(String message) { System.out.println("[FILE] " + message); }
}

public class ErrorEmailLogger extends Logger {
    public ErrorEmailLogger(int level) { super(level); }
    @Override protected void write(String message) { System.err.println("[EMAIL ALERT] " + message); }
}
```

---

### 3.2 Command Pattern

#### 🎯 Intent & Motivation
Encapsulate a request as an **object**, thereby letting you parameterize clients with different requests, queue or log requests, and support **undoable operations**.
Production use cases:
- Text editor undo/redo history
- Transaction rollback mechanisms
- Asynchronous task queues and job schedulers

#### ⚙️ Deep-Dive Mechanics
- **Decoupling Invoker and Receiver**: The caller (Invoker) only knows the `Command` interface (`execute()`, `undo()`), completely decoupled from the domain logic of the `Receiver` (`Document`).
- **Dual-Stack Undo / Redo Mechanism**:
  - When a command executes, push it onto `undoStack` and clear `redoStack`.
  - When `undo()` is requested: pop from `undoStack`, invoke `command.undo()`, and push onto `redoStack`.
  - When `redo()` is requested: pop from `redoStack`, invoke `command.execute()`, and push onto `undoStack`.

#### 💻 Production-Ready Java Implementation

```java
import java.util.ArrayDeque;
import java.util.Deque;

public interface Command {
    void execute();
    void undo();
}

// Receiver class containing actual domain operations
public class Document {
    private final StringBuilder content = new StringBuilder();

    public void write(String text) { content.append(text); }
    public void erase(int length) {
        content.delete(content.length() - length, content.length());
    }
    public String getContent() { return content.toString(); }
}

// Concrete Command
public class WriteCommand implements Command {
    private final Document document;
    private final String text;

    public WriteCommand(Document document, String text) {
        this.document = document;
        this.text = text;
    }

    @Override public void execute() { document.write(text); }
    @Override public void undo() { document.erase(text.length()); }
}

// Invoker managing command history
public class CommandInvoker {
    private final Deque<Command> undoStack = new ArrayDeque<>();
    private final Deque<Command> redoStack = new ArrayDeque<>();

    public void executeCommand(Command command) {
        command.execute();
        undoStack.push(command);
        redoStack.clear(); // Executing a new command invalidates redo history
    }

    public void undo() {
        if (!undoStack.isEmpty()) {
            Command cmd = undoStack.pop();
            cmd.undo();
            redoStack.push(cmd);
        }
    }

    public void redo() {
        if (!redoStack.isEmpty()) {
            Command cmd = redoStack.pop();
            cmd.execute();
            undoStack.push(cmd);
        }
    }
}
```

---

# 4. Structural Patterns

Structural patterns explain how to assemble objects and classes into larger structures while keeping them flexible and efficient.

---

### 4.1 Decorator Pattern

#### 🎯 Intent & Motivation
Attach **additional responsibilities to an object dynamically**. Decorators provide a flexible alternative to subclassing for extending functionality.
Production use cases:
- Java I/O Streams (`new BufferedReader(new FileReader("file.txt"))`)
- Stackable add-on pricing (Coffee toppings, car rental insurance add-ons)
- Dynamic HTTP request instrumentation (Authentication, Logging, Rate Limiting)

#### ⚙️ Deep-Dive Mechanics
- **Preventing Class Explosion**: Extending functionality with static inheritance creates combinatorial subclass growth ($N \times 2^M$ classes). Decorator composes features dynamically using only $N + M$ classes.
- **Recursive Wrapping**: The Decorator implements the same interface as the component it wraps and holds a reference to it. Calling a method delegates to the wrapped instance and adds additional behavior before/after.

#### 💻 Production-Ready Java Implementation

```java
import java.util.Objects;

public interface Beverage {
    String getDescription();
    double getCost();
}

public class Espresso implements Beverage {
    @Override public String getDescription() { return "Espresso"; }
    @Override public double getCost() { return 2.0; }
}

// Abstract Decorator implementing Beverage and wrapping Beverage
public abstract class AddOnDecorator implements Beverage {
    protected final Beverage beverage;

    public AddOnDecorator(Beverage beverage) {
        this.beverage = Objects.requireNonNull(beverage, "beverage cannot be null");
    }
}

public class Milk extends AddOnDecorator {
    public Milk(Beverage beverage) { super(beverage); }
    @Override public String getDescription() { return beverage.getDescription() + " + Milk"; }
    @Override public double getCost() { return beverage.getCost() + 0.5; }
}

public class Caramel extends AddOnDecorator {
    public Caramel(Beverage beverage) { super(beverage); }
    @Override public String getDescription() { return beverage.getDescription() + " + Caramel"; }
    @Override public double getCost() { return beverage.getCost() + 0.75; }
}
```

---

### 4.2 Adapter Pattern

#### 🎯 Intent & Motivation
Convert the interface of an existing class into another interface **that clients expect**. Allows classes with incompatible interfaces to collaborate seamlessly.
Production use cases:
- Integrating third-party payment gateways (Stripe, PayPal, Razorpay) with differing SDK method signatures
- Wrapping legacy XML APIs to match modern JSON contracts

#### ⚙️ Deep-Dive Mechanics
- **Object Adapter (Composition)**: The adapter holds a reference to the adaptee (`has-a`). This is the preferred approach in Java because it promotes loose coupling and works across an entire hierarchy of adaptees.
- **Class Adapter (Inheritance)**: The adapter extends both the target interface and the adaptee (`is-a`), requiring multiple inheritance (unsupported for classes in Java).

#### 💻 Production-Ready Java Implementation

```java
// Target interface expected by our application
public interface ThirdPartyPaymentGateway {
    boolean pay(String customerEmail, double amountInUsd);
}

// Adaptee: Legacy third-party library with incompatible method signature
public class LegacyIndianPaymentProvider {
    public void makeInrPayment(String email, long amountInPaise) {
        System.out.println("Processed " + amountInPaise + " paise for " + email);
    }
}

// Object Adapter translating USD dollars to INR paise
public class PaymentProviderAdapter implements ThirdPartyPaymentGateway {
    private final LegacyIndianPaymentProvider legacyProvider;

    public PaymentProviderAdapter(LegacyIndianPaymentProvider legacyProvider) {
        this.legacyProvider = legacyProvider;
    }

    @Override
    public boolean pay(String customerEmail, double amountInUsd) {
        // Translation logic
        long paise = (long) (amountInUsd * 83.0 * 100);
        legacyProvider.makeInrPayment(customerEmail, paise);
        return true;
    }
}
```

---

### 4.3 Facade Pattern

#### 🎯 Intent & Motivation
Provide a **unified, simplified, high-level interface** to a complex set of interfaces in a subsystem. Reduces coupling between client callers and multiple internal services.
Production use cases:
- Order checkout orchestrators (Inventory → Payment → Warehouse → Shipping → Notification)
- Media converters (Audio decoding → Video decoding → Bitrate normalization → Multiplexing)

#### ⚙️ Deep-Dive Mechanics
- **Subsystem Decoupling**: Clients interact only with the Facade. If the internal subsystem services change, the client remains unaffected.
- **Non-Invasive**: The Facade does not hide the subsystem classes; advanced clients requiring fine-grained control can still access internal subsystems directly.

#### 💻 Production-Ready Java Implementation

```java
public class OrderCheckoutFacade {
    private final InventoryService inventoryService;
    private final PaymentService paymentService;
    private final ShippingService shippingService;
    private final NotificationService notificationService;

    public OrderCheckoutFacade(InventoryService inventory, PaymentService payment,
                               ShippingService shipping, NotificationService notification) {
        this.inventoryService = inventory;
        this.paymentService = payment;
        this.shippingService = shipping;
        this.notificationService = notification;
    }

    public boolean placeOrder(String userId, String productId, int qty, String paymentToken) {
        if (!inventoryService.isAvailable(productId, qty)) return false;
        inventoryService.reserve(productId, qty);

        boolean paid = paymentService.charge(userId, paymentToken);
        if (!paid) {
            inventoryService.release(productId, qty);
            return false;
        }

        String trackingId = shippingService.ship(userId, productId, qty);
        notificationService.notifyUser(userId, "Order dispatched: " + trackingId);
        return true;
    }
}
```

---

### 4.4 Proxy Pattern

#### 🎯 Intent & Motivation
Provide a **surrogate or placeholder** for another object to control access to it. The Proxy has the exact same interface as the real subject, allowing it to intercept calls transparently.

#### ⚙️ Deep-Dive Mechanics & Core Proxy Types
1. **Virtual Proxy (Lazy Loading)**: Defers the creation and initialization of an expensive resource until it is actually requested.
2. **Protection Proxy (Access Control)**: Checks client authentication and authorization (e.g. RBAC) before forwarding requests to the real subject.
3. **Caching Proxy (Memoization)**: Stores results of expensive operations or network requests to return cached results for identical inputs.
4. **Remote Proxy (RPC / gRPC)**: Encapsulates network marshaling and serialization, making remote services appear local.

#### 💻 Production-Ready Java Implementation

```java
import java.util.Map;
import java.util.concurrent.ConcurrentHashMap;

public interface VideoStreamingService {
    byte[] streamVideo(String videoId);
}

// Real Subject
public class RealVideoStreamingService implements VideoStreamingService {
    @Override
    public byte[] streamVideo(String videoId) {
        // Cold fetch simulation (e.g. S3 download or disk read)
        System.out.println("Fetching video from cloud storage: " + videoId);
        return new byte[]{1, 2, 3, 4};
    }
}

// Caching Proxy
public class CachingVideoProxy implements VideoStreamingService {
    private final VideoStreamingService realService;
    private final Map<String, byte[]> videoCache = new ConcurrentHashMap<>();

    public CachingVideoProxy(VideoStreamingService realService) {
        this.realService = realService;
    }

    @Override
    public byte[] streamVideo(String videoId) {
        return videoCache.computeIfAbsent(videoId, realService::streamVideo);
    }
}
```

---

# 5. Interview Heuristics & Decision Framework

When designing systems in machine coding and LLD interviews, use this comparative guide to select the right pattern:

### ⚖️ Pattern Comparison Matrix

| Problem Scenario | Recommended Pattern | Why Not Alternative? |
|---|---|---|
| Interchangeable algorithms at runtime | **Strategy** | Strategy is configured from the outside; State transitions internally based on context. |
| Object behavior changes based on internal state | **State** | State encapsulates FSM logic; avoids sprawling `if/else` checks across methods. |
| Stacking dynamic features / add-ons | **Decorator** | Decorator adds behavior without subclassing; Proxy controls access; Adapter fixes incompatible interfaces. |
| Adapting legacy / third-party SDK interface | **Adapter** | Adapter translates signatures; Facade simplifies multiple subsystem interfaces. |
| Simplifying complex multi-service checkout | **Facade** | Facade provides a single entry point; does not prevent direct access to subsystems. |
| Lazy loading or caching expensive objects | **Proxy** | Proxy preserves the exact subject interface; Decorator adds new functional responsibilities. |
| Enforcing invariant checks on complex creation | **Builder** | Builder enforces step-by-step construction and field validation before object creation. |
| Creating families of related UI / OS themes | **Abstract Factory** | Abstract Factory creates coordinated product families; Factory Method creates a single product hierarchy. |
| Multi-level undo/redo or command queuing | **Command** | Command encapsulates execution and rollback as an object; Strategy executes directly. |
| Request filtering or logging through stages | **Chain of Responsibility** | Decouples sender from receivers; supports dynamic ordering and fallthrough. |
