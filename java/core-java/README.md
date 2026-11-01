# ☕ Core Java & Collections Internals

This section covers core language mechanics, collection framework internals, memory behaviors, and modern Java features.

---

## 🗄️ 1. `HashMap` Deep Dive (Java 8+)

### Internal Architecture
- **Data Structure:** Array of `Node<K, V>` (Buckets), backed by singly linked lists and Red-Black Trees (`TreeNode<K, V>`).
- **Initial Capacity:** Default 16 (always a power of 2).
- **Load Factor:** Default 0.75 ($16 \times 0.75 = 12$ threshold before resizing).

### How `put(K key, V value)` Works
1. Compute hash using high-order spreading:
   ```java
   static final int hash(Object key) {
       int h;
       return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
   }
   ```
2. Determine bucket index: `index = (capacity - 1) & hash`.
3. If bucket is empty: insert new `Node`.
4. If collision occurs:
   - If key equals existing node's key: overwrite value.
   - Else if node is instance of `TreeNode`: insert into Red-Black Tree ($O(\log k)$).
   - Else traverse linked list: if list length reaches **8** (`TREEIFY_THRESHOLD`) and capacity $\ge 64$, convert linked list to Red-Black Tree.
5. If `size > threshold`: double table capacity ($2 \times capacity$) and rehash nodes.

### Java 7 vs Java 8+
- Java 7 used entry arrays with linked lists only ($O(n)$ worst-case collision lookup). Java 8+ converts buckets with $\ge 8$ nodes into self-balancing Red-Black trees ($O(\log n)$ worst-case).

---

## 🛡️ 2. `ConcurrentHashMap` (Java 8+)

### Why Not `Collections.synchronizedMap()` or `Hashtable`?
- `Hashtable` synchronizes every method with a single object-level lock, creating an extreme bottleneck for concurrent reads and writes.

### Java 8 `ConcurrentHashMap` Design
- **Lock-Free Reads:** `get()` calls are non-blocking and require no locks because nodes use `volatile V val` and `volatile Node<K,V> next`.
- **Fine-Grained Bucket Locking:**
  - For empty buckets: Insertion is performed lock-free using **CAS** (`compareAndSet`).
  - For occupied buckets: Synchronizes **only on the head node** of the specific bucket being updated (`synchronized (firstNode)`).
- **Concurrent Resizing:** Worker threads assist in transferring chunks of buckets to the new table during resizing.

---

## 🏎️ 3. `ArrayList` vs `LinkedList`

| Characteristic | `ArrayList` | `LinkedList` |
|---|---|---|
| **Underlying Structure** | Resizable dynamic array | Doubly-linked list (`Node` objects) |
| **Random Access (`get(i)`)** | $O(1)$ directly by index | $O(n)$ traversal required |
| **Cache Locality** | **High** (elements stored contiguously in memory) | **Poor** (nodes scattered in heap, CPU cache misses) |
| **Memory Overhead** | Small (empty slots in backing array) | Large (every node allocates `prev`, `next`, and `item` references) |
| **Resizing Mechanism** | Increases by $1.5\times$ ($oldCapacity + (oldCapacity >> 1)$) | No resizing; allocates node per element |

> [!TIP]
> In production and modern hardware, `ArrayList` is almost always preferred over `LinkedList`, even for insertions, due to CPU cache-line prefetching and lower memory overhead.

---

## 🧩 4. Generics: PECS (Producer Extends, Consumer Super)

When designing reusable generic APIs:
- **Producer Extends:** If your method reads values out of a collection, use `? extends T`:
  ```java
  public void readAll(List<? extends Number> numbers) {
      for (Number n : numbers) {
          System.out.println(n.doubleValue());
      }
      // numbers.add(10); // Compile Error!
  }
  ```
- **Consumer Super:** If your method writes values into a collection, use `? super T`:
  ```java
  public void addIntegers(List<? super Integer> list) {
      list.add(1);
      list.add(2);
  }
  ```

---

## 🆕 5. Modern Java Innovations (Java 17 & Java 21)

### Records (Java 14+)
Concise immutable data carriers that automatically generate constructor, getters, `equals()`, `hashCode()`, and `toString()`:
```java
public record UserDTO(Long id, String name, String email) {}
```

### Sealed Classes (Java 17+)
Explicitly restrict which classes or interfaces may extend or implement them:
```java
public sealed interface PaymentMethod permits CreditCard, Upi, NetBanking {}

public final class CreditCard implements PaymentMethod {}
public final class Upi implements PaymentMethod {}
public final class NetBanking implements PaymentMethod {}
```

### Pattern Matching for `switch` (Java 21+)
```java
static String formatPayment(PaymentMethod p) {
    return switch (p) {
        case CreditCard c -> "Card payment: " + c;
        case Upi u        -> "UPI payment: " + u;
        case NetBanking n -> "Net banking: " + n;
    };
}
```

