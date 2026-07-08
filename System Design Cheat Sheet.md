# System Design Cheat Sheet

A dense, one-page reference for interviews and quick review. Print it. Keep it open during mock interviews.

---

## Numbers Every Engineer Must Know

### Latency Reference Table

| Operation | Latency |
|-----------|---------|
| L1 cache reference | 0.5 ns |
| Branch misprediction | 5 ns |
| L2 cache reference | 7 ns |
| Mutex lock/unlock | 25 ns |
| Main memory reference | 100 ns |
| Compress 1KB with Snappy | 3,000 ns = 3 µs |
| Send 2KB over 1 Gbps network | 20,000 ns = 20 µs |
| SSD random read | 150,000 ns = 150 µs |
| Read 1 MB sequentially from memory | 250,000 ns = 250 µs |
| Round trip within same data center | 500,000 ns = 0.5 ms |
| Read 1 MB sequentially from SSD | 1,000,000 ns = 1 ms |
| HDD disk seek | 10,000,000 ns = 10 ms |
| Read 1 MB sequentially from HDD | 20,000,000 ns = 20 ms |
| Send packet from CA to Netherlands and back | 150,000,000 ns = 150 ms |

**Key takeaways:**
- Memory is ~200x faster than SSD
- SSD is ~100x faster than HDD
- Network within a DC is fast (~0.5ms); cross-continent is slow (~150ms)
- Avoid disk seeks; favor sequential reads

---

### Storage Sizes

```
1 Byte    = 8 bits
1 KB      = 10^3 bytes  = 1,000 bytes
1 MB      = 10^6 bytes  = 1,000,000 bytes
1 GB      = 10^9 bytes  = 1,000,000,000 bytes
1 TB      = 10^12 bytes
1 PB      = 10^15 bytes

A tweet:           ~280 bytes of text
A photo (avg):     ~300 KB
A 1-min video:     ~50 MB (compressed)
A 1-hour video:    ~3 GB (compressed)
```

---

### Throughput and Traffic Estimates

```
1 million requests/day  =  ~12 requests/second
10 million req/day      =  ~115 req/sec
100 million req/day     =  ~1,150 req/sec (about 1K RPS)
1 billion req/day       =  ~11,500 req/sec (about 10K RPS)

Typical web server:      500 - 10,000 RPS (depends on work)
Typical DB server:       1,000 - 10,000 QPS (reads), 100-1,000 QPS (writes)
Kafka throughput:        100K - 1M messages/sec per broker
```

---

## Capacity Estimation Formulas

```
Daily Active Users (DAU) = Monthly Active Users * 0.5 (rule of thumb)

Requests Per Second (RPS):
  RPS = Total daily requests / 86,400 seconds
  Peak RPS ≈ Average RPS * 2-3x

Storage per year:
  Storage = RPS * avg_object_size * 86,400 * 365

Bandwidth (bytes/sec):
  Bandwidth = RPS * avg_response_size

Read/Write ratio:
  Assume 80/20 (80% reads, 20% writes) unless told otherwise

Replication factor:
  Total storage = raw storage * replication_factor (typically 3)
```

**Estimation template:**

```
Step 1: How many DAU?           e.g., 100 million
Step 2: How many actions/user/day? e.g., 10 posts
Step 3: Total daily requests    = 100M * 10 = 1 billion
Step 4: RPS                     = 1B / 86,400 ≈ 12,000 RPS
Step 5: Peak RPS                = 12,000 * 3 = 36,000 RPS
Step 6: Avg object size         e.g., 1 KB per post
Step 7: Daily storage           = 1B * 1KB = 1 TB/day
Step 8: 5-year storage          = 1 TB * 365 * 5 = ~1.8 PB
Step 9: With replication (3x)   = 1.8 PB * 3 = ~5.4 PB
```

---

## Common Architecture Patterns

| Pattern | Use When | Key Tradeoff |
|---------|----------|-------------|
| Monolith | Early stage, small team | Simple to deploy; hard to scale parts independently |
| Microservices | Different scaling needs per service | Independent deployability; operational complexity |
| Event-Driven | Decoupled async workflows | High throughput; harder to trace and debug |
| CQRS | Read and write workloads differ greatly | Optimized read/write models; eventual consistency |
| Event Sourcing | Full audit trail required | Complete history; complex state reconstruction |
| Saga (orchestration) | Multi-service distributed transactions | No 2PC; requires compensating transactions |
| Strangler Fig | Migrating from monolith to microservices | Safe incremental migration; temporary complexity |
| Cell-Based | Limit blast radius at scale | Fault isolation; higher infrastructure cost |
| Sidecar | Cross-cutting concerns per service (mTLS, metrics) | Consistent policy; added resource overhead |

---

## Database Selection Guide

