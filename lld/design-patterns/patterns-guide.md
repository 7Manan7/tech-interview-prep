# 🎨 Gang of Four (GoF) Design Patterns — Java Implementation Guide

A comprehensive, production-grade implementation guide for the most frequently tested Design Patterns in Low-Level Design and Machine Coding interviews.

---

## 📑 Table of Contents

1. [Creational Patterns](#1-creational-patterns)
   - [Singleton Pattern (DCL, Bill Pugh, Enum)](#11-singleton-pattern)
   - [Factory Method Pattern](#12-factory-method-pattern)
   - [Abstract Factory Pattern](#13-abstract-factory-pattern)
   - [Builder Pattern](#14-builder-pattern)
2. [Behavioral Patterns (Tier 1)](#2-behavioral-patterns-tier-1)
   - [Strategy Pattern](#21-strategy-pattern)
   - [Observer Pattern](#22-observer-pattern)
   - [State Pattern](#23-state-pattern)
3. [Behavioral Patterns (Tier 2)](#3-behavioral-patterns-tier-2)
   - [Chain of Responsibility Pattern](#31-chain-of-responsibility-pattern)
   - [Command Pattern](#32-command-pattern)
4. [Structural Patterns](#4-structural-patterns)
   - [Decorator Pattern](#41-decorator-pattern)
   - [Adapter Pattern](#42-adapter-pattern)
   - [Facade Pattern](#43-facade-pattern)
   - [Proxy Pattern](#44-proxy-pattern)
5. [Interview Heuristics & Trade-offs](#5-interview-heuristics--trade-offs)

---

# 1. Creational Patterns

### 1.1 Singleton Pattern

#### Approach A: Double-Checked Locking (DCL) with `volatile`
```java
public class DatabaseConnectionPool {
    private static volatile DatabaseConnectionPool instance;

    private DatabaseConnectionPool() {
        if (instance != null) {
            throw new IllegalStateException("Instance already exists!");
        }
    }

    public static DatabaseConnectionPool getInstance() {
        if (instance == null) {
            synchronized (DatabaseConnectionPool.class) {
                if (instance == null) {
                    instance = new DatabaseConnectionPool();
                }
            }
        }
        return instance;
    }
}
```

#### Approach B: Bill Pugh Singleton Holder
```java
public class CacheRegistry {
    private CacheRegistry() {}

    private static class InstanceHolder {
        private static final CacheRegistry INSTANCE = new CacheRegistry();
    }

    public static CacheRegistry getInstance() {
        return InstanceHolder.INSTANCE;
    }
}
```

#### Approach C: Enum Singleton (Effective Java Recommendation)
```java
public enum ConfigurationService {
    INSTANCE;

    private final Map<String, String> configs = new ConcurrentHashMap<>();

    public void setConfig(String key, String value) { configs.put(key, value); }
    public String getConfig(String key) { return configs.get(key); }
}
```

---

### 1.2 Factory Method Pattern

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
    @Override public void drive() { System.out.println("Driving car"); }
    @Override public double getCostPerHour() { return 25.0; }
}

public class Truck implements Vehicle {
    @Override public void drive() { System.out.println("Driving truck"); }
    @Override public double getCostPerHour() { return 60.0; }
}

public class VehicleFactory {
    public static Vehicle createVehicle(String type) {
        if (type == null) throw new IllegalArgumentException("Type cannot be null");
        return switch (type.toUpperCase()) {
            case "BIKE" -> new Bike();
            case "CAR" -> new Car();
            case "TRUCK" -> new Truck();
            default -> throw new IllegalArgumentException("Unsupported vehicle type: " + type);
        };
    }
}
```

---

### 1.3 Abstract Factory Pattern

```java
public interface Button { void render(); }
public interface Checkbox { void render(); }

public class LightButton implements Button {
    @Override public void render() { System.out.println("Render Light Button"); }
}
public class LightCheckbox implements Checkbox {
    @Override public void render() { System.out.println("Render Light Checkbox"); }
}

public class DarkButton implements Button {
    @Override public void render() { System.out.println("Render Dark Button"); }
}
public class DarkCheckbox implements Checkbox {
    @Override public void render() { System.out.println("Render Dark Checkbox"); }
}

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

---

### 1.4 Builder Pattern

```java
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

    public static class Builder {
        private final String userId;
        private final String resourceId;
        private Instant startTime;
        private Instant endTime;
        private String promoCode;
        private boolean insuranceOptIn;

        public Builder(String userId, String resourceId) {
            this.userId = Objects.requireNonNull(userId, "userId required");
            this.resourceId = Objects.requireNonNull(resourceId, "resourceId required");
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
            if (startTime == null || endTime == null) {
                throw new IllegalStateException("Start and End time must be set");
            }
            if (!endTime.isAfter(startTime)) {
                throw new IllegalArgumentException("End time must be strictly after Start time");
            }
            return new ReservationRequest(this);
        }
    }
}
```

---

# 2. Behavioral Patterns (Tier 1)

### 2.1 Strategy Pattern

```java
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

```java
public record OrderEvent(String orderId, String customerId, BigDecimal totalAmount) {}

public interface OrderListener {
    void handleOrderPlaced(OrderEvent event);
}

public class OrderEventPublisher {
    private final List<OrderListener> listeners = new CopyOnWriteArrayList<>();

    public void register(OrderListener listener) {
        listeners.add(Objects.requireNonNull(listener));
    }

    public void unregister(OrderListener listener) {
        listeners.remove(listener);
    }

    public void publish(OrderEvent event) {
        for (OrderListener listener : listeners) {
            listener.handleOrderPlaced(event);
        }
    }
}
```

---

### 2.3 State Pattern

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
    @Override public void dispense(VendingMachine context) { System.out.println("Cannot dispense without coins."); }
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
        context.resetBalance();
        context.setState(new NoCoinState());
    }
}

public class DispensingState implements VendingMachineState {
    @Override public void insertCoin(VendingMachine context, int amount) { System.out.println("Please wait, dispensing."); }
    @Override public void selectItem(VendingMachine context, String code) { System.out.println("Already dispensing."); }
    @Override
    public void dispense(VendingMachine context) {
        System.out.println("Item dispensed!");
        context.resetBalance();
        context.setState(new NoCoinState());
    }
    @Override public void cancelAndRefund(VendingMachine context) { System.out.println("Cannot cancel while dispensing."); }
}
```

---

# 3. Behavioral Patterns (Tier 2)

### 3.1 Chain of Responsibility Pattern

```java
public abstract class Logger {
    public static final int INFO = 1;
    public static final int DEBUG = 2;
    public static final int ERROR = 3;

    protected int level;
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

```java
public interface Command {
    void execute();
    void undo();
}

public class Document {
    private final StringBuilder content = new StringBuilder();

    public void write(String text) { content.append(text); }
    public void erase(int length) {
        content.delete(content.length() - length, content.length());
    }
    public String getContent() { return content.toString(); }
}

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

public class CommandInvoker {
    private final Deque<Command> undoStack = new ArrayDeque<>();
    private final Deque<Command> redoStack = new ArrayDeque<>();

    public void executeCommand(Command command) {
        command.execute();
        undoStack.push(command);
        redoStack.clear();
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

### 4.1 Decorator Pattern

```java
public interface Beverage {
    String getDescription();
    double getCost();
}

public class Espresso implements Beverage {
    @Override public String getDescription() { return "Espresso"; }
    @Override public double getCost() { return 2.0; }
}

public abstract class AddOnDecorator implements Beverage {
    protected final Beverage beverage;

    public AddOnDecorator(Beverage beverage) {
        this.beverage = Objects.requireNonNull(beverage);
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

```java
public interface ThirdPartyPaymentGateway {
    boolean pay(String customerEmail, double amountInUsd);
}

public class LegacyIndianPaymentProvider {
    public void makeInrPayment(String email, long amountInPaise) {
        System.out.println("Processed " + amountInPaise + " paise for " + email);
    }
}

public class PaymentProviderAdapter implements ThirdPartyPaymentGateway {
    private final LegacyIndianPaymentProvider legacyProvider;

    public PaymentProviderAdapter(LegacyIndianPaymentProvider legacyProvider) {
        this.legacyProvider = legacyProvider;
    }

    @Override
    public boolean pay(String customerEmail, double amountInUsd) {
        long paise = (long) (amountInUsd * 83.0 * 100);
        legacyProvider.makeInrPayment(customerEmail, paise);
        return true;
    }
}
```

---

### 4.3 Facade Pattern

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

```java
public interface VideoStreamingService {
    byte[] streamVideo(String videoId);
}

public class RealVideoStreamingService implements VideoStreamingService {
    @Override
    public byte[] streamVideo(String videoId) {
        return new byte[]{1, 2, 3}; // Cold network fetch
    }
}

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

# 5. Interview Heuristics & Trade-offs

- **Strategy vs. State**: Strategy is client-selected to execute an algorithmic variant; State transitions internally and autonomously.
- **Decorator vs. Proxy**: Decorator dynamically augments responsibilities; Proxy manages lifecycle, caching, or authorization without altering behavior.
- **Factory Method vs. Abstract Factory**: Factory Method produces a single product; Abstract Factory produces families of related products.

