# Chapter 19: System Design Case Studies

This chapter presents 15+ complete, end-to-end system design case studies. Each document walks through the full design lifecycle: requirements gathering, capacity estimation, API design, architecture, database design, scaling strategy, and real-world context. These case studies are the most important reference material in this course — they synthesize every concept from the previous chapters into realistic, interview-ready designs.

---

## How to Use This Chapter

Each case study follows the same structure so you can compare approaches across systems:

1. **Problem Statement** — What are we building and why?
2. **Functional & Non-Functional Requirements** — What must the system do?
3. **Capacity Estimation** — Real numbers: storage, throughput, bandwidth
4. **API Design** — Key endpoints with request/response shapes
5. **High-Level Architecture** — Mermaid diagram of all major components
6. **Core Components Deep Dive** — How each piece works internally
7. **Database Design** — Schema, SQL vs NoSQL decision with justification
8. **Scaling Strategy** — From 1 user to 100 million users
9. **Key Bottlenecks and Solutions** — The hard problems and how to solve them
10. **Trade-offs Made** — What was sacrificed for what
11. **Real-World: How [Company] Does It** — Publicly known implementation details
12. **Interview Discussion Points** — Questions interviewers commonly ask

---

## Case Studies Index

| # | System | Core Challenge | Key Concepts |
|---|--------|---------------|--------------|
| 01 | [URL Shortener (TinyURL)](./01.%20URL%20Shortener%20-%20TinyURL.md) | Unique code generation, high read:write ratio | Base62 encoding, Redis, 301 vs 302 redirect |
| 02 | [Chat System (WhatsApp)](./02.%20WhatsApp%20-%20Chat%20System.md) | Real-time messaging, offline delivery, group chat | WebSockets, message queues, E2E encryption |
| 03 | [Photo Sharing (Instagram)](./03.%20Instagram%20-%20Photo%20Sharing.md) | Feed generation, media storage, celebrity problem | Fanout on write vs read, CDN, S3 |
| 04 | [Social Network Feed (Twitter)](./04.%20Twitter%20-%20Social%20Network%20Feed.md) | Tweet fanout, home timeline, trending topics | Precomputed timelines, Count-Min Sketch |
| 05 | [Video Streaming (Netflix)](./05.%20Netflix%20-%20Video%20Streaming.md) | Video encoding, CDN, adaptive bitrate | Transcoding pipeline, HLS/DASH, DRM |
| 06 | [Ride-Hailing (Uber)](./06.%20Uber%20-%20Ride%20Hailing.md) | Real-time location, matching, surge pricing | Geo-indexing, WebSockets, event-driven |
| 07 | [Web Search (Google)](./07.%20Google%20-%20Web%20Search.md) | Crawling, indexing, ranking, query latency | Inverted index, PageRank, MapReduce |
| 08 | [Key-Value Store](./08.%20Key%20Value%20Store.md) | Distributed storage, consistency, partitioning | Consistent hashing, LSM trees, quorum |
| 09 | [Distributed Message Queue (Kafka)](./09.%20Distributed%20Message%20Queue%20-%20Kafka.md) | High throughput, durability, consumer groups | Partitions, offsets, replication |
| 10 | [Rate Limiter](./10.%20Rate%20Limiter.md) | Token bucket vs leaky bucket, distributed state | Redis atomic ops, sliding window |
| 11 | [Notification System](./11.%20Notification%20System.md) | Fan-out, push/email/SMS, retry on failure | APNs/FCM, message queues, idempotency |
| 12 | [Cloud Storage (Dropbox)](./12.%20Dropbox%20-%20Cloud%20Storage.md) | Chunked upload, sync, deduplication | Block storage, delta sync, conflict resolution |
| 13 | [Distributed Cache (Redis)](./13.%20Distributed%20Cache%20-%20Redis.md) | Eviction policies, consistency, clustering | LRU/LFU, replication, cache invalidation |
| 14 | [Payment System](./14.%20Payment%20System.md) | Exactly-once processing, fraud detection | Idempotency keys, double-entry ledger |
| 15 | [Search Autocomplete](./15.%20Search%20Autocomplete.md) | Low-latency prefix lookup, ranking | Trie, Redis sorted sets, caching tiers |

---

## Recurring Themes Across Case Studies

### The Read:Write Imbalance
Almost every social system has vastly more reads than writes. Instagram, Twitter, and URL shorteners all exploit this by caching aggressively, precomputing results (feed generation), and accepting slight staleness in exchange for speed.

### The Celebrity Problem
Any system where a single entity can have millions of followers faces the "hot key" or "celebrity" problem. A celebrity's tweet, post, or action cannot be fanned out to all followers synchronously — it would overwhelm the system. The standard solution is a hybrid model: precompute for regular users, inject celebrity content at read time.

### SQL vs NoSQL Decision Framework
- **Use SQL** when: data has complex relationships, ACID transactions are required, schema is stable, team knows SQL well.
- **Use NoSQL (wide-column)** when: write throughput is massive, data model is denormalized by access pattern, horizontal scaling is required.
- **Use NoSQL (document)** when: schema varies per record, hierarchical data is common.
- **Use Redis** when: data fits in memory, low latency is critical, data is ephemeral or is a cache.

### The Storage Hierarchy
Every large system uses a tiered storage strategy: hot data in Redis (memory), warm data in a primary database (SSD), cold data in object storage like S3 (cheap, slow). Understanding which tier each data type belongs in is a key system design skill.

### CAP Theorem in Practice
No case study blindly picks "AP" or "CP" — it partitions by subsystem. A chat system can tolerate slightly stale "last seen" timestamps (AP) while message delivery must be at-least-once (CP-leaning). Granular consistency decisions lead to better designs than blanket choices.

---

## Recommended Study Order

If you are preparing for interviews, study in this order:

1. URL Shortener — simplest end-to-end system; builds vocabulary
2. Rate Limiter — algorithmic depth, distributed state
3. Key-Value Store — foundational; all other systems are built on top
4. Notification System — practical fan-out pattern
5. Chat System — real-time complexity
6. Instagram / Twitter — feed design is the canonical hard problem
7. Netflix — storage and streaming at scale
8. Uber — real-time geo systems
9. Web Search — the most complex; leave for last

---

*Each case study is self-contained. You do not need to read them in order.*
