# 💻 Classic Machine Coding Problems (LLD)

In machine coding rounds (popular at companies like Uber, Flipkart, Swiggy, PhonePe, Razorpay, Google, Amazon), you are given a real-world problem and expected to deliver clean, object-oriented, extensible, and working code within 60–90 minutes.

> 📖 **Case Studies Deep-Dive**: For detailed entities, class designs, concurrency controls, and code implementations, see **[Case Studies Deep-Dive](./case-studies.md)** or **[LLD Master Guide Section 7](../lld-guide.md#7-must-practice-lld-case-studies-by-category)**.

---

## 📋 Categorized Problem Index

### 1. Booking & Slot Allocation
| # | Problem | Core Design Patterns | Key Concurrency / Extensibility Focus | Detailed Solution |
|---|---|---|---|---|
| 1 | **Parking Lot** | Strategy, Factory, Singleton | Multi-floor slot allocation, dynamic fee calculation, vehicle types | [View Solution](./case-studies.md#11-parking-lot-system) |
| 2 | **Movie Ticket Booking (BookMyShow)** | State, Strategy, Singleton | Concurrent seat booking, temporary seat lock timeout (TTL) | [View Solution](./case-studies.md#12-movie-ticket-booking-bookmyshow) |
| 3 | **Amazon Locker Management** | Strategy, Observer | Compartment dimension matching (S/M/L/XL), OTP verification | [View Solution](./case-studies.md#13-amazon-locker-management-system) |
| 4 | **Car Rental System (Zoomcar)** | Decorator, State | Vehicle reservation, dynamic insurance add-ons, maintenance states | [View Solution](./case-studies.md#14-car-rental-system) |

### 2. State & Workflow Machines
| # | Problem | Core Design Patterns | Key Concurrency / Extensibility Focus | Detailed Solution |
|---|---|---|---|---|
| 5 | **Vending Machine** | State | Idle, HasCoin, Dispensing, SoldOut states, change refund | [View Solution](./case-studies.md#21-vending-machine) |
| 6 | **Elevator Control System** | State, Strategy (SCAN / LOOK) | Multi-elevator dispatch strategy, internal/external request queues | [View Solution](./case-studies.md#22-elevator-control-system) |
| 7 | **ATM Cash Dispenser** | Chain of Responsibility, State | Note dispensers ($100 $\to$ $50 $\to$ $20), PIN authentication | [View Solution](./case-studies.md#23-atm-cash-dispenser) |
| 8 | **Order Management System** | State / Rich Enum, Observer | Order lifecycle (Created $\to$ Paid $\to$ Packed $\to$ Shipped) | [View Solution](./case-studies.md#24-order-management-system) |

### 3. Matching, Ledgers & Marketplaces
| # | Problem | Core Design Patterns | Key Concurrency / Extensibility Focus | Detailed Solution |
|---|---|---|---|---|
| 9 | **Splitwise (Expense Sharing)** | Strategy, Observer | Equal, Exact, Percentage splits, debt simplification graph algorithm | [View Solution](./case-studies.md#31-splitwise) |
| 10 | **Ride-Sharing (Uber / Lyft)** | Strategy, Decorator, Observer | Driver matching algorithms, surge pricing decorators, trip states | [View Solution](./case-studies.md#32-ride-sharing-service-uber--lyft) |
| 11 | **Food Delivery (Swiggy / DoorDash)** | Facade, Observer | Restaurant menu, cart checkout, delivery assignment | [View Solution](./case-studies.md#33-food-delivery-system) |
| 12 | **Inventory & Shopping Cart** | Decorator, Strategy | Cart coupon stacking, inventory reservation during checkout | [View Solution](./case-studies.md#34-inventory--shopping-cart-system) |

### 4. Board & Turn-Based Games
| # | Problem | Core Design Patterns | Key Concurrency / Extensibility Focus | Detailed Solution |
|---|---|---|---|---|
| 13 | **Snake and Ladder** | Strategy, Queue | Turn-based player loop, extensible board with snakes/ladders | [View Solution](./case-studies.md#41-snake-and-ladder) |
| 14 | **Chess Game** | Command, Strategy | Move validation per piece, check/checkmate detection, move history & undo | [View Solution](./case-studies.md#42-chess-game) |
| 15 | **Tic-Tac-Toe** | Strategy, State | $N \times N$ board scaling, $O(1)$ win evaluation per move | [View Solution](./case-studies.md#43-tic-tac-toe) |

### 5. Core Backend Infrastructure
| # | Problem | Core Design Patterns | Key Concurrency / Extensibility Focus | Detailed Solution |
|---|---|---|---|---|
| 16 | **Thread-Safe LRU / LFU Cache** | Doubly Linked List + HashMap | $O(1)$ operations, ReadWriteLock, TTL lazy expiry | [View Solution](./case-studies.md#51-thread-safe-lru--lfu-cache-with-ttl) |
| 17 | **Rate Limiter** | Strategy, Token Bucket, Sliding Window | Thread safety, atomic refill rate, burst handling | [View Solution](./case-studies.md#52-rate-limiter) |
| 18 | **In-Memory Pub-Sub Broker** | Observer, Queue | Topic-based broadcast, consumer groups, offset tracking | [View Solution](./case-studies.md#53-in-memory-pub-sub-broker) |
| 19 | **Logger Framework** | Chain of Responsibility, Strategy | Log levels (DEBUG, INFO, ERROR), asynchronous buffer worker | [View Solution](./case-studies.md#54-logger-framework) |
| 20 | **Delayed Job Scheduler** | PriorityBlockingQueue, Command | Time-based priority scheduling, worker thread pool execution | [View Solution](./case-studies.md#55-delayed-job-scheduler) |

---

## 📝 Template Driver Class Structure

When submitting your machine coding solution, provide an interactive demonstration driver:

```java
public class Driver {
    public static void main(String[] args) {
        // 1. Initialize System & Repositories
        // 2. Setup master data (floors, slots, users, etc.)
        // 3. Execute concurrent/sequential operations
        // 4. Print clean assertions / verification logs
    }
}
```
