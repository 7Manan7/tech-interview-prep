# 💻 Classic Machine Coding Case Studies — Deep Dive

Detailed functional scopes, class structures, architectural design patterns, concurrency controls, and code implementations for high-frequency machine coding interview problems.

---

## 📑 Table of Contents

1. [Booking & Slot Allocation](#1-booking--slot-allocation)
   - [Parking Lot System](#11-parking-lot-system)
   - [Movie Ticket Booking (BookMyShow)](#12-movie-ticket-booking-bookmyshow)
   - [Amazon Locker Management System](#13-amazon-locker-management-system)
   - [Car Rental System (Zoomcar / Hertz)](#14-car-rental-system)
2. [State & Workflow Machines](#2-state--workflow-machines)
   - [Vending Machine](#21-vending-machine)
   - [Elevator Control System](#22-elevator-control-system)
   - [ATM Cash Dispenser](#23-atm-cash-dispenser)
   - [Order Management System (OMS)](#24-order-management-system)
3. [Matching, Ledgers & Marketplaces](#3-matching-ledgers--marketplaces)
   - [Splitwise (Expense Sharing with Debt Simplification)](#31-splitwise)
   - [Ride-Sharing Service (Uber / Lyft)](#32-ride-sharing-service-uber--lyft)
   - [Food Delivery System (Swiggy / DoorDash)](#33-food-delivery-system)
   - [Inventory & Shopping Cart System](#34-inventory--shopping-cart-system)
4. [Board & Turn-Based Games](#4-board--turn-based-games)
   - [Snake and Ladder](#41-snake-and-ladder)
   - [Chess Game](#42-chess-game)
   - [Tic-Tac-Toe (N x N)](#43-tic-tac-toe)
5. [Core Backend Infrastructure](#5-core-backend-infrastructure)
   - [Thread-Safe LRU / LFU Cache with TTL](#51-thread-safe-lru--lfu-cache-with-ttl)
   - [Rate Limiter (Token Bucket & Sliding Window)](#52-rate-limiter)
   - [In-Memory Pub-Sub Broker](#53-in-memory-pub-sub-broker)
   - [Logger Framework](#54-logger-framework)
   - [Delayed Job Scheduler](#55-delayed-job-scheduler)

---

# 1. Booking & Slot Allocation

### 1.1 Parking Lot System
- **Entities:** `ParkingLot`, `ParkingFloor`, `ParkingSpot`, `Vehicle`, `Ticket`, `Gate`.
- **Patterns:** `Strategy` (slot allocation & pricing), `Factory` (vehicle/spot creation).
- **Concurrency:** Thread-safe slot acquisition using CAS on `AtomicBoolean`:
```java
public class ParkingSpot {
    private final String spotId;
    private final VehicleType supportedType;
    private final AtomicBoolean occupied = new AtomicBoolean(false);
    private volatile Vehicle currentVehicle;

    public boolean tryOccupy(Vehicle vehicle) {
        if (vehicle.getType() == supportedType && occupied.compareAndSet(false, true)) {
            this.currentVehicle = vehicle;
            return true;
        }
        return false;
    }
}
```

---

### 1.2 Movie Ticket Booking (BookMyShow)
- **Entities:** `Cinema`, `Screen`, `Show`, `Movie`, `Seat`, `ShowSeat`, `Booking`.
- **Patterns:** `State` (`AVAILABLE`, `LOCKED`, `BOOKED`), `Strategy` (dynamic pricing).
- **Concurrency:** Keyed seat locking via `ConcurrentHashMap<String, LockMetadata>` with TTL auto-expiry:
```java
public class SeatLockService {
    private final ConcurrentHashMap<String, LockMetadata> lockMap = new ConcurrentHashMap<>();

    public synchronized boolean acquireSeats(String showId, List<String> seatIds, String userId, Duration ttl) {
        Instant now = Instant.now();
        for (String seatId : seatIds) {
            String key = showId + ":" + seatId;
            LockMetadata meta = lockMap.get(key);
            if (meta != null && meta.expiresAt().isAfter(now)) {
                return false;
            }
        }
        for (String seatId : seatIds) {
            String key = showId + ":" + seatId;
            lockMap.put(key, new LockMetadata(userId, now.plus(ttl)));
        }
        return true;
    }
}
```

---

### 1.3 Amazon Locker Management System
- **Entities:** `LockerHub`, `LockerCompartment`, `LockerSize`, `Package`, `OtpCode`.
- **Patterns:** `Strategy` (compartment best-fit matching), `Observer` (expiry notification).
```java
public enum LockerSize {
    SMALL(1), MEDIUM(2), LARGE(3), XLARGE(4);
    private final int rank;
    LockerSize(int rank) { this.rank = rank; }
    public boolean canAccommodate(LockerSize packageSize) {
        return this.rank >= packageSize.rank;
    }
}
```

---

### 1.4 Car Rental System
- **Entities:** `Vehicle`, `VehicleCategory`, `BranchLocation`, `Reservation`, `RentalContract`.
- **Patterns:** `Decorator` (insurance, roadside assistance, GPS add-ons), `State` (vehicle status lifecycle).

---

# 2. State & Workflow Machines

### 2.1 Vending Machine
- **Entities:** `VendingMachine`, `Item`, `ItemShelf`, `Coin`, `VendingState`.
- **Patterns:** `State` (`IdleState`, `HasCoinState`, `DispensingState`, `SoldOutState`).

---

### 2.2 Elevator Control System
- **Entities:** `ElevatorController`, `ElevatorCar`, `Direction`, `Door`, `FloorRequest`.
- **Algorithm:** SCAN / LOOK algorithm using two priority queues:
  - `upMinHeap` for requests above current floor moving UP.
  - `downMaxHeap` for requests below current floor moving DOWN.

---

### 2.3 ATM Cash Dispenser
- **Entities:** `AtmMachine`, `CardReader`, `CashDispenserChain`, `Account`.
- **Patterns:** `Chain of Responsibility` for currency note dispensing ($100 $\to$ $50 $\to$ $20 $\to$ $10).

---

### 2.4 Order Management System
- **Entities:** `Order`, `OrderItem`, `Payment`, `Shipment`, `OrderStatus`.
- **Patterns:** Rich Enum with state validation + Observer for downstream lifecycle listeners.

---

# 3. Matching, Ledgers & Marketplaces

### 3.1 Splitwise
- **Entities:** `User`, `Expense`, `Split` (`EqualSplit`, `ExactSplit`, `PercentSplit`), `Group`.
- **Debt Simplification Algorithm:**
```java
public class DebtSimplifier {
    public record Transaction(String fromUser, String toUser, double amount) {}

    public static List<Transaction> simplifyDebts(Map<String, Double> netBalances) {
        PriorityQueue<Map.Entry<String, Double>> debtors =
            new PriorityQueue<>(Comparator.comparingDouble(Map.Entry::getValue));
        PriorityQueue<Map.Entry<String, Double>> creditors =
            new PriorityQueue<>((a, b) -> Double.compare(b.getValue(), a.getValue()));

        for (Map.Entry<String, Double> entry : netBalances.entrySet()) {
            if (entry.getValue() < -0.01) debtors.add(entry);
            else if (entry.getValue() > 0.01) creditors.add(entry);
        }

        List<Transaction> transactions = new ArrayList<>();
        while (!debtors.isEmpty() && !creditors.isEmpty()) {
            var debtor = debtors.poll();
            var creditor = creditors.poll();

            double debit = -debtor.getValue();
            double credit = creditor.getValue();
            double settledAmount = Math.min(debit, credit);

            transactions.add(new Transaction(debtor.getKey(), creditor.getKey(), settledAmount));

            if (debit > settledAmount) {
                debtor.setValue(-(debit - settledAmount));
                debtors.add(debtor);
            }
            if (credit > settledAmount) {
                creditor.setValue(credit - settledAmount);
                creditors.add(creditor);
            }
        }
        return transactions;
    }
}
```

---

### 3.2 Ride-Sharing Service (Uber / Lyft)
- **Entities:** `Rider`, `Driver`, `Trip`, `Location`, `PricingStrategy`.
- **Patterns:** `Strategy` (driver matching & surge pricing), `Decorator` (toll surcharges).

---

### 3.3 Food Delivery System
- **Entities:** `Restaurant`, `MenuItem`, `Cart`, `Order`, `DeliveryPartner`.
- **Patterns:** `Facade` (`CheckoutFacade`), `Observer` (live courier tracking).

---

### 3.4 Inventory & Shopping Cart System
- **Entities:** `Product`, `InventoryItem`, `Cart`, `Coupon`.
- **Patterns:** `Decorator` (stacked coupons), `Strategy` (discount calculation).

---

# 4. Board & Turn-Based Games

### 4.1 Snake and Ladder
- **Entities:** `Board`, `Cell`, `Jump`, `Player`, `Dice`, `Game`.
- **Patterns:** `Strategy` (dice rolling), Queue-based turn management.

---

### 4.2 Chess Game
- **Entities:** `Board`, `Spot`, `Piece`, `Move`, `Player`.
- **Patterns:** `Command` (move history & undo/redo), `Strategy` (piece move validators).

---

### 4.3 Tic-Tac-Toe
- **Entities:** `Board`, `Player`, `PieceType`.
- **$O(1)$ Win Check:**
```java
public class TicTacToeBoard {
    private final int size;
    private final int[] rowCounts;
    private final int[] colCounts;
    private int diagCount = 0;
    private int antiDiagCount = 0;

    public TicTacToeBoard(int size) {
        this.size = size;
        this.rowCounts = new int[size];
        this.colCounts = new int[size];
    }

    public boolean makeMove(int row, int col, int playerVal) {
        rowCounts[row] += playerVal;
        colCounts[col] += playerVal;
        if (row == col) diagCount += playerVal;
        if (row + col == size - 1) antiDiagCount += playerVal;

        int target = playerVal * size;
        return rowCounts[row] == target
            || colCounts[col] == target
            || diagCount == target
            || antiDiagCount == target;
    }
}
```

---

# 5. Core Backend Infrastructure

### 5.1 Thread-Safe LRU / LFU Cache with TTL
- **Implementation:** HashMap + Doubly Linked List with `ReentrantReadWriteLock`.

---

### 5.2 Rate Limiter
- **Algorithms:** Token Bucket (using `ReentrantLock` and token refill rate) and Sliding Window Counter.

---

### 5.3 In-Memory Pub-Sub Broker
- **Core Strategy:** Concurrent message queues per topic with atomic offset tracking per consumer group.

---

### 5.4 Logger Framework
- **Core Strategy:** Chain of Responsibility log levels with asynchronous non-blocking worker queue.

---

### 5.5 Delayed Job Scheduler
- **Core Strategy:** Backed by `PriorityBlockingQueue` ordered by `scheduledTimestamp` and worker thread pool.