| Database Type | Best For | Examples | Avoid When |
|---------------|----------|----------|------------|
| **Relational (SQL)** | ACID transactions, complex joins, structured data | PostgreSQL, MySQL, Aurora | Schema changes very frequently; extreme horizontal write scale needed |
| **Document** | Semi-structured data, flexible schema, nested objects | MongoDB, DynamoDB, Firestore | Complex multi-document transactions required |
| **Key-Value** | Caching, sessions, simple lookups by key | Redis, DynamoDB, etcd | Complex queries or relationships |
| **Wide-Column** | Time-series, high write throughput, sparse data | Cassandra, HBase, Bigtable | Complex queries, joins, ad-hoc analytics |
| **Graph** | Relationship-heavy queries, social networks, recommendations | Neo4j, Amazon Neptune | Simple lookup patterns, non-relationship data |
| **Time-Series** | Metrics, IoT, financial tick data | InfluxDB, TimescaleDB, Prometheus | General-purpose workloads |
| **Search** | Full-text search, faceting, relevance ranking | Elasticsearch, OpenSearch | Transactions, strong consistency needs |
| **In-Memory** | Sub-millisecond reads, caching, pub/sub, leaderboards | Redis, Memcached | Data too large for RAM, durability is critical |
| **NewSQL** | SQL semantics at distributed scale | CockroachDB, Spanner, YugabyteDB | Cost-sensitive small-scale systems |

---

## Caching Strategies

| Strategy | How It Works | When to Use | Downside |
|----------|-------------|-------------|----------|
| **Cache-Aside** (Lazy) | App checks cache; on miss, loads from DB and populates cache | General purpose | Cold start, cache staleness |
| **Read-Through** | Cache handles miss automatically, loads from DB | Transparent to app | More complex cache setup |
| **Write-Through** | Write goes to cache AND DB synchronously | Consistency required | Higher write latency |
| **Write-Back** | Write goes to cache; DB updated asynchronously | Write-heavy, latency sensitive | Risk of data loss on cache crash |
| **Write-Around** | Write goes directly to DB, bypassing cache | Infrequently-read data | Cache miss on first read |
| **Refresh-Ahead** | Cache pre-fetches data before TTL expires | Predictable access patterns | Wasted cache if data not accessed |

**Eviction Policies:**

| Policy | Evicts | Best For |
|--------|--------|---------|
| LRU | Least recently used | General workloads |
| LFU | Least frequently used | Popularity-skewed access |
| FIFO | Oldest item | Simple queue-like patterns |
| TTL | Expired items | Time-sensitive data |
| Random | Random item | Simpler, faster implementation |

---

## Load Balancing Algorithms

| Algorithm | How It Works | Best For |
|-----------|-------------|----------|
| Round Robin | Requests distributed sequentially | Homogeneous servers, stateless services |
| Weighted Round Robin | Servers get proportional share based on weight | Heterogeneous server capacities |
| Least Connections | Routes to server with fewest active connections | Long-lived connections (WebSockets) |
| Least Response Time | Routes to server with lowest latency + connections | Performance-sensitive traffic |
| IP Hash | Hashes client IP to pick server | Sticky sessions without cookies |
| Consistent Hashing | Hashes request key, minimizes remapping on changes | Distributed caches, stateful routing |
| Random (Power of Two) | Picks best of 2 random servers | Simple, effective at scale |

---

## CAP Theorem Quick Reference

```
         Consistency
              |
              |
    CA -------+------- CP
    (SQL)     |     (HBase, Zookeeper)
              |
    AP -------+
 (Cassandra, DynamoDB in eventual mode)
              |
          Partition
```

| System Type | Guarantee | Examples |
|-------------|-----------|---------|
| **CP** | Consistent + Partition tolerant | HBase, Zookeeper, etcd, MongoDB (w: majority) |
| **AP** | Available + Partition tolerant | Cassandra, DynamoDB, CouchDB, DNS |
| **CA** | Consistent + Available (no partition) | Traditional RDBMS (single-node) |

**In practice:** Partition tolerance is non-negotiable in distributed systems. The real choice is **CP vs AP** — consistency vs availability during a network partition.

---

## The Nines of Availability

| Availability | Downtime per Year | Downtime per Month | Downtime per Week |
|-------------|-------------------|-------------------|------------------|
| 90% (1 nine) | 36.5 days | 72 hours | 16.8 hours |
| 99% (2 nines) | 3.65 days | 7.2 hours | 1.68 hours |
| 99.9% (3 nines) | 8.76 hours | 43.8 minutes | 10.1 minutes |
| 99.99% (4 nines) | 52.6 minutes | 4.38 minutes | 1.01 minutes |
| 99.999% (5 nines) | 5.26 minutes | 26.3 seconds | 6.05 seconds |

---

## Common Bottlenecks and Fixes

| Bottleneck | Symptoms | Common Fixes |
|-----------|----------|-------------|
| Database reads | Slow queries, high DB CPU | Add read replicas, add indexes, add caching layer |
| Database writes | Write queue backing up, high latency | Sharding, async writes via queue, write-back caching |
| Single server CPU | High CPU utilization | Horizontal scaling, async processing, optimize code |
| Network I/O | High latency, packet loss | CDN for static content, reduce payload size, HTTP/2 |
| Disk I/O | Slow read/write, high wait time | SSD, more RAM (reduce disk access), async I/O |
| Memory | OOM errors, swapping | Increase RAM, fix memory leaks, evict unused data |
| Hot partition | One shard/cache key getting all traffic | Key salting, consistent hashing, read replicas for hot key |
| Synchronous dependencies | High p99 latency | Async decoupling with queue, circuit breaker, timeouts |
| N+1 queries | Too many DB calls per request | ORM eager loading, batch queries, caching |
| No caching | Cache hit rate 0%, DB hammered | Add Redis/Memcached, implement cache-aside |

