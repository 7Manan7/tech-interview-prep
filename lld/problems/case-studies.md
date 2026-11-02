# 💻 Classic Machine Coding Case Studies — Deep Dive

A master-level repository of functional scopes, class structures, architectural design patterns, concurrency controls, and production-ready Java implementations for all 20 high-frequency machine coding interview problems.

---

## 📑 Table of Contents

1. [Booking & Slot Allocation](#1-booking--slot-allocation)
   - [1.1 Parking Lot System](#11-parking-lot-system)
   - [1.2 Movie Ticket Booking (BookMyShow)](#12-movie-ticket-booking-bookmyshow)
   - [1.3 Amazon Locker Management System](#13-amazon-locker-management-system)
   - [1.4 Car Rental System (Zoomcar / Hertz)](#14-car-rental-system)
2. [State & Workflow Machines](#2-state--workflow-machines)
   - [2.1 Vending Machine](#21-vending-machine)
   - [2.2 Elevator Control System](#22-elevator-control-system)
   - [2.3 ATM Cash Dispenser](#23-atm-cash-dispenser)
   - [2.4 Order Management System (OMS)](#24-order-management-system)
3. [Matching, Ledgers & Marketplaces](#3-matching-ledgers--marketplaces)
   - [3.1 Splitwise (Expense Sharing with Debt Simplification)](#31-splitwise)
   - [3.2 Ride-Sharing Service (Uber / Lyft)](#32-ride-sharing-service-uber--lyft)
   - [3.3 Food Delivery System (Swiggy / DoorDash)](#33-food-delivery-system)
   - [3.4 Inventory & Shopping Cart System](#34-inventory--shopping-cart-system)
4. [Board & Turn-Based Games](#4-board--turn-based-games)
   - [4.1 Snake and Ladder](#41-snake-and-ladder)
   - [4.2 Chess Game](#42-chess-game)
   - [4.3 Tic-Tac-Toe (N x N Scalable)](#43-tic-tac-toe)
5. [Core Backend Infrastructure](#5-core-backend-infrastructure)
   - [5.1 Thread-Safe LRU / LFU Cache with TTL](#51-thread-safe-lru--lfu-cache-with-ttl)
   - [5.2 Rate Limiter (Token Bucket & Sliding Window)](#52-rate-limiter)
   - [5.3 In-Memory Pub-Sub Broker](#53-in-memory-pub-sub-broker)
   - [5.4 Logger Framework](#54-logger-framework)
   - [5.5 Delayed Job Scheduler](#55-delayed-job-scheduler)

---

# 1. Booking & Slot Allocation

Focuses on: **Fine-grained resource locking**, **temporary reservations with TTL auto-expiration**, **dynamic pricing strategies**, and **inventory allocation algorithms**.

---

### 1.1 Parking Lot System

#### Problem Overview
Design an automated parking lot management system supporting:
- Multi-floor parking with diverse spot types (`MOTORCYCLE`, `COMPACT`, `LARGE`).
- Concurrent vehicle entry and exit at multiple physical gates without race conditions.
- Pluggable spot allocation algorithms (e.g., nearest to gate, first available).
- Dynamic pricing calculation based on vehicle type and duration.

#### Core Domain Model & Design Patterns
- **Patterns**: `Strategy` (Spot Allocation & Fee Calculation), `Factory` (Vehicle & Spot creation), `Singleton` (ParkingLot catalog).
- **Concurrency**: Lock-free atomic spot occupancy using `AtomicBoolean.compareAndSet(false, true)` to guarantee zero double-allocations under high concurrency.

#### Production-Ready Java Implementation

```java
import java.time.Duration;
import java.time.Instant;
import java.util.*;
import java.util.concurrent.*;
import java.util.concurrent.atomic.AtomicBoolean;

public class ParkingLotDemo {

    public enum VehicleType { MOTORCYCLE, CAR, TRUCK }

    public record Vehicle(String licensePlate, VehicleType type) {}

    public static class ParkingSpot {
        private final String spotId;
        private final int floorNumber;
        private final VehicleType supportedType;
        private final AtomicBoolean occupied = new AtomicBoolean(false);
        private volatile Vehicle currentVehicle;

        public ParkingSpot(String spotId, int floorNumber, VehicleType supportedType) {
            this.spotId = spotId;
            this.floorNumber = floorNumber;
            this.supportedType = supportedType;
        }

        public boolean tryOccupy(Vehicle vehicle) {
            if (vehicle.type() != this.supportedType) return false;
            if (occupied.compareAndSet(false, true)) {
                this.currentVehicle = vehicle;
                return true;
            }
            return false;
        }

        public void vacate() {
            this.currentVehicle = null;
            this.occupied.set(false);
        }

        public boolean isAvailable() { return !occupied.get(); }
        public String getSpotId() { return spotId; }
        public VehicleType getSupportedType() { return supportedType; }
        public int getFloorNumber() { return floorNumber; }
    }

    public record ParkingTicket(String ticketId, String spotId, String licensePlate, Instant entryTime) {}

    public interface ParkingStrategy {
        Optional<ParkingSpot> findSpot(List<ParkingSpot> spots, Vehicle vehicle);
    }

    public static class NearestSpotStrategy implements ParkingStrategy {
        @Override
        public Optional<ParkingSpot> findSpot(List<ParkingSpot> spots, Vehicle vehicle) {
            return spots.stream()
                .filter(s -> s.getSupportedType() == vehicle.type() && s.isAvailable())
                .sorted(Comparator.comparingInt(ParkingSpot::getFloorNumber))
                .findFirst();
        }
    }

    public interface FeeStrategy {
        double calculateFee(VehicleType type, Duration duration);
    }

    public static class HourlyFeeStrategy implements FeeStrategy {
        private static final Map<VehicleType, Double> RATES = Map.of(
            VehicleType.MOTORCYCLE, 10.0,
            VehicleType.CAR, 25.0,
            VehicleType.TRUCK, 50.0
        );

        @Override
        public double calculateFee(VehicleType type, Duration duration) {
            long hours = Math.max(1, (long) Math.ceil(duration.toMinutes() / 60.0));
            return hours * RATES.getOrDefault(type, 20.0);
        }
    }

    public static class ParkingLotService {
        private final List<ParkingSpot> spots = new CopyOnWriteArrayList<>();
        private final Map<String, ParkingTicket> activeTickets = new ConcurrentHashMap<>();
        private final Map<String, ParkingSpot> spotIndex = new ConcurrentHashMap<>();
        private final ParkingStrategy parkingStrategy;
        private final FeeStrategy feeStrategy;

        public ParkingLotService(ParkingStrategy parkingStrategy, FeeStrategy feeStrategy) {
            this.parkingStrategy = parkingStrategy;
            this.feeStrategy = feeStrategy;
        }

        public void addSpot(ParkingSpot spot) {
            spots.add(spot);
            spotIndex.put(spot.getSpotId(), spot);
        }

        public ParkingTicket parkVehicle(Vehicle vehicle) {
            Optional<ParkingSpot> spotOpt = parkingStrategy.findSpot(spots, vehicle);
            if (spotOpt.isEmpty() || !spotOpt.get().tryOccupy(vehicle)) {
                throw new IllegalStateException("No available spot for vehicle: " + vehicle.licensePlate());
            }

            ParkingSpot spot = spotOpt.get();
            String ticketId = "TKT-" + UUID.randomUUID().toString().substring(0, 8);
            ParkingTicket ticket = new ParkingTicket(ticketId, spot.getSpotId(), vehicle.licensePlate(), Instant.now());
            activeTickets.put(ticketId, ticket);
            return ticket;
        }

        public double exitVehicle(String ticketId, VehicleType type) {
            ParkingTicket ticket = activeTickets.remove(ticketId);
            if (ticket == null) throw new IllegalArgumentException("Invalid ticket ID: " + ticketId);

            ParkingSpot spot = spotIndex.get(ticket.spotId());
            if (spot != null) spot.vacate();

            Duration duration = Duration.between(ticket.entryTime(), Instant.now());
            return feeStrategy.calculateFee(type, duration);
        }
    }
}
```

---

### 1.2 Movie Ticket Booking (BookMyShow)

#### Problem Overview
Design a distributed movie ticket booking system handling:
- High concurrency during blockbuster opening sales where thousands contest the same seat.
- **Temporary Seat Locking (TTL)**: When user initiates checkout, reserve seats for 5–10 minutes.
- Automatic release on expiration without deadlocks or double-allocation.
- Atomic multi-seat reservation (all requested seats or none).

#### Core Domain Model & Design Patterns
- **Patterns**: `State` (Seat status: `AVAILABLE`, `TEMPORARILY_LOCKED`, `BOOKED`), `Strategy` (Dynamic seat pricing by tier: Silver, Gold, Platinum).
- **Concurrency**: Fine-grained keyed locks per seat using `ConcurrentHashMap<String, LockMetadata>`. Uses atomic check-and-reserve across all seats in the batch with rollback on partial failure.

#### Production-Ready Java Implementation

```java
import java.time.Duration;
import java.time.Instant;
import java.util.*;
import java.util.concurrent.*;

public class BookMyShowDemo {

    public enum SeatType { SILVER, GOLD, PLATINUM }
    public enum SeatStatus { AVAILABLE, TEMPORARILY_LOCKED, BOOKED }

    public record Seat(String seatId, int row, int col, SeatType type) {}

    public record LockMetadata(String lockedByUserId, Instant expiresAt) {
        public boolean isExpired() {
            return Instant.now().isAfter(expiresAt);
        }
    }

    public static class SeatLockManager {
        private final ConcurrentHashMap<String, LockMetadata> seatLocks = new ConcurrentHashMap<>();
        private final Set<String> permanentlyBookedSeats = ConcurrentHashMap.newKeySet();

        /**
         * Atomically attempts to lock a batch of seats. If ANY seat is locked or booked,
         * aborts the operation and acquires nothing.
         */
        public synchronized boolean acquireSeats(String showId, List<String> seatIds, String userId, Duration ttl) {
            // Step 1: Validate none of the requested seats are permanently booked or actively locked
            for (String seatId : seatIds) {
                String key = showKey(showId, seatId);
                if (permanentlyBookedSeats.contains(key)) return false;

                LockMetadata lock = seatLocks.get(key);
                if (lock != null && !lock.isExpired() && !lock.lockedByUserId().equals(userId)) {
                    return false; // Actively locked by another user
                }
            }

            // Step 2: Acquire locks for all seats
            Instant expiry = Instant.now().plus(ttl);
            for (String seatId : seatIds) {
                String key = showKey(showId, seatId);
                seatLocks.put(key, new LockMetadata(userId, expiry));
            }
            return true;
        }

        public synchronized boolean confirmBooking(String showId, List<String> seatIds, String userId) {
            // Verify caller owns active locks on all seats
            for (String seatId : seatIds) {
                String key = showKey(showId, seatId);
                LockMetadata lock = seatLocks.get(key);
                if (lock == null || lock.isExpired() || !lock.lockedByUserId().equals(userId)) {
                    return false;
                }
            }

            // Transition from temporarily locked to permanently booked
            for (String seatId : seatIds) {
                String key = showKey(showId, seatId);
                seatLocks.remove(key);
                permanentlyBookedSeats.add(key);
            }
            return true;
        }

        public synchronized void releaseSeats(String showId, List<String> seatIds, String userId) {
            for (String seatId : seatIds) {
                String key = showKey(showId, seatId);
                LockMetadata lock = seatLocks.get(key);
                if (lock != null && lock.lockedByUserId().equals(userId)) {
                    seatLocks.remove(key);
                }
            }
        }

        private String showKey(String showId, String seatId) {
            return showId + ":" + seatId;
        }
    }

    public static class BookingService {
        private final SeatLockManager lockManager = new SeatLockManager();
        private static final Duration LOCK_TTL = Duration.ofMinutes(10);

        public boolean selectSeats(String showId, List<String> seatIds, String userId) {
            return lockManager.acquireSeats(showId, seatIds, userId, LOCK_TTL);
        }

        public String checkout(String showId, List<String> seatIds, String userId, double paymentAmount) {
            boolean confirmed = lockManager.confirmBooking(showId, seatIds, userId);
            if (!confirmed) {
                throw new IllegalStateException("Seat reservation expired or unavailable.");
            }
            return "BKG-" + UUID.randomUUID().toString().substring(0, 8);
        }
    }
}
```

---

### 1.3 Amazon Locker Management System

#### Problem Overview
Design an automated parcel locker network (e.g., Amazon Locker, InPost) that manages:
- Compartments of multiple physical sizes (`SMALL`, `MEDIUM`, `LARGE`, `XLARGE`).
- Package dimension mapping ensuring a package is allocated to the smallest compartment that safely accommodates it.
- Delivery deposit, generating an immutable, cryptographic 6-digit PIN/OTP code with 72-hour customer pickup window.
- Automatic return-to-depot flow when user pickup TTL expires.

#### Core Domain Model & Design Patterns
- **Patterns**: `Strategy` (Best-Fit Compartment Allocation), `Observer` (Customer delivery SMS & pickup expiry notifications).
- **Extensibility**: Compartment size matching uses rank-based comparison (`SMALL(1) <= MEDIUM(2) <= LARGE(3) <= XLARGE(4)`).

#### Production-Ready Java Implementation

```java
import java.security.SecureRandom;
import java.time.Duration;
import java.time.Instant;
import java.util.*;
import java.util.concurrent.*;

public class AmazonLockerDemo {

    public enum LockerSize {
        SMALL(1), MEDIUM(2), LARGE(3), XLARGE(4);

        private final int capacityRank;
        LockerSize(int rank) { this.capacityRank = rank; }

        public boolean canFit(LockerSize packageSize) {
            return this.capacityRank >= packageSize.capacityRank;
        }
    }

    public enum CompartmentStatus { AVAILABLE, OCCUPIED, MAINTENANCE }

    public static class Compartment {
        private final String compartmentId;
        private final LockerSize size;
        private volatile CompartmentStatus status = CompartmentStatus.AVAILABLE;
        private volatile String currentPackageId;

        public Compartment(String id, LockerSize size) {
            this.compartmentId = id;
            this.size = size;
        }

        public synchronized boolean depositPackage(String packageId) {
            if (status != CompartmentStatus.AVAILABLE) return false;
            this.currentPackageId = packageId;
            this.status = CompartmentStatus.OCCUPIED;
            return true;
        }

        public synchronized String retrievePackage() {
            if (status != CompartmentStatus.OCCUPIED) return null;
            String pkg = this.currentPackageId;
            this.currentPackageId = null;
            this.status = CompartmentStatus.AVAILABLE;
            return pkg;
        }

        public String getCompartmentId() { return compartmentId; }
        public LockerSize getSize() { return size; }
        public CompartmentStatus getStatus() { return status; }
    }

    public record LockerTicket(
        String ticketId,
        String compartmentId,
        String packageId,
        String otpCode,
        Instant expiresAt
    ) {
        public boolean isExpired() { return Instant.now().isAfter(expiresAt); }
    }

    public static class LockerService {
        private final List<Compartment> compartments = new CopyOnWriteArrayList<>();
        private final Map<String, LockerTicket> activeByOtp = new ConcurrentHashMap<>();
        private final SecureRandom random = new SecureRandom();

        public void registerCompartment(Compartment compartment) {
            compartments.add(compartment);
        }

        public synchronized LockerTicket deposit(String packageId, LockerSize packageSize) {
            // Find smallest available compartment that accommodates packageSize
            Compartment target = compartments.stream()
                .filter(c -> c.getStatus() == CompartmentStatus.AVAILABLE && c.getSize().canFit(packageSize))
                .min(Comparator.comparing(Compartment::getSize))
                .orElseThrow(() -> new IllegalStateException("No compartment available for size: " + packageSize));

            target.depositPackage(packageId);

            String otp = String.format("%06d", random.nextInt(1_000_000));
            Instant expiry = Instant.now().plus(Duration.ofDays(3));
            String ticketId = "LCK-" + UUID.randomUUID().toString().substring(0, 8);

            LockerTicket ticket = new LockerTicket(ticketId, target.getCompartmentId(), packageId, otp, expiry);
            activeByOtp.put(otp, ticket);
            return ticket;
        }

        public String pickup(String otp) {
            LockerTicket ticket = activeByOtp.get(otp);
            if (ticket == null) throw new IllegalArgumentException("Invalid OTP code.");
            if (ticket.isExpired()) {
                throw new IllegalStateException("Pickup window expired. Package scheduled for return to warehouse.");
            }

            Compartment comp = compartments.stream()
                .filter(c -> c.getCompartmentId().equals(ticket.compartmentId()))
                .findFirst()
                .orElseThrow();

            activeByOtp.remove(otp);
            return comp.retrievePackage();
        }
    }
}
```

---

### 1.4 Car Rental System (Zoomcar / Hertz)

#### Problem Overview
Design an enterprise car rental management platform supporting:
- Vehicle inventory categorized by segment (`SEDAN`, `SUV`, `HATCHBACK`, `LUXURY`).
- Flexible dynamic pricing with stackable add-ons (Base Rental, Full Insurance Coverage, GPS Navigation, Roadside Assistance, Child Safety Seat).
- Vehicle lifecycle state transitions (`AVAILABLE`, `RESERVED`, `RENTED`, `UNDER_MAINTENANCE`).
- Overlap-free reservation date scheduling.

#### Core Domain Model & Design Patterns
- **Patterns**: `Decorator` pattern to dynamically compose price add-ons cleanly without exploding inheritance hierarchies; `State` pattern to prevent illegal lifecycle transitions.

#### Production-Ready Java Implementation

```java
import java.time.LocalDate;
import java.time.temporal.ChronoUnit;
import java.util.*;

public class CarRentalDemo {

    public enum VehicleType { HATCHBACK, SEDAN, SUV, LUXURY }
    public enum VehicleStatus { AVAILABLE, RESERVED, RENTED, MAINTENANCE }

    public static class Vehicle {
        private final String vehicleId;
        private final String model;
        private final VehicleType type;
        private VehicleStatus status = VehicleStatus.AVAILABLE;

        public Vehicle(String vehicleId, String model, VehicleType type) {
            this.vehicleId = vehicleId;
            this.model = model;
            this.type = type;
        }

        public synchronized void updateStatus(VehicleStatus newStatus) {
            this.status = newStatus;
        }

        public String getVehicleId() { return vehicleId; }
        public VehicleType getType() { return type; }
        public VehicleStatus getStatus() { return status; }
    }

    // Decorator Pattern for Stackable Add-on Pricing
    public interface RentalPackage {
        double getCostPerDay();
        String getDescription();
    }

    public static class BaseRental implements RentalPackage {
        private final VehicleType vehicleType;

        public BaseRental(VehicleType vehicleType) {
            this.vehicleType = vehicleType;
        }

        @Override
        public double getCostPerDay() {
            return switch (vehicleType) {
                case HATCHBACK -> 35.0;
                case SEDAN -> 50.0;
                case SUV -> 80.0;
                case LUXURY -> 150.0;
            };
        }

        @Override
        public String getDescription() {
            return vehicleType + " Base Rental";
        }
    }

    public static abstract class RentalAddonDecorator implements RentalPackage {
        protected final RentalPackage wrapped;
        public RentalAddonDecorator(RentalPackage wrapped) { this.wrapped = wrapped; }
    }

    public static class InsuranceAddon extends RentalAddonDecorator {
        public InsuranceAddon(RentalPackage wrapped) { super(wrapped); }
        @Override public double getCostPerDay() { return wrapped.getCostPerDay() + 15.0; }
        @Override public String getDescription() { return wrapped.getDescription() + " + Full Insurance"; }
    }

    public static class GpsAddon extends RentalAddonDecorator {
        public GpsAddon(RentalPackage wrapped) { super(wrapped); }
        @Override public double getCostPerDay() { return wrapped.getCostPerDay() + 5.0; }
        @Override public String getDescription() { return wrapped.getDescription() + " + GPS Navigation"; }
    }

    public static class ChildSeatAddon extends RentalAddonDecorator {
        public ChildSeatAddon(RentalPackage wrapped) { super(wrapped); }
        @Override public double getCostPerDay() { return wrapped.getCostPerDay() + 8.0; }
        @Override public String getDescription() { return wrapped.getDescription() + " + Child Safety Seat"; }
    }

    public record Reservation(
        String reservationId,
        String vehicleId,
        String customerId,
        LocalDate startDate,
        LocalDate endDate,
        RentalPackage rentalPackage,
        double totalCost
    ) {}

    public static class RentalService {
        public Reservation reserve(Vehicle vehicle, String customerId, LocalDate start, LocalDate end, RentalPackage pkg) {
            if (vehicle.getStatus() != VehicleStatus.AVAILABLE) {
                throw new IllegalStateException("Vehicle " + vehicle.getVehicleId() + " is currently unavailable.");
            }
            long days = ChronoUnit.DAYS.between(start, end);
            if (days <= 0) throw new IllegalArgumentException("Reservation duration must be at least 1 day.");

            double totalCost = days * pkg.getCostPerDay();
            vehicle.updateStatus(VehicleStatus.RESERVED);

            return new Reservation(
                "RES-" + UUID.randomUUID().toString().substring(0, 8),
                vehicle.getVehicleId(),
                customerId,
                start,
                end,
                pkg,
                totalCost
            );
        }
    }
}
```

---

# 2. State & Workflow Machines

Focuses on: **Formal State Machines (FSM)**, **Chain of Responsibility**, **event-driven lifecycle progression**, and **multi-agent dispatching algorithms**.

---

### 2.1 Vending Machine

#### Problem Overview
Design a coin-operated vending machine managing:
- Multiple item shelves with codes, prices, and stock inventory.
- State transitions: `Idle` $\to$ `HasCoin` $\to$ `Dispensing` $\to$ `SoldOut`.
- Coin insertions, selection validation, coin return/cancellation at any point before dispensing, and exact change calculation.

#### Core Domain Model & Design Patterns
- **Patterns**: `State` pattern encapsulating state-dependent operations into discrete classes (`IdleState`, `HasCoinState`, `DispensingState`, `SoldOutState`). Prevents monolithic nested `if-else` / `switch` structures.

#### Production-Ready Java Implementation

```java
import java.util.*;

public class VendingMachineDemo {

    public enum Coin {
        PENNY(1), NICKEL(5), DIME(10), QUARTER(25);
        private final int valueInCents;
        Coin(int value) { this.valueInCents = value; }
        public int getValue() { return valueInCents; }
    }

    public record Item(String code, String name, int priceInCents) {}

    public static class Inventory {
        private final Map<String, Item> items = new HashMap<>();
        private final Map<String, Integer> counts = new HashMap<>();

        public void addItem(Item item, int count) {
            items.put(item.code(), item);
            counts.put(item.code(), count);
        }

        public Item getItem(String code) { return items.get(code); }
        public boolean hasStock(String code) { return counts.getOrDefault(code, 0) > 0; }
        public void deductStock(String code) { counts.put(code, counts.get(code) - 1); }
    }

    public interface VendingState {
        void insertCoin(VendingMachine machine, Coin coin);
        void selectItem(VendingMachine machine, String itemCode);
        void dispense(VendingMachine machine);
        List<Coin> refund(VendingMachine machine);
    }

    public static class IdleState implements VendingState {
        @Override
        public void insertCoin(VendingMachine machine, Coin coin) {
            machine.addBalance(coin.getValue());
            machine.setState(new HasCoinState());
        }
        @Override public void selectItem(VendingMachine m, String code) {
            throw new IllegalStateException("Insert coins before selecting an item.");
        }
        @Override public void dispense(VendingMachine m) {
            throw new IllegalStateException("No active transaction.");
        }
        @Override public List<Coin> refund(VendingMachine m) {
            return Collections.emptyList();
        }
    }

    public static class HasCoinState implements VendingState {
        @Override
        public void insertCoin(VendingMachine machine, Coin coin) {
            machine.addBalance(coin.getValue());
        }

        @Override
        public void selectItem(VendingMachine machine, String itemCode) {
            Item item = machine.getInventory().getItem(itemCode);
            if (item == null) throw new IllegalArgumentException("Unknown item code: " + itemCode);
            if (!machine.getInventory().hasStock(itemCode)) {
                throw new IllegalStateException("Item " + item.name() + " is out of stock.");
            }
            if (machine.getBalance() < item.priceInCents()) {
                throw new IllegalStateException("Insufficient balance. Remaining: " + (item.priceInCents() - machine.getBalance()) + "c");
            }
            machine.setSelectedCode(itemCode);
            machine.setState(new DispensingState());
            machine.dispense();
        }

        @Override
        public void dispense(VendingMachine machine) {
            throw new IllegalStateException("Select an item first.");
        }

        @Override
        public List<Coin> refund(VendingMachine machine) {
            int refundAmount = machine.getBalance();
            machine.resetBalance();
            machine.setState(new IdleState());
            return machine.calculateChange(refundAmount);
        }
    }

    public static class DispensingState implements VendingState {
        @Override public void insertCoin(VendingMachine m, Coin c) { throw new IllegalStateException("Currently dispensing."); }
        @Override public void selectItem(VendingMachine m, String c) { throw new IllegalStateException("Currently dispensing."); }

        @Override
        public void dispense(VendingMachine machine) {
            String code = machine.getSelectedCode();
            Item item = machine.getInventory().getItem(code);
            machine.getInventory().deductStock(code);

            int changeDue = machine.getBalance() - item.priceInCents();
            machine.resetBalance();
            machine.setSelectedCode(null);

            System.out.println("Dispensed: " + item.name());
            if (changeDue > 0) {
                System.out.println("Returning change: " + changeDue + "c");
            }
            machine.setState(new IdleState());
        }

        @Override public List<Coin> refund(VendingMachine m) { throw new IllegalStateException("Cannot refund during dispensing."); }
    }

    public static class VendingMachine {
        private VendingState state = new IdleState();
        private final Inventory inventory = new Inventory();
        private int balance = 0;
        private String selectedCode;

        public void setState(VendingState state) { this.state = state; }
        public Inventory getInventory() { return inventory; }
        public int getBalance() { return balance; }
        public void addBalance(int cents) { this.balance += cents; }
        public void resetBalance() { this.balance = 0; }
        public String getSelectedCode() { return selectedCode; }
        public void setSelectedCode(String code) { this.selectedCode = code; }

        public void insertCoin(Coin coin) { state.insertCoin(this, coin); }
        public void selectItem(String code) { state.selectItem(this, code); }
        public void dispense() { state.dispense(this); }
        public List<Coin> refund() { return state.refund(this); }

        public List<Coin> calculateChange(int amountInCents) {
            List<Coin> coins = new ArrayList<>();
            int remaining = amountInCents;
            for (Coin c : new Coin[]{Coin.QUARTER, Coin.DIME, Coin.NICKEL, Coin.PENNY}) {
                while (remaining >= c.getValue()) {
                    coins.add(c);
                    remaining -= c.getValue();
                }
            }
            return coins;
        }
    }
}
```

---

### 2.2 Elevator Control System

#### Problem Overview
Design a multi-elevator bank control system in a modern high-rise building:
- Support internal car floor requests (passengers selecting target floor).
- Support external hall calls (passengers pressing UP or DOWN button on a floor).
- Implement the **SCAN / LOOK algorithm** (elevator serves all requests in current direction until none remain, then reverses).
- Efficient multi-car dispatching: pick the optimal elevator for an external request based on proximity, direction, and load.

#### Core Domain Model & Design Patterns
- **Scheduling Algorithm**: Dual Priority Queue representation per elevator car:
  - `upRequests` (`PriorityQueue<Integer>` min-heap): floors above current floor when moving UP.
  - `downRequests` (`PriorityQueue<Integer>` max-heap): floors below current floor when moving DOWN.
- **Patterns**: `State` (Direction: `UP`, `DOWN`, `IDLE`; Door: `OPEN`, `CLOSED`), `Strategy` (Dispatch algorithm).

#### Production-Ready Java Implementation

```java
import java.util.*;

public class ElevatorDemo {

    public enum Direction { UP, DOWN, IDLE }
    public enum DoorState { OPEN, CLOSED }

    public static class ElevatorCar {
        private final int id;
        private int currentFloor = 1;
        private Direction direction = Direction.IDLE;
        private DoorState doorState = DoorState.CLOSED;

        // Min-heap for UP requests (serves nearest floor first)
        private final PriorityQueue<Integer> upRequests = new PriorityQueue<>();
        // Max-heap for DOWN requests (serves highest floor first)
        private final PriorityQueue<Integer> downRequests = new PriorityQueue<>(Collections.reverseOrder());

        public ElevatorCar(int id) { this.id = id; }

        public synchronized void addRequest(int targetFloor) {
            if (targetFloor == currentFloor) {
                openAndCloseDoor();
                return;
            }

            if (targetFloor > currentFloor) {
                upRequests.add(targetFloor);
                if (direction == Direction.IDLE) direction = Direction.UP;
            } else {
                downRequests.add(targetFloor);
                if (direction == Direction.IDLE) direction = Direction.DOWN;
            }
        }

        public synchronized void step() {
            if (direction == Direction.UP) {
                if (!upRequests.isEmpty()) {
                    currentFloor = upRequests.poll();
                    openAndCloseDoor();
                }
                if (upRequests.isEmpty()) {
                    direction = downRequests.isEmpty() ? Direction.IDLE : Direction.DOWN;
                }
            } else if (direction == Direction.DOWN) {
                if (!downRequests.isEmpty()) {
                    currentFloor = downRequests.poll();
                    openAndCloseDoor();
                }
                if (downRequests.isEmpty()) {
                    direction = upRequests.isEmpty() ? Direction.IDLE : Direction.UP;
                }
            }
        }

        private void openAndCloseDoor() {
            doorState = DoorState.OPEN;
            // Passenger ingress/egress simulation
            doorState = DoorState.CLOSED;
        }

        public int calculateSuitability(int floor, Direction requestedDirection) {
            int distance = Math.abs(currentFloor - floor);
            if (direction == Direction.IDLE) return distance;
            if (direction == requestedDirection) {
                if (direction == Direction.UP && floor >= currentFloor) return distance;
                if (direction == Direction.DOWN && floor <= currentFloor) return distance;
            }
            return distance + 100; // Penalty for moving in opposite direction
        }

        public int getId() { return id; }
        public int getCurrentFloor() { return currentFloor; }
        public Direction getDirection() { return direction; }
    }

    public static class ElevatorDispatcher {
        private final List<ElevatorCar> elevators;

        public ElevatorDispatcher(List<ElevatorCar> elevators) {
            this.elevators = elevators;
        }

        public synchronized ElevatorCar dispatchHallCall(int floor, Direction direction) {
            ElevatorCar bestCar = elevators.stream()
                .min(Comparator.comparingInt(car -> car.calculateSuitability(floor, direction)))
                .orElseThrow();

            bestCar.addRequest(floor);
            return bestCar;
        }
    }
}
```

---

### 2.3 ATM Cash Dispenser

#### Problem Overview
Design a self-service ATM cash dispenser handling:
- Customer debit card authentication and account balance verification.
- Dispensing currency notes of various denominations ($100, $50, $20, $10).
- Dynamically managing internal physical note counts for each cassette.
- Rejecting requests that cannot be fulfilled with exact denominations or when total cash balance is insufficient.

#### Core Domain Model & Design Patterns
- **Patterns**: `Chain of Responsibility` pattern where each denomination dispenser handles as many notes of its denomination as possible, then passes the remainder to the next node in the chain.

#### Production-Ready Java Implementation

```java
import java.util.*;

public class AtmCashDispenserDemo {

    public static abstract class CashDispenser {
        protected final int denomination;
        protected int availableNotes;
        protected CashDispenser nextDispenser;

        public CashDispenser(int denomination, int initialNotes) {
            this.denomination = denomination;
            this.availableNotes = initialNotes;
        }

        public void setNextDispenser(CashDispenser next) {
            this.nextDispenser = next;
        }

        public synchronized void dispense(int remainingAmount, Map<Integer, Integer> dispensedSummary) {
            if (remainingAmount <= 0) return;

            int neededNotes = remainingAmount / denomination;
            int notesToDispense = Math.min(neededNotes, availableNotes);

            if (notesToDispense > 0) {
                availableNotes -= notesToDispense;
                dispensedSummary.put(denomination, notesToDispense);
                remainingAmount -= (notesToDispense * denomination);
            }

            if (remainingAmount > 0) {
                if (nextDispenser != null) {
                    nextDispenser.dispense(remainingAmount, dispensedSummary);
                } else {
                    throw new IllegalStateException("Unable to dispense exact cash amount with available denominations.");
                }
            }
        }
    }

    public static class Dispenser100 extends CashDispenser { public Dispenser100(int count) { super(100, count); } }
    public static class Dispenser50 extends CashDispenser { public Dispenser50(int count) { super(50, count); } }
    public static class Dispenser20 extends CashDispenser { public Dispenser20(int count) { super(20, count); } }
    public static class Dispenser10 extends CashDispenser { public Dispenser10(int count) { super(10, count); } }

    public static class AtmService {
        private final CashDispenser dispenserChain;

        public AtmService() {
            CashDispenser d100 = new Dispenser100(50);
            CashDispenser d50 = new Dispenser50(50);
            CashDispenser d20 = new Dispenser20(100);
            CashDispenser d10 = new Dispenser10(100);

            d100.setNextDispenser(d50);
            d50.setNextDispenser(d20);
            d20.setNextDispenser(d10);
            this.dispenserChain = d100;
        }

        public synchronized Map<Integer, Integer> withdrawCash(int amount) {
            if (amount <= 0 || amount % 10 != 0) {
                throw new IllegalArgumentException("Amount must be a positive multiple of 10.");
            }
            Map<Integer, Integer> dispensed = new LinkedHashMap<>();
            dispenserChain.dispense(amount, dispensed);
            return dispensed;
        }
    }
}
```

---

### 2.4 Order Management System (OMS)

#### Problem Overview
Design a production order fulfillment engine handling:
- Multi-step order lifecycle: `CREATED` $\to$ `PAYMENT_PENDING` $\to$ `PAID` $\to$ `PACKING` $\to$ `SHIPPED` $\to$ `DELIVERED` (with terminal states `CANCELLED`, `REFUNDED`).
- Validation preventing illegal state transitions (e.g., an order cannot transition from `CREATED` directly to `SHIPPED`).
- Event-driven notifications decoupling downstream actions (Inventory Reserve, SMS Confirmation, Analytics Logging).

#### Core Domain Model & Design Patterns
- **Patterns**: `Rich Enum / State Machine` for transition validation; `Observer` pattern for asynchronous downstream event listeners.

#### Production-Ready Java Implementation

```java
import java.util.*;
import java.util.concurrent.CopyOnWriteArrayList;

public class OrderManagementDemo {

    public enum OrderStatus {
        CREATED {
            @Override public boolean canTransitionTo(OrderStatus next) { return next == PAYMENT_PENDING || next == CANCELLED; }
        },
        PAYMENT_PENDING {
            @Override public boolean canTransitionTo(OrderStatus next) { return next == PAID || next == CANCELLED; }
        },
        PAID {
            @Override public boolean canTransitionTo(OrderStatus next) { return next == PACKING || next == REFUNDED; }
        },
        PACKING {
            @Override public boolean canTransitionTo(OrderStatus next) { return next == SHIPPED || next == CANCELLED; }
        },
        SHIPPED {
            @Override public boolean canTransitionTo(OrderStatus next) { return next == DELIVERED; }
        },
        DELIVERED {
            @Override public boolean canTransitionTo(OrderStatus next) { return next == REFUNDED; }
        },
        CANCELLED {
            @Override public boolean canTransitionTo(OrderStatus next) { return false; }
        },
        REFUNDED {
            @Override public boolean canTransitionTo(OrderStatus next) { return false; }
        };

        public abstract boolean canTransitionTo(OrderStatus next);
    }

    public record OrderLineItem(String sku, int quantity, double unitPrice) {}

    public interface OrderLifecycleListener {
        void onStatusChanged(String orderId, OrderStatus from, OrderStatus to);
    }

    public static class Order {
        private final String orderId;
        private final List<OrderLineItem> items;
        private OrderStatus status = OrderStatus.CREATED;
        private final List<OrderLifecycleListener> listeners = new CopyOnWriteArrayList<>();

        public Order(String orderId, List<OrderLineItem> items) {
            this.orderId = orderId;
            this.items = List.copyOf(items);
        }

        public void addListener(OrderLifecycleListener listener) {
            listeners.add(listener);
        }

        public synchronized void transitionTo(OrderStatus newStatus) {
            if (!this.status.canTransitionTo(newStatus)) {
                throw new IllegalStateException("Illegal state transition from " + this.status + " to " + newStatus);
            }
            OrderStatus oldStatus = this.status;
            this.status = newStatus;

            for (OrderLifecycleListener listener : listeners) {
                listener.onStatusChanged(orderId, oldStatus, newStatus);
            }
        }

        public String getOrderId() { return orderId; }
        public OrderStatus getStatus() { return status; }
        public List<OrderLineItem> getItems() { return items; }
    }
}
```

---

# 3. Matching, Ledgers & Marketplaces

Focuses on: **Graph debt minimization algorithms**, **spatial matching**, **Facade orchestration**, and **fine-grained inventory reservations**.

---

### 3.1 Splitwise (Expense Sharing with Debt Simplification)

#### Problem Overview
Design an expense sharing and ledger tracking platform (like Splitwise):
- Support multiple split types: `EQUAL`, `EXACT` dollar amounts, and `PERCENTAGE` splits.
- Maintain net balance ledgers between users across individual and group expenses.
- **Debt Simplification Algorithm**: Minimize the total number of inter-user settling transactions using a greedy min-cash-flow graph settlement algorithm.

#### Core Domain Model & Design Patterns
- **Patterns**: `Strategy` (Split computation: `EqualSplit`, `ExactSplit`, `PercentSplit`), `Observer` (Balance update notifications).
- **Algorithm**: Net balance reduction with dual PriorityQueues (`Debtors` ascending min-heap, `Creditors` descending max-heap). Reduces up to $N(N - 1)$ pairwise debts to at most $N - 1$ total transactions.

#### Production-Ready Java Implementation

```java
import java.util.*;

public class SplitwiseDemo {

    public record User(String userId, String name, String email) {}

    public enum SplitType { EQUAL, EXACT, PERCENT }

    public record Split(String userId, double amount) {}

    public static class DebtSimplifier {
        public record Transaction(String fromUser, String toUser, double amount) {}

        /**
         * Solves the Min-Cash-Flow problem greedily using dual heaps.
         * Runs in O(V log V) time where V is the number of users.
         */
        public static List<Transaction> simplifyDebts(Map<String, Double> netBalances) {
            // Debtors: sorted by balance ascending (most negative first)
            PriorityQueue<Map.Entry<String, Double>> debtors =
                new PriorityQueue<>(Comparator.comparingDouble(Map.Entry::getValue));

            // Creditors: sorted by balance descending (highest positive first)
            PriorityQueue<Map.Entry<String, Double>> creditors =
                new PriorityQueue<>((a, b) -> Double.compare(b.getValue(), a.getValue()));

            for (Map.Entry<String, Double> entry : netBalances.entrySet()) {
                if (entry.getValue() < -0.01) debtors.add(new AbstractMap.SimpleEntry<>(entry));
                else if (entry.getValue() > 0.01) creditors.add(new AbstractMap.SimpleEntry<>(entry));
            }

            List<Transaction> transactions = new ArrayList<>();
            while (!debtors.isEmpty() && !creditors.isEmpty()) {
                var debtor = debtors.poll();
                var creditor = creditors.poll();

                double debit = -debtor.getValue();
                double credit = creditor.getValue();
                double settledAmount = Math.min(debit, credit);

                transactions.add(new Transaction(debtor.getKey(), creditor.getKey(), Math.round(settledAmount * 100.0) / 100.0));

                if (debit > settledAmount + 0.01) {
                    debtor.setValue(-(debit - settledAmount));
                    debtors.add(debtor);
                }
                if (credit > settledAmount + 0.01) {
                    creditor.setValue(credit - settledAmount);
                    creditors.add(creditor);
                }
            }
            return transactions;
        }
    }

    public static class ExpenseService {
        private final Map<String, Map<String, Double>> pairwiseBalance = new HashMap<>();

        public synchronized void addExpense(String paidBy, double totalAmount, List<Split> splits) {
            for (Split s : splits) {
                if (s.userId().equals(paidBy)) continue;
                adjustBalance(s.userId(), paidBy, s.amount());
            }
        }

        private void adjustBalance(String debtor, String creditor, double amount) {
            pairwiseBalance.putIfAbsent(debtor, new HashMap<>());
            pairwiseBalance.get(debtor).merge(creditor, amount, Double::sum);

            pairwiseBalance.putIfAbsent(creditor, new HashMap<>());
            pairwiseBalance.get(creditor).merge(debtor, -amount, Double::sum);
        }

        public Map<String, Double> computeNetBalances() {
            Map<String, Double> net = new HashMap<>();
            for (var outer : pairwiseBalance.entrySet()) {
                for (var inner : outer.getValue().entrySet()) {
                    net.merge(inner.getKey(), inner.getValue(), Double::sum);
                }
            }
            return net;
        }
    }
}
```

---

### 3.2 Ride-Sharing Service (Uber / Lyft)

#### Problem Overview
Design a distributed ride-hailing backend supporting:
- Rider trip requests with pickup and drop coordinates.
- Spatial driver matching (e.g., nearest available driver, highest-rated driver within a 5 km radius).
- Dynamic pricing calculation based on base fare, distance, and real-time demand surge multiplier.
- Trip lifecycle: `REQUESTED` $\to$ `ACCEPTED` $\to$ `DRIVER_ARRIVED` $\to$ `IN_TRIP` $\to$ `COMPLETED` $\to$ `CANCELLED`.

#### Core Domain Model & Design Patterns
- **Patterns**: `Strategy` (Driver matching and surge pricing), `Decorator` (Toll roads, night-shift airport surcharges), `Observer` (Live location and trip progress events).

#### Production-Ready Java Implementation

```java
import java.util.*;
import java.util.concurrent.*;

public class UberDemo {

    public record Location(double latitude, double longitude) {
        public double distanceTo(Location other) {
            // Simplified Euclidean approximation for demo; use Haversine in production
            double dx = this.latitude - other.latitude;
            double dy = this.longitude - other.longitude;
            return Math.sqrt(dx * dx + dy * dy) * 111.0; // km
        }
    }

    public enum DriverStatus { AVAILABLE, ON_TRIP, OFFLINE }

    public static class Driver {
        private final String driverId;
        private Location location;
        private double rating;
        private DriverStatus status = DriverStatus.AVAILABLE;

        public Driver(String id, Location loc, double rating) {
            this.driverId = id;
            this.location = loc;
            this.rating = rating;
        }

        public synchronized boolean tryAssign() {
            if (status == DriverStatus.AVAILABLE) {
                status = DriverStatus.ON_TRIP;
                return true;
            }
            return false;
        }

        public String getDriverId() { return driverId; }
        public Location getLocation() { return location; }
        public double getRating() { return rating; }
        public DriverStatus getStatus() { return status; }
    }

    public interface DriverMatchingStrategy {
        Optional<Driver> match(Location pickup, List<Driver> availableDrivers);
    }

    public static class NearestDriverStrategy implements DriverMatchingStrategy {
        @Override
        public Optional<Driver> match(Location pickup, List<Driver> availableDrivers) {
            return availableDrivers.stream()
                .filter(d -> d.getStatus() == DriverStatus.AVAILABLE)
                .min(Comparator.comparingDouble(d -> d.getLocation().distanceTo(pickup)));
        }
    }

    public static class PricingEngine {
        private static final double BASE_FARE = 5.0;
        private static final double PER_KM_RATE = 2.0;

        public static double calculateFare(Location pickup, Location drop, double surgeMultiplier) {
            double distanceKm = pickup.distanceTo(drop);
            return (BASE_FARE + (distanceKm * PER_KM_RATE)) * surgeMultiplier;
        }
    }

    public record Trip(
        String tripId,
        String riderId,
        String driverId,
        Location pickup,
        Location drop,
        double fare
    ) {}

    public static class RideDispatchService {
        private final List<Driver> drivers = new CopyOnWriteArrayList<>();
        private final DriverMatchingStrategy matchingStrategy;

        public RideDispatchService(DriverMatchingStrategy matchingStrategy) {
            this.matchingStrategy = matchingStrategy;
        }

        public void registerDriver(Driver driver) { drivers.add(driver); }

        public synchronized Trip requestRide(String riderId, Location pickup, Location drop, double surge) {
            Optional<Driver> matchedDriver = matchingStrategy.match(pickup, drivers);
            if (matchedDriver.isEmpty() || !matchedDriver.get().tryAssign()) {
                throw new IllegalStateException("No available drivers nearby. Please try again.");
            }

            double fare = PricingEngine.calculateFare(pickup, drop, surge);
            String tripId = "TRIP-" + UUID.randomUUID().toString().substring(0, 8);
            return new Trip(tripId, riderId, matchedDriver.get().getDriverId(), pickup, drop, fare);
        }
    }
}
```

---

### 3.3 Food Delivery System (Swiggy / DoorDash)

#### Problem Overview
Design a high-throughput food ordering platform supporting:
- Restaurant menu listings and order cart construction.
- Atomic checkout orchestration across inventory check, payment gateway, kitchen order firing, and courier assignment.
- Real-time order progress updates via the Observer pattern.

#### Core Domain Model & Design Patterns
- **Patterns**: `Facade` (`FoodOrderFacade`) encapsulating complex subsystem interactions into a clean client entry point; `Observer` for customer push notifications.

#### Production-Ready Java Implementation

```java
import java.util.*;
import java.util.concurrent.CopyOnWriteArrayList;

public class FoodDeliveryDemo {

    public record FoodItem(String id, String name, double price) {}
    public record CartItem(FoodItem item, int quantity) {}

    public static class RestaurantService {
        public boolean verifyMenuAvailability(String restaurantId, List<CartItem> items) {
            return true; // Simplified: inventory confirmed
        }
        public void fireKitchenOrder(String restaurantId, String orderId, List<CartItem> items) {
            System.out.println("Kitchen preparing order " + orderId + " for restaurant " + restaurantId);
        }
    }

    public static class PaymentService {
        public boolean processPayment(String customerId, double amount) {
            return amount > 0;
        }
    }

    public static class DeliveryPartnerService {
        public String assignNearestCourier(String restaurantId) {
            return "COURIER-" + UUID.randomUUID().toString().substring(0, 6);
        }
    }

    // Facade Pattern unifying checkout workflows
    public static class FoodOrderFacade {
        private final RestaurantService restaurantService = new RestaurantService();
        private final PaymentService paymentService = new PaymentService();
        private final DeliveryPartnerService deliveryService = new DeliveryPartnerService();

        public record OrderConfirmation(String orderId, String courierId, double totalAmount) {}

        public OrderConfirmation placeOrder(String customerId, String restaurantId, List<CartItem> cart) {
            // 1. Verify availability
            if (!restaurantService.verifyMenuAvailability(restaurantId, cart)) {
                throw new IllegalStateException("Selected items are out of stock.");
            }

            // 2. Calculate total
            double total = cart.stream().mapToDouble(c -> c.item().price() * c.quantity()).sum();

            // 3. Process payment
            boolean paid = paymentService.processPayment(customerId, total);
            if (!paid) throw new IllegalStateException("Payment processing failed.");

            // 4. Fire order to restaurant kitchen
            String orderId = "ORD-" + UUID.randomUUID().toString().substring(0, 8);
            restaurantService.fireKitchenOrder(restaurantId, orderId, cart);

            // 5. Assign delivery courier
            String courierId = deliveryService.assignNearestCourier(restaurantId);

            return new OrderConfirmation(orderId, courierId, total);
        }
    }
}
```

---

### 3.4 Inventory & Shopping Cart System

#### Problem Overview
Design an e-commerce shopping cart and inventory engine handling:
- Multi-item shopping carts with dynamic coupon stacking (e.g., 20% off plus $5 seasonal voucher).
- **Flash Sale Concurrency**: Prevent overselling stock under massive concurrent checkout waves.
- Temporary inventory reservations with automatic TTL release if checkout is abandoned.

#### Core Domain Model & Design Patterns
- **Patterns**: `Decorator` pattern for layered discount calculation; Atomic stock decrement via `AtomicInteger` or Compare-And-Swap.

#### Production-Ready Java Implementation

```java
import java.time.Duration;
import java.time.Instant;
import java.util.*;
import java.util.concurrent.*;
import java.util.concurrent.atomic.AtomicInteger;

public class InventoryCartDemo {

    public static class ProductInventory {
        private final String sku;
        private final AtomicInteger availableStock;
        private final ConcurrentHashMap<String, ReservationMetadata> activeReservations = new ConcurrentHashMap<>();

        public record ReservationMetadata(int quantity, Instant expiresAt) {
            public boolean isExpired() { return Instant.now().isAfter(expiresAt); }
        }

        public ProductInventory(String sku, int initialStock) {
            this.sku = sku;
            this.availableStock = new AtomicInteger(initialStock);
        }

        public boolean reserve(String reservationId, int quantity, Duration ttl) {
            while (true) {
                int current = availableStock.get();
                if (current < quantity) return false;
                if (availableStock.compareAndSet(current, current - quantity)) {
                    activeReservations.put(reservationId, new ReservationMetadata(quantity, Instant.now().plus(ttl)));
                    return true;
                }
            }
        }

        public void commit(String reservationId) {
            activeReservations.remove(reservationId);
        }

        public void rollback(String reservationId) {
            ReservationMetadata meta = activeReservations.remove(reservationId);
            if (meta != null) {
                availableStock.addAndGet(meta.quantity());
            }
        }

        public int getStock() { return availableStock.get(); }
    }

    // Decorator for Cart Discount Rules
    public interface CartPriceCalculator {
        double calculateTotal(double subtotal);
    }

    public static class BaseCartPrice implements CartPriceCalculator {
        @Override public double calculateTotal(double subtotal) { return subtotal; }
    }

    public static class PercentageDiscountDecorator implements CartPriceCalculator {
        private final CartPriceCalculator wrapped;
        private final double discountPercent; // e.g. 0.15 for 15%

        public PercentageDiscountDecorator(CartPriceCalculator wrapped, double discountPercent) {
            this.wrapped = wrapped;
            this.discountPercent = discountPercent;
        }

        @Override
        public double calculateTotal(double subtotal) {
            double current = wrapped.calculateTotal(subtotal);
            return current * (1.0 - discountPercent);
        }
    }

    public static class FixedCouponDiscountDecorator implements CartPriceCalculator {
        private final CartPriceCalculator wrapped;
        private final double fixedDeduction;

        public FixedCouponDiscountDecorator(CartPriceCalculator wrapped, double fixedDeduction) {
            this.wrapped = wrapped;
            this.fixedDeduction = fixedDeduction;
        }

        @Override
        public double calculateTotal(double subtotal) {
            double current = wrapped.calculateTotal(subtotal);
            return Math.max(0.0, current - fixedDeduction);
        }
    }
}
```

---

# 4. Board & Turn-Based Games

Focuses on: **Turn-based player queue state machines**, **Polymorphic move validation**, **Command pattern for undo/redo**, and **$O(1)$ board win evaluation algorithms**.

---

### 4.1 Snake and Ladder

#### Problem Overview
Design a modular, extensible Snake and Ladder game supporting:
- Configurable board size (default 1 to 100) with dynamic snakes (`start > end`) and ladders (`start < end`).
- Multi-player turn management using a cyclic FIFO queue.
- Pluggable dice rolling strategy (fair 6-sided dice, multi-dice, or rigged dice for testing).
- Rules: Exact roll required to reach cell 100; consecutive 6s rules (optional).

#### Core Domain Model & Design Patterns
- **Patterns**: `Strategy` (Dice rolling), `Queue` (Cyclic player turns).

#### Production-Ready Java Implementation

```java
import java.util.*;
import java.util.concurrent.ThreadLocalRandom;

public class SnakeAndLadderDemo {

    public record Jump(int start, int end) {
        public Jump {
            if (start == end) throw new IllegalArgumentException("Jump start and end cannot be identical.");
        }
        public boolean isSnake() { return start > end; }
        public boolean isLadder() { return start < end; }
    }

    public static class Player {
        private final String name;
        private int position = 0;

        public Player(String name) { this.name = name; }
        public String getName() { return name; }
        public int getPosition() { return position; }
        public void setPosition(int position) { this.position = position; }
    }

    public interface DiceStrategy {
        int roll();
    }

    public static class StandardDice implements DiceStrategy {
        @Override public int roll() {
            return ThreadLocalRandom.current().nextInt(1, 7);
        }
    }

    public static class SnakeAndLadderGame {
        private final int boardSize;
        private final Map<Integer, Integer> jumps = new HashMap<>();
        private final Deque<Player> players = new ArrayDeque<>();
        private final DiceStrategy dice;
        private Player winner = null;

        public SnakeAndLadderGame(int boardSize, List<Jump> jumpList, List<Player> playerList, DiceStrategy dice) {
            this.boardSize = boardSize;
            for (Jump j : jumpList) jumps.put(j.start(), j.end());
            players.addAll(playerList);
            this.dice = dice;
        }

        public boolean isGameOver() { return winner != null; }

        public void playTurn() {
            if (isGameOver()) throw new IllegalStateException("Game is already over. Winner: " + winner.getName());

            Player current = players.pollFirst();
            int roll = dice.roll();
            int nextPos = current.getPosition() + roll;

            if (nextPos <= boardSize) {
                // Check snake or ladder jump
                if (jumps.containsKey(nextPos)) {
                    nextPos = jumps.get(nextPos);
                }
                current.setPosition(nextPos);

                if (current.getPosition() == boardSize) {
                    winner = current;
                    System.out.println("🎉 Player " + current.getName() + " wins the game!");
                    return;
                }
            }
            players.addLast(current); // Requeue for next turn
        }

        public Player getWinner() { return winner; }
    }
}
```

---

### 4.2 Chess Game

#### Problem Overview
Design an extensible object-oriented Chess game engine:
- $8 \times 8$ grid of spots with two players (`WHITE` and `BLACK`).
- Polymorphic movement rules for each piece type: `King`, `Queen`, `Rook`, `Bishop`, `Knight`, `Pawn`.
- **Command Pattern**: Encapsulate every move as a command object to support move history logging, undo/redo, and replay features.

#### Core Domain Model & Design Patterns
- **Patterns**: `Command` (Move execution & undo), `Strategy` / Subclass Polymorphism (`Piece.canMove()`), `State` (`Check`, `Checkmate`, `Stalemate`).

#### Production-Ready Java Implementation

```java
import java.util.*;

public class ChessDemo {

    public enum Color { WHITE, BLACK }

    public record Spot(int row, int col) {
        public boolean isValid() { return row >= 0 && row < 8 && col >= 0 && col < 8; }
    }

    public static abstract class Piece {
        private final Color color;
        private boolean killed = false;

        public Piece(Color color) { this.color = color; }
        public Color getColor() { return color; }
        public boolean isKilled() { return killed; }
        public void setKilled(boolean killed) { this.killed = killed; }

        public abstract boolean canMove(Spot start, Spot end, Piece destinationPiece);
    }

    public static class Rook extends Piece {
        public Rook(Color color) { super(color); }
        @Override
        public boolean canMove(Spot start, Spot end, Piece destinationPiece) {
            if (destinationPiece != null && destinationPiece.getColor() == getColor()) return false;
            return start.row() == end.row() || start.col() == end.col();
        }
    }

    public static class Knight extends Piece {
        public Knight(Color color) { super(color); }
        @Override
        public boolean canMove(Spot start, Spot end, Piece destinationPiece) {
            if (destinationPiece != null && destinationPiece.getColor() == getColor()) return false;
            int dr = Math.abs(start.row() - end.row());
            int dc = Math.abs(start.col() - end.col());
            return (dr == 1 && dc == 2) || (dr == 2 && dc == 1);
        }
    }

    // Command Pattern for Undoable Moves
    public interface ChessCommand {
        boolean execute();
        void undo();
    }

    public static class MoveCommand implements ChessCommand {
        private final Piece[][] board;
        private final Spot start;
        private final Spot end;
        private Piece capturedPiece;

        public MoveCommand(Piece[][] board, Spot start, Spot end) {
            this.board = board;
            this.start = start;
            this.end = end;
        }

        @Override
        public boolean execute() {
            Piece moving = board[start.row()][start.col()];
            if (moving == null) return false;

            capturedPiece = board[end.row()][end.col()];
            if (!moving.canMove(start, end, capturedPiece)) return false;

            if (capturedPiece != null) capturedPiece.setKilled(true);
            board[end.row()][end.col()] = moving;
            board[start.row()][start.col()] = null;
            return true;
        }

        @Override
        public void undo() {
            Piece moved = board[end.row()][end.col()];
            board[start.row()][start.col()] = moved;
            board[end.row()][end.col()] = capturedPiece;
            if (capturedPiece != null) capturedPiece.setKilled(false);
        }
    }
}
```

---

### 4.3 Tic-Tac-Toe (N x N Scalable)

#### Problem Overview
Design a generalized $N \times N$ Tic-Tac-Toe game engine:
- Scalable to any grid dimension $N$ (e.g., $3 \times 3$, $5 \times 5$, $1000 \times 1000$).
- Support two players (`X` and `O`).
- **$O(1)$ Win Verification**: Check whether a player has won in constant time without inspecting all $N^2$ cells or running loops across rows/columns.

#### Core Domain Model & Design Patterns
- **Algorithm**: Maintain integer frequency arrays for row and column sums, and two integer variables for the main and anti-diagonals.
  - Player 1 places `+1`, Player 2 places `-1`.
  - Win condition: When any row, col, diag, or anti-diag sum reaches $+N$ (Player 1) or $-N$ (Player 2).

#### Production-Ready Java Implementation

```java
public class TicTacToeDemo {

    public enum PlayerPiece {
        X(1), O(-1);
        private final int value;
        PlayerPiece(int value) { this.value = value; }
        public int getValue() { return value; }
    }

    public static class TicTacToeEngine {
        private final int size;
        private final int[] rowSums;
        private final int[] colSums;
        private int diagSum = 0;
        private int antiDiagSum = 0;
        private int totalMoves = 0;
        private boolean isFinished = false;

        public TicTacToeEngine(int size) {
            this.size = size;
            this.rowSums = new int[size];
            this.colSums = new int[size];
        }

        /**
         * Validates and records a move. Returns:
         * 1 if Player X wins,
         * 2 if Player O wins,
         * 0 if the game continues,
         * -1 if the game is a draw.
         * Runs strictly in O(1) time and O(N) space.
         */
        public int makeMove(int row, int col, PlayerPiece piece) {
            if (isFinished) throw new IllegalStateException("Game already finished.");
            if (row < 0 || row >= size || col < 0 || col >= size) {
                throw new IllegalArgumentException("Coordinate out of bounds.");
            }

            int val = piece.getValue();
            rowSums[row] += val;
            colSums[col] += val;

            if (row == col) diagSum += val;
            if (row + col == size - 1) antiDiagSum += val;

            totalMoves++;
            int target = val * size;

            if (rowSums[row] == target || colSums[col] == target || diagSum == target || antiDiagSum == target) {
                isFinished = true;
                return piece == PlayerPiece.X ? 1 : 2;
            }

            if (totalMoves == size * size) {
                isFinished = true;
                return -1; // Draw
            }

            return 0; // In progress
        }
    }
}
```

---

# 5. Core Backend Infrastructure

Focuses on: **Thread safety**, **low-latency concurrency primitives**, **asynchronous task buffering**, and **distributed systems building blocks**.

---

### 5.1 Thread-Safe LRU / LFU Cache with TTL

#### Problem Overview
Design a high-throughput, in-memory generic cache:
- $O(1)$ time complexity for both `get(key)` and `put(key, value)`.
- Evict Least Recently Used (LRU) entry when cache capacity is exceeded.
- **Time-to-Live (TTL)** support: Expire entries after a specified duration.
- High concurrent read throughput using `ReentrantReadWriteLock`.

#### Core Domain Model & Design Patterns
- **Data Structures**: Hash map for $O(1)$ key lookups + custom Doubly Linked List for $O(1)$ node promotion and eviction.
- **Concurrency**: `ReentrantReadWriteLock` allows concurrent reader threads while serializing writes.

#### Production-Ready Java Implementation

```java
import java.time.Duration;
import java.time.Instant;
import java.util.*;
import java.util.concurrent.locks.ReentrantReadWriteLock;

public class ThreadSafeLruCache<K, V> {

    private static class Node<K, V> {
        K key;
        V value;
        Instant expiresAt;
        Node<K, V> prev;
        Node<K, V> next;

        Node(K key, V value, Instant expiresAt) {
            this.key = key;
            this.value = value;
            this.expiresAt = expiresAt;
        }

        boolean isExpired() {
            return expiresAt != null && Instant.now().isAfter(expiresAt);
        }
    }

    private final int capacity;
    private final Map<K, Node<K, V>> map = new HashMap<>();
    private final Node<K, V> head = new Node<>(null, null, null);
    private final Node<K, V> tail = new Node<>(null, null, null);
    private final ReentrantReadWriteLock rwLock = new ReentrantReadWriteLock();

    public ThreadSafeLruCache(int capacity) {
        this.capacity = capacity;
        head.next = tail;
        tail.prev = head;
    }

    public V get(K key) {
        rwLock.writeLock().lock(); // Write lock needed because LRU order updates on read
        try {
            Node<K, V> node = map.get(key);
            if (node == null) return null;
            if (node.isExpired()) {
                removeNode(node);
                map.remove(key);
                return null;
            }
            moveToHead(node);
            return node.value;
        } finally {
            rwLock.writeLock().unlock();
        }
    }

    public void put(K key, V value, Duration ttl) {
        rwLock.writeLock().lock();
        try {
            Instant expiry = ttl != null ? Instant.now().plus(ttl) : null;
            Node<K, V> existing = map.get(key);
            if (existing != null) {
                existing.value = value;
                existing.expiresAt = expiry;
                moveToHead(existing);
                return;
            }

            if (map.size() >= capacity) {
                Node<K, V> lru = tail.prev;
                removeNode(lru);
                map.remove(lru.key);
            }

            Node<K, V> newNode = new Node<>(key, value, expiry);
            map.put(key, newNode);
            addFirst(newNode);
        } finally {
            rwLock.writeLock().unlock();
        }
    }

    private void addFirst(Node<K, V> node) {
        node.next = head.next;
        node.prev = head;
        head.next.prev = node;
        head.next = node;
    }

    private void removeNode(Node<K, V> node) {
        node.prev.next = node.next;
        node.next.prev = node.prev;
    }

    private void moveToHead(Node<K, V> node) {
        removeNode(node);
        addFirst(node);
    }
}
```

---

### 5.2 Rate Limiter (Token Bucket & Sliding Window)

#### Problem Overview
Design a thread-safe in-memory rate limiter supporting:
- **Token Bucket Algorithm**: Smooth continuous token refilling with burst tolerance up to bucket capacity.
- **Sliding Window Log Algorithm**: Exact request rate enforcement over a sliding time window.

#### Core Domain Model & Design Patterns
- **Patterns**: `Strategy` (Token Bucket vs Sliding Window).
- **Concurrency**: Fine-grained `ReentrantLock` with monotonic clock (`System.nanoTime()`) calculations.

#### Production-Ready Java Implementation

```java
import java.util.*;
import java.util.concurrent.ConcurrentLinkedQueue;
import java.util.concurrent.locks.ReentrantLock;

public class RateLimiterDemo {

    public interface RateLimiter {
        boolean allowRequest();
    }

    /**
     * Token Bucket Rate Limiter
     */
    public static class TokenBucketRateLimiter implements RateLimiter {
        private final long capacity;
        private final double refillTokensPerNano;
        private double availableTokens;
        private long lastRefillNanoTime;
        private final ReentrantLock lock = new ReentrantLock();

        public TokenBucketRateLimiter(long capacity, double tokensPerSecond) {
            this.capacity = capacity;
            this.refillTokensPerNano = tokensPerSecond / 1_000_000_000.0;
            this.availableTokens = capacity;
            this.lastRefillNanoTime = System.nanoTime();
        }

        @Override
        public boolean allowRequest() {
            lock.lock();
            try {
                refill();
                if (availableTokens >= 1.0) {
                    availableTokens -= 1.0;
                    return true;
                }
                return false;
            } finally {
                lock.unlock();
            }
        }

        private void refill() {
            long now = System.nanoTime();
            long elapsedNanos = now - lastRefillNanoTime;
            double tokensToAdd = elapsedNanos * refillTokensPerNano;
            this.availableTokens = Math.min(capacity, this.availableTokens + tokensToAdd);
            this.lastRefillNanoTime = now;
        }
    }

    /**
     * Sliding Window Log Rate Limiter
     */
    public static class SlidingWindowLogRateLimiter implements RateLimiter {
        private final int maxRequests;
        private final long windowNanos;
        private final Queue<Long> requestTimestamps = new ConcurrentLinkedQueue<>();
        private final ReentrantLock lock = new ReentrantLock();

        public SlidingWindowLogRateLimiter(int maxRequests, long windowMillis) {
            this.maxRequests = maxRequests;
            this.windowNanos = windowMillis * 1_000_000L;
        }

        @Override
        public boolean allowRequest() {
            lock.lock();
            try {
                long now = System.nanoTime();
                long boundary = now - windowNanos;

                while (!requestTimestamps.isEmpty() && requestTimestamps.peek() <= boundary) {
                    requestTimestamps.poll();
                }

                if (requestTimestamps.size() < maxRequests) {
                    requestTimestamps.add(now);
                    return true;
                }
                return false;
            } finally {
                lock.unlock();
            }
        }
    }
}
```

---

### 5.3 In-Memory Pub-Sub Broker

#### Problem Overview
Design a high-throughput, in-memory topic-based publish-subscribe broker (like Kafka / RabbitMQ):
- Multiple topics with broadcast to consumer groups.
- Independent offset tracking per consumer group.
- Asynchronous non-blocking message publishing and concurrent dispatching.

#### Core Domain Model & Design Patterns
- **Patterns**: `Observer` pattern, `Producer-Consumer` pattern using bounded `BlockingQueue`.
- **Concurrency**: `ConcurrentHashMap<String, Topic>` and atomic offsets via `AtomicLong`.

#### Production-Ready Java Implementation

```java
import java.util.*;
import java.util.concurrent.*;
import java.util.concurrent.atomic.AtomicLong;

public class PubSubBrokerDemo {

    public record Message(String messageId, String payload, Instant timestamp) {}

    public interface Subscriber {
        String getId();
        void onMessage(Message message);
    }

    public static class ConsumerGroup {
        private final String groupId;
        private final List<Subscriber> subscribers = new CopyOnWriteArrayList<>();
        private final AtomicLong offset = new AtomicLong(0);

        public ConsumerGroup(String groupId) { this.groupId = groupId; }
        public void addSubscriber(Subscriber sub) { subscribers.add(sub); }
        public List<Subscriber> getSubscribers() { return subscribers; }
        public AtomicLong getOffset() { return offset; }
        public String getGroupId() { return groupId; }
    }

    public static class Topic {
        private final String topicName;
        private final List<Message> messageLog = new CopyOnWriteArrayList<>();
        private final Map<String, ConsumerGroup> consumerGroups = new ConcurrentHashMap<>();
        private final ExecutorService dispatcherPool = Executors.newCachedThreadPool();

        public Topic(String name) { this.topicName = name; }

        public void registerConsumerGroup(ConsumerGroup group) {
            consumerGroups.put(group.getGroupId(), group);
        }

        public void publish(Message message) {
            messageLog.add(message);
            // Dispatch asynchronously to each registered consumer group
            for (ConsumerGroup group : consumerGroups.values()) {
                dispatcherPool.submit(() -> dispatchToGroup(group));
            }
        }

        private void dispatchToGroup(ConsumerGroup group) {
            while (true) {
                int currentOffset = (int) group.getOffset().get();
                if (currentOffset >= messageLog.size()) break;

                Message msg = messageLog.get(currentOffset);
                if (group.getOffset().compareAndSet(currentOffset, currentOffset + 1)) {
                    // Round-robin dispatch among group subscribers
                    List<Subscriber> subs = group.getSubscribers();
                    if (!subs.isEmpty()) {
                        Subscriber target = subs.get(currentOffset % subs.size());
                        target.onMessage(msg);
                    }
                }
            }
        }
    }
}
```

---

### 5.4 Logger Framework

#### Problem Overview
Design a flexible, high-performance logging framework (like Logback or Log4j2):
- Support multiple log levels (`DEBUG`, `INFO`, `WARN`, `ERROR`).
- **Chain of Responsibility**: Filter log events based on logger severity threshold.
- Multiple pluggable log sinks (Console, File, Remote Service).
- **Asynchronous Non-Blocking Logging**: Application threads enqueue log events into a bounded `BlockingQueue`, serviced by a dedicated daemon background flush worker thread.

#### Core Domain Model & Design Patterns
- **Patterns**: `Chain of Responsibility` for level filtering; `Producer-Consumer` pattern with background worker.

#### Production-Ready Java Implementation

```java
import java.time.Instant;
import java.util.*;
import java.util.concurrent.*;

public class LoggerFrameworkDemo {

    public enum LogLevel {
        DEBUG(1), INFO(2), WARN(3), ERROR(4);
        private final int severity;
        LogLevel(int severity) { this.severity = severity; }
        public boolean isApplicable(LogLevel incoming) { return incoming.severity >= this.severity; }
    }

    public record LogMessage(LogLevel level, String message, Instant timestamp, String threadName) {
        @Override
        public String toString() {
            return String.format("[%s] [%s] [%s] - %s", timestamp, threadName, level, message);
        }
    }

    public interface LogSink {
        void write(LogMessage logMessage);
    }

    public static class ConsoleSink implements LogSink {
        @Override public void write(LogMessage msg) { System.out.println(msg); }
    }

    public static class AsyncLoggerEngine {
        private final LogLevel minLevel;
        private final List<LogSink> sinks = new CopyOnWriteArrayList<>();
        private final BlockingQueue<LogMessage> buffer = new ArrayBlockingQueue<>(10_000);
        private final Thread workerThread;
        private volatile boolean running = true;

        public AsyncLoggerEngine(LogLevel minLevel) {
            this.minLevel = minLevel;
            this.workerThread = new Thread(this::processLogs, "AsyncLoggerWorker");
            this.workerThread.setDaemon(true);
            this.workerThread.start();
        }

        public void addSink(LogSink sink) { sinks.add(sink); }

        public void log(LogLevel level, String message) {
            if (!minLevel.isApplicable(level)) return;

            LogMessage msg = new LogMessage(level, message, Instant.now(), Thread.currentThread().getName());
            boolean accepted = buffer.offer(msg);
            if (!accepted) {
                System.err.println("Logger queue full! Dropping log message: " + message);
            }
        }

        private void processLogs() {
            while (running || !buffer.isEmpty()) {
                try {
                    LogMessage msg = buffer.poll(100, TimeUnit.MILLISECONDS);
                    if (msg != null) {
                        for (LogSink sink : sinks) {
                            sink.write(msg);
                        }
                    }
                } catch (InterruptedException e) {
                    Thread.currentThread().interrupt();
                    break;
                }
            }
        }

        public void shutdown() {
            this.running = false;
        }
    }
}
```

---

### 5.5 Delayed Job Scheduler

#### Problem Overview
Design an in-memory delayed task execution system:
- Schedule tasks to run after a specific delay or at a target wall-clock timestamp.
- High-efficiency time-ordered queueing without busy-waiting polling loops.
- Support task cancellation before execution.
- Multi-threaded worker pool to execute scheduled jobs concurrently upon expiry.

#### Core Domain Model & Design Patterns
- **Data Structure**: Java `DelayQueue` (internally backed by a Priority Queue ordered by remaining delay).
- **Concurrency**: `ScheduledExecutorService` or custom worker pool using `DelayQueue.take()` (which sleeps the worker thread until the earliest job is ready to fire).

#### Production-Ready Java Implementation

```java
import java.time.Duration;
import java.time.Instant;
import java.util.concurrent.*;
import java.util.concurrent.atomic.AtomicBoolean;

public class DelayedJobSchedulerDemo {

    public static class DelayedTask implements Delayed {
        private final String taskId;
        private final Runnable task;
        private final Instant scheduledTime;
        private final AtomicBoolean cancelled = new AtomicBoolean(false);

        public DelayedTask(String taskId, Runnable task, Instant scheduledTime) {
            this.taskId = taskId;
            this.task = task;
            this.scheduledTime = scheduledTime;
        }

        public boolean cancel() { return cancelled.compareAndSet(false, true); }
        public boolean isCancelled() { return cancelled.get(); }
        public Runnable getTask() { return task; }
        public String getTaskId() { return taskId; }

        @Override
        public long getDelay(TimeUnit unit) {
            long remainingMillis = Duration.between(Instant.now(), scheduledTime).toMillis();
            return unit.convert(remainingMillis, TimeUnit.MILLISECONDS);
        }

        @Override
        public int compareTo(Delayed other) {
            if (this == other) return 0;
            long diff = this.getDelay(TimeUnit.MILLISECONDS) - other.getDelay(TimeUnit.MILLISECONDS);
            return Long.compare(diff, 0L);
        }
    }

    public static class DelayedJobScheduler {
        private final DelayQueue<DelayedTask> delayQueue = new DelayQueue<>();
        private final ExecutorService workerPool;
        private final Thread dispatcherThread;
        private volatile boolean running = true;

        public DelayedJobScheduler(int workerPoolSize) {
            this.workerPool = Executors.newFixedThreadPool(workerPoolSize);
            this.dispatcherThread = new Thread(this::pollAndDispatch, "DelayedJobDispatcher");
            this.dispatcherThread.setDaemon(true);
            this.dispatcherThread.start();
        }

        public DelayedTask schedule(String taskId, Runnable task, Duration delay) {
            Instant executionTime = Instant.now().plus(delay);
            DelayedTask delayedTask = new DelayedTask(taskId, task, executionTime);
            delayQueue.put(delayedTask);
            return delayedTask;
        }

        private void pollAndDispatch() {
            while (running) {
                try {
                    // DelayQueue.take() blocks until an item's delay has expired
                    DelayedTask readyTask = delayQueue.take();
                    if (!readyTask.isCancelled()) {
                        workerPool.submit(readyTask.getTask());
                    }
                } catch (InterruptedException e) {
                    Thread.currentThread().interrupt();
                    break;
                }
            }
        }

        public void shutdown() {
            this.running = false;
            dispatcherThread.interrupt();
            workerPool.shutdown();
        }
    }
}
```
