# 🏛️ High-Level Design (HLD) & System Design

High-Level System Design rounds evaluate your ability to architect scalable, reliable, highly available, and fault-tolerant distributed systems under real-world traffic, latency, and data constraints.

> 📖 **Full Master Guide**: For comprehensive deep-dives, architectural diagrams, formulas, trade-offs, schemas, and case study solutions, see the **[HLD Distributed Systems Master Guide](./hld-guide.md)**.

---

## ⏱️ The 45-Minute System Design Interview Framework

A structured, methodical approach is essential for pacing an HLD interview:

```
00-05 min: Requirements Clarification (Functional & Non-Functional, SLAs)
05-10 min: Capacity Estimation (Traffic QPS, Bandwidth, 5-Year Storage, Cache RAM)
10-15 min: API Design & Data Model (Core Entities, Schemas, SQL vs. NoSQL)
15-25 min: High-Level Architecture (Client -> DNS -> CDN -> LB -> Microservices -> DB/Cache)
25-35 min: Deep Dive into Critical Components (Bottlenecks, Partitioning, Concurrency, Algorithms)
35-45 min: Scalability, Resilience, Failure Modes & Trade-offs (Saga, Circuit Breaker, Retries)
```

---

## 🏛️ The 7 Pillars of Distributed System Design

| # | Pillar | Focus & Key Concepts | Deep Dive |
|---|---|---|---|
| 1 | **Distributed Systems Fundamentals** | CAP & PACELC theorems, linearizability vs. eventual consistency, Quorum tunings ($R+W>N$), back-of-the-envelope estimation | [Section 1](./hld-guide.md#1-distributed-systems-fundamentals--trade-offs) |
| 2 | **Networking, APIs & Edge** | TCP vs. UDP, HTTP/1.1 vs. HTTP/2 vs. HTTP/3 (QUIC), REST vs. gRPC vs. GraphQL, WebSockets/SSE, Anycast DNS, L4 vs. L7 LB | [Section 2](./hld-guide.md#2-networking-apis--edge-infrastructure) |
| 3 | **Data Storage & Scaling** | SQL vs. NoSQL matrix, B+ Trees vs. LSM Trees & SSTables, Single/Multi-Leader & Leaderless replication, Range/Hash sharding | [Section 3](./hld-guide.md#3-data-storage-internals--database-scaling) |
| 4 | **Caching & Consistent Hashing** | Cache-Aside, Write-Through, Write-Behind, Cache Stampede/Penetration mitigations, Consistent Hashing rings with virtual nodes | [Section 4](./hld-guide.md#4-caching-consistent-hashing--performance) |
| 5 | **Messaging & Event Streaming** | Task Queues (RabbitMQ/SQS) vs. Append-only logs (Kafka), At-least-once with idempotent consumers, Backpressure, DLQs | [Section 5](./hld-guide.md#5-asynchronous-messaging--event-streaming) |
| 6 | **Coordination & Resilience** | Saga pattern (Orchestration/Choreography), Outbox + CDC, Snowflake 64-bit IDs, Circuit Breakers, Rate Limiters, Observability | [Section 6](./hld-guide.md#6-microservices-coordination-resilience--observability) |
| 7 | **Must-Practice System Archetypes** | Feeds (Twitter), Real-time Chat (WhatsApp), Location Dispatch (Uber), Video Streaming (Netflix), FinTech Ledgers | [Section 7](./hld-guide.md#7-must-practice-hld-system-archetypes) |

---

## 🌐 Classic System Design Interview Problems

| # | System | Key Architectural Challenges | Core Technologies & Patterns |
|---|---|---|---|
| 1 | **URL Shortener (TinyURL)** | Low-latency read/write, Base62 encoding, 64-bit ID generation | Redis, Base62, Snowflake ID, NoSQL / RDBMS |
| 2 | **Distributed Rate Limiter** | Synchronized state across clusters, microsecond latency | Redis (`INCR` with TTL, Lua scripts), Token Bucket |
| 3 | **Chat Application (WhatsApp / Slack)** | Bi-directional communication, presence detection, message ordering | WebSockets, Cassandra / HBase, Redis Pub/Sub, Kafka |
| 4 | **Video Streaming (Netflix / YouTube)** | Video transcoding DAGs, global edge streaming, adaptive bitrate | CDN, Chunked upload, HLS / DASH protocols, S3 |
| 5 | **Ride-Sharing (Uber / Lyft)** | Geospatial indexing, dynamic pricing, real-time driver dispatch | Google S2 / Uber H3, Redis GEO, WebSockets |
| 6 | **Flash Sale / Ticket Booking** | Massive burst traffic, inventory overselling prevention | Redis distributed locks, Kafka queue, optimistic locking |
| 7 | **Distributed ID Generator** | Unique, time-sortable 64-bit IDs without coordination | Twitter Snowflake (Timestamp + Node ID + Sequence) |
| 8 | **Web Crawler** | Politeness, deduplication, fault tolerance, massive URL frontier | Bloom Filters, Priority Queues, Host Queues, S3 |

---

## 📐 Standard Distributed Architecture Blueprint

```text
[ Client (Web/Mobile) ]
          │
          ▼
   [ Anycast DNS / Cloudflare CDN ] (Edge Caching, DDoS Protection)
          │
          ▼
   [ L4 Load Balancer (NLB) ] (TCP High-Throughput Routing)
          │
          ▼
   [ API Gateway / L7 LB ] (Envoy / Kong: Auth, Rate Limiting, SSL Termination)
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