---

## Rate Limiting Algorithms

| Algorithm | How It Works | Burst Handling | Memory |
|-----------|-------------|----------------|--------|
| **Fixed Window** | Count requests per fixed time window | Allows 2x burst at window boundary | Low |
| **Sliding Window Log** | Log each request timestamp, count in window | Accurate, no boundary burst | High |
| **Sliding Window Counter** | Blend of current and previous window | Approximate, low memory | Low |
| **Token Bucket** | Tokens added at fixed rate, spent per request | Allows bursts up to bucket size | Low |
| **Leaky Bucket** | Queue processed at fixed rate, overflow dropped | Smooth output, drops bursts | Medium |

---

## The 6-Step Interview Framework

```
Step 1: CLARIFY (5 min)
  - Ask: Who are the users? What is the scale?
  - Ask: What features are in scope?
  - Ask: What are the consistency/availability requirements?
  - Never start designing before this step.

Step 2: ESTIMATE (5 min)
  - DAU, RPS, storage per year
  - Read/write ratio
  - Use the estimation template above

Step 3: HIGH-LEVEL DESIGN (10 min)
  - Draw the major components: clients, servers, databases, caches, queues
  - Show data flow from left to right
  - Don't dive into details yet

Step 4: DEEP DIVE (15 min)
  - Interviewer usually picks 1-2 components to discuss deeply
  - Come prepared to deep dive on: data model, API design, bottlenecks
  - Proactively identify tradeoffs

Step 5: BOTTLENECKS AND SCALING (5 min)
  - What breaks at 10x scale? 100x scale?
  - Walk through each component and identify its limit
  - Propose solutions with explicit tradeoffs

Step 6: WRAP UP (5 min)
  - Summarize the design
  - Mention what you would improve given more time
  - Highlight key design decisions you made
```

---

## Estimation Shortcuts

```
Seconds in a day:     86,400  (~100K for rough math)
Seconds in a month:   2.6 million (~3M)
Seconds in a year:    31.5 million (~30M)

1 KB  = 10^3 bytes
1 MB  = 10^6 bytes  (about 1 photo)
1 GB  = 10^9 bytes  (about 3 hours of MP4 video)
1 TB  = 10^12 bytes (about 1,000 hours of video)

"A million users posting once a day" = 12 RPS average, 36 RPS peak
"A billion users posting once a day" = 12,000 RPS average, 36,000 RPS peak

Write-heavy system (e.g., logging): read:write = 1:1 or 1:2
Read-heavy system (e.g., Twitter timeline): read:write = 100:1

Cache hit rate target: >90% for most systems
p99 latency target: < 100ms for web APIs, < 10ms for internal services
```

---

## Common System Design Tradeoffs

| Decision | Option A | Option B | Choose A When | Choose B When |
|----------|----------|----------|---------------|---------------|
| Consistency vs Availability | Strong consistency | Eventual consistency | Banking, inventory, booking | Social feeds, DNS, caches |
| SQL vs NoSQL | SQL | NoSQL | Transactions, joins, structured | High write throughput, flexible schema, scale |
| Sync vs Async | Synchronous calls | Message queue | User needs immediate response | Decoupling, high throughput, background work |
| Push vs Pull | Server pushes updates | Client polls for updates | Real-time, low update frequency | Batch, irregular access patterns |
| Monolith vs Microservices | Monolith | Microservices | Early stage, small team | Different scaling needs, large team, mature domain |
| Normalization vs Denormalization | Normalized | Denormalized | Write-heavy, data integrity critical | Read-heavy, query performance critical |
| Horizontal vs Vertical scaling | Horizontal (more machines) | Vertical (bigger machine) | Stateless services, web tier | Databases, stateful services (initial) |

---

## API Design Quick Reference

```
REST VERBS
  GET    /users         -> list users         (idempotent, cacheable)
  GET    /users/123     -> get user 123       (idempotent, cacheable)
  POST   /users         -> create user        (not idempotent)
  PUT    /users/123     -> replace user 123   (idempotent)
  PATCH  /users/123     -> update user 123    (not necessarily idempotent)
  DELETE /users/123     -> delete user 123    (idempotent)

PAGINATION
  Offset:  GET /posts?offset=20&limit=10     (simple, drifts on live data)
  Cursor:  GET /posts?cursor=abc123&limit=10 (stable, no drift)

VERSIONING
  URL:     /api/v1/users
  Header:  Accept: application/vnd.api.v1+json

RATE LIMIT HEADERS
  X-RateLimit-Limit: 1000
  X-RateLimit-Remaining: 999
  X-RateLimit-Reset: 1609459200
  Retry-After: 60
```

---

*Keep this open during every practice interview. The numbers and frameworks should become instinctive.*
