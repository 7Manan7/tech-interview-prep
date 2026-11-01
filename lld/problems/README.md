# 💻 Classic Machine Coding Problems (LLD)

In machine coding rounds (popular at companies like Uber, Flipkart, Swiggy, PhonePe, Razorpay, Google, Amazon), you are given a real-world problem and expected to deliver clean, object-oriented, extensible, and working code within 90 minutes.

---

## 📋 High-Frequency Problem Index

| # | Problem | Core Design Patterns & Concepts | Key Concurrency / Extensibility Focus |
|---|---|---|---|
| 1 | **[Parking Lot](#1-parking-lot)** | Strategy, Factory, Singleton | Multi-floor slot allocation, dynamic fee calculation, vehicle types |
| 2 | **[Tic-Tac-Toe](#2-tic-tac-toe)** | State, Strategy | $N \times N$ board scaling, pluggable winning condition strategies |
| 3 | **[Rate Limiter](#3-rate-limiter)** | Strategy, Token Bucket, Sliding Window | Thread safety, concurrency limits, distributed redis support |
| 4 | **[Splitwise (Expense Sharing)](#4-splitwise)** | Strategy, Observer, Factory | Equal, Exact, Percentage splits, debt simplification graph algorithm |
| 5 | **[Elevator System](#5-elevator-system)** | State, Strategy (SCAN / LOOK algorithm) | Multi-elevator dispatch strategy, internal/external requests |
| 6 | **[Snake and Ladder](#6-snake-and-ladder)** | Object modeling, Queue | Board setup, dynamic players, dice roll strategy |
| 7 | **[BookMyShow / Movie Ticket Booking](#7-bookmyshow)** | Singleton, State, Pessimistic / Optimistic Locking | Concurrent seat booking, temporary seat lock timeout (e.g. 10 mins) |
| 8 | **[In-Memory Cache (LRU / LFU)](#8-in-memory-cache)** | Doubly Linked List + HashMap | $O(1)$ operations, pluggable eviction strategies, thread safety |
| 9 | **[Notification Service](#9-notification-service)** | Observer, Factory, Strategy | Multi-channel (SMS, Email, Push), priority queues, rate limits & retries |
| 10 | **[Chess / Board Game](#10-chess)** | Command, Strategy, Factory | Piece moves, check/checkmate validation, move history & undo |

---

## 🔍 Detailed Problem Breakdowns

### 1. Parking Lot
- **Key Entities:** `Vehicle` (Car, Bike, Truck), `ParkingSlot` (Compact, Large, Motorcycle), `ParkingFloor`, `Ticket`, `Gate` (EntryGate, ExitGate), `ParkingLot`.
- **Patterns:**
  - `Strategy`: For slot allocation (First Available, Nearest to Entrance) and pricing strategy (Hourly, Weekend, Flat).
  - `Factory`: For creating appropriate vehicle/slot types.
- **Key Concurrency Point:** Synchronizing slot assignment when multiple entry gates attempt to allocate the same parking spot simultaneously.

### 2. Rate Limiter
- **Algorithms to Implement:**
  - **Token Bucket:** Refills tokens at a constant rate; bursts allowed up to bucket capacity.
  - **Leaky Bucket:** Constant processing rate; drops requests when buffer overflows.
  - **Sliding Window Counter / Log:** Tracks timestamps to prevent burst at window boundaries.
- **Key Concurrency Point:** Atomic updates using `AtomicLong` or `ReentrantLock` per client/API key.

### 3. Splitwise
- **Key Entities:** `User`, `Expense`, `Split` (`EqualSplit`, `ExactSplit`, `PercentSplit`), `Group`, `BalanceSheet`.
- **Patterns:**
  - `Strategy`: For validating and computing splits (`EqualExpenseStrategy`, `PercentExpenseStrategy`).
- **Bonus Feature:** Debt simplification algorithm using greedy / min-cash-flow algorithm (graph / priority queues).

### 4. BookMyShow
- **Key Entities:** `City`, `Cinema`, `Screen`, `Show`, `Movie`, `Seat`, `Booking`, `Payment`.
- **Critical Challenge:** Two users selecting the exact same seat at the same second.
- **Solution:** Temporary seat reservation with TTL:
  ```java
  public enum SeatStatus {
      AVAILABLE,
      LOCKED,     // Temporary lock with expiration timestamp
      BOOKED
  }
  ```

---

## 📝 Template Driver Class Structure

When submitting your machine coding solution, provide an interactive or demonstration driver:

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

