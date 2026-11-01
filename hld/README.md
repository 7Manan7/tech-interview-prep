# 🏛️ High-Level Design (HLD) & System Design

High-Level System Design rounds evaluate your ability to design scalable, reliable, highly available, and fault-tolerant distributed architectures for large-scale production applications.

---

## ⏱️ The 45-Minute System Design Interview Framework

A structured conversation is key to acing HLD interviews. Avoid jumping directly into drawing architecture diagrams.

```
00-05 min: Requirements Clarification (Functional & Non-Functional)
05-10 min: Capacity Estimation (Traffic, Storage, Bandwidth, Memory)
10-15 min: API Design & Data Model (Core Entities, Schemas, SQL vs NoSQL)
15-25 min: High-Level Architecture (Client -> DNS -> CDN -> LB -> Services -> DB/Cache)
25-35 min: Deep Dive into Critical Components (Bottlenecks, Concurrency, Algorithms)
35-45 min: Scalability, Fault Tolerance, Failure Modes & Trade-offs
```

---

## 🧱 Core Distributed Systems Building Blocks

### 1. CAP Theorem & PACELC
- In the presence of a network **Partition (P)**, a distributed system must choose between **Consistency (C)** and **Availability (A)**.
- **PACELC extension:** If there is a Partition (P), how does the system choose between Availability (A) and Consistency (C); Else (E), how does it choose between Latency (L) and Consistency (C)?

### 2. Consistent Hashing
- Distributes requests across a dynamic pool of cache/DB nodes.
- Uses a virtual ring ($0$ to $2^{32}-1$) with virtual nodes to minimize data migration when nodes join or leave ($O(K/N)$ keys remapped).

### 3. Caching Strategies
- **Cache-Aside (Lazy Loading):** Application reads cache first; if miss, reads DB and updates cache.
- **Write-Through:** Application writes to cache; cache synchronously writes to DB.
- **Write-Back (Write-Behind):** Application writes to cache; cache asynchronously writes to DB in batches (high throughput, risk of data loss on crash).
- **Cache Invalidation:** TTL, explicit eviction on update, write-around.

### 4. Database Scaling & Partitioning
- **Vertical Scaling vs Horizontal Sharding:** Sharding by Hash, Range, or Directory-based.
- **Replication:** Single-leader (Master-Replica with read replicas), Multi-leader, Leaderless (Quorum read/write: $R + W > N$).
- **SQL vs NoSQL:**
  - *Relational (PostgreSQL, MySQL):* Structured schema, ACID compliance, complex joins.
  - *Document (MongoDB):* Hierarchical, schema-flexible data.
  - *Key-Value (Redis, DynamoDB):* Fast single-key reads/writes, session storage.
  - *Wide-Column (Cassandra):* Heavy write throughput, time-series, log ingestion.

### 5. Asynchronous Processing & Messaging
- **Message Queues (RabbitMQ):** Task queuing, worker queues, point-to-point.
- **Distributed Streaming Logs (Apache Kafka):** High-throughput, distributed event log with consumer groups, partitioned topics, and offset tracking.
- **Handling Idempotency:** Utilizing idempotency keys (`UUID` in header) to avoid duplicate payments or actions.

---

## 🌐 Classic System Design Interview Problems

| # | System | Key Architectural Challenges | Core Technologies & Patterns |
|---|---|---|---|
| 1 | **URL Shortener (TinyURL)** | Low latency read/write, base62 encoding vs token service, collision handling | Redis Cache, Base62, Distributed ID Generator, NoSQL / RDBMS |
| 2 | **Distributed Rate Limiter** | Synchronization across clusters, microsecond latency | Redis (`INCR` with TTL, Lua scripts), Token Bucket |
| 3 | **Chat Application (WhatsApp / Slack)** | Bi-directional communication, presence detection, offline message storage | WebSockets, Cassandra / HBase, Redis Pub/Sub, Kafka |
| 4 | **Video Streaming (Netflix / YouTube)** | Video transcoding, global low-latency playback, adaptive bitrate streaming | CDN, Chunked upload, HLS / DASH protocols, S3 / Object storage |
| 5 | **Ride Sharing (Uber / Lyft)** | Geospatial queries, dynamic pricing, real-time driver tracking | QuadTree, Google S2 / Uber H3 spatial index, WebSockets, Redis |
| 6 | **Flash Sale / Ticket Booking** | Massive burst traffic, inventory overselling prevention | Redis distributed locks, Kafka queue-based order placement, optimistic locking |
| 7 | **Distributed ID Generator** | Unique, time-sortable 64-bit IDs without coordination | Twitter Snowflake algorithm (Timestamp + Worker ID + Sequence) |
| 8 | **Web Crawler** | Politeness, deduplication, fault tolerance, massive URL frontier | Bloom Filters, Priority Queues, DFS/BFS with host-based queues, S3 |

---

## 📐 Standard Architecture Blueprint

```text
[ Client (Web/Mobile) ]
          │
          ▼
   [ DNS / Cloudflare CDN ]
          │
          ▼
   [ API Gateway / Load Balancer ] (Nginx / Envoy / AWS ALB)
          │
     ┌────┴────────────────────────┬──────────────────────┐
     ▼                             ▼                      ▼
[ Auth Service ]           [ Core Business API ]    [ Search Service ]
                                   │                      │
                  ┌────────────────┴───────────────┐      ▼
                  ▼                                ▼  [Elasticsearch]
           [ Redis Cache ]               [ Kafka Event Bus ]
                  │                                │
                  ▼                                ▼
     [ Primary SQL / NoSQL DB ]            [ Worker Services ]
                  │
                  ▼
         [ Read Replicas ]
```

