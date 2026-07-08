# Course Progress Tracker

Track your progress through every topic. Check off each item as you complete it. Use the Notes column to record your own observations, questions, or page references.

**How to use:** After reading a topic, close your notes and re-explain it out loud. Only check it off when you can explain it without reading.

---

**Overall Progress**

| Phase | Chapters | Status |
|-------|----------|--------|
| Phase 1: Foundations | 01-04 | |
| Phase 2: Core Infrastructure | 05-09 | |
| Phase 3: Distributed Systems | 10-13 | |
| Phase 4: Production Engineering | 14-17 | |
| Phase 5: Interview Ready | 18-20 | |

---

## Chapter 1: Basics

- [ ] What is System Design — and why it is a separate skill from coding | Notes:
- [ ] Functional requirements vs non-functional requirements | Notes:
- [ ] Latency, throughput, and availability as design goals | Notes:
- [ ] The tradeoff triangle: cost, speed, correctness | Notes:
- [ ] Back-of-envelope estimation — why and how | Notes:
- [ ] Estimation: users, requests per second, storage, bandwidth | Notes:
- [ ] Powers of two and time units every engineer should know | Notes:
- [ ] How to read and present a system design | Notes:
- [ ] Common vocabulary: components, services, APIs, clients, servers | Notes:
- [ ] Single points of failure and why they matter | Notes:

---

## Chapter 2: Networking

- [ ] How the internet works — a practical mental model | Notes:
- [ ] IP addresses, DNS, and domain resolution | Notes:
- [ ] TCP vs UDP — when to use each | Notes:
- [ ] HTTP/1.1 vs HTTP/2 vs HTTP/3 | Notes:
- [ ] HTTPS and TLS — what encryption means in transit | Notes:
- [ ] Request-response lifecycle end to end | Notes:
- [ ] Status codes and what they mean for system design | Notes:
- [ ] REST principles | Notes:
- [ ] WebSockets and long polling | Notes:
- [ ] Server-Sent Events (SSE) | Notes:
- [ ] CDN — what it is and how it reduces latency | Notes:
- [ ] Edge nodes and points of presence | Notes:
- [ ] Forward proxy vs reverse proxy | Notes:
- [ ] API gateway as a network boundary | Notes:
- [ ] DNS load balancing | Notes:
- [ ] Anycast routing | Notes:

---

## Chapter 3: Scalability

- [ ] Vertical scaling — adding more resources to one machine | Notes:
- [ ] Horizontal scaling — adding more machines | Notes:
- [ ] Why stateless servers are easier to scale | Notes:
- [ ] Session state — where to store it when servers are stateless | Notes:
- [ ] Read replicas — scaling reads separately from writes | Notes:
- [ ] The shared-nothing architecture | Notes:
- [ ] Auto-scaling — reacting to load dynamically | Notes:
- [ ] Capacity planning before auto-scaling | Notes:
- [ ] Bottleneck identification — finding the constraint | Notes:
- [ ] The 80/20 rule applied to performance optimization | Notes:
- [ ] How scalability and consistency interact | Notes:

---

## Chapter 4: Databases

- [ ] Relational databases — tables, rows, columns, and constraints | Notes:
- [ ] ACID properties — Atomicity, Consistency, Isolation, Durability | Notes:
- [ ] SQL fundamentals for system design | Notes:
- [ ] Indexing — how indexes speed up queries | Notes:
- [ ] Primary keys, foreign keys, and composite keys | Notes:
- [ ] Normalization and when to denormalize | Notes:
- [ ] NoSQL — the four main types (document, key-value, column, graph) | Notes:
- [ ] When to choose NoSQL over SQL | Notes:
- [ ] BASE properties — Basically Available, Soft state, Eventually consistent | Notes:
- [ ] Database replication — primary-replica model | Notes:
- [ ] Synchronous vs asynchronous replication | Notes:
- [ ] Database sharding — horizontal partitioning | Notes:
- [ ] Sharding strategies: range, hash, directory | Notes:
- [ ] The problems sharding introduces (cross-shard queries, rebalancing) | Notes:
- [ ] Read replicas vs sharding — different problems, different solutions | Notes:
- [ ] Connection pooling | Notes:
- [ ] N+1 query problem | Notes:
- [ ] When to use an in-memory database | Notes:

---

## Chapter 5: Caching

- [ ] What caching is and why it matters | Notes:
- [ ] Cache hit vs cache miss | Notes:
- [ ] Cache-aside (lazy loading) pattern | Notes:
- [ ] Write-through caching | Notes:
- [ ] Write-back (write-behind) caching | Notes:
- [ ] Read-through caching | Notes:
- [ ] Cache eviction policies: LRU, LFU, FIFO, TTL | Notes:
- [ ] Cache stampede and how to prevent it | Notes:
- [ ] Thundering herd problem | Notes:
- [ ] Redis — architecture and use cases | Notes:
- [ ] Memcached — when to prefer it over Redis | Notes:
- [ ] Distributed caching — consistent hashing for cache nodes | Notes:
- [ ] CDN as a cache layer | Notes:
- [ ] Application-level caching vs database query caching | Notes:
- [ ] Cache invalidation — the hard problem | Notes:
- [ ] Hot key problem in distributed caches | Notes:
- [ ] Local (in-process) cache vs remote cache tradeoffs | Notes:

---

## Chapter 6: Load Balancing

- [ ] What a load balancer does and why you need one | Notes:
- [ ] Layer 4 (transport layer) load balancing | Notes:
- [ ] Layer 7 (application layer) load balancing | Notes:
- [ ] Round robin algorithm | Notes:
- [ ] Weighted round robin | Notes:
- [ ] Least connections algorithm | Notes:
- [ ] IP hash / sticky sessions | Notes:
- [ ] Random with two choices | Notes:
- [ ] Consistent hashing for load balancing | Notes:
- [ ] Health checks — active vs passive | Notes:
- [ ] SSL termination at the load balancer | Notes:
- [ ] Global load balancing and geo-routing | Notes:
- [ ] Load balancer as a single point of failure — how to avoid | Notes:
- [ ] Hardware vs software load balancers | Notes:
- [ ] Nginx, HAProxy, AWS ELB/ALB — practical differences | Notes:

---

## Chapter 7: Storage

- [ ] Block storage — raw volume, used by databases and VMs | Notes:
- [ ] File storage — hierarchical, NAS/NFS | Notes:
- [ ] Object storage — flat namespace, S3-style | Notes:
- [ ] When to use object storage vs file storage vs block storage | Notes:
- [ ] Amazon S3 and compatible APIs | Notes:
- [ ] HDFS — Hadoop Distributed File System | Notes:
- [ ] Replication factor in distributed storage | Notes:
- [ ] Erasure coding vs replication | Notes:
- [ ] Content-addressable storage | Notes:
- [ ] Blob storage and large file handling | Notes:
- [ ] Chunking large files for upload and storage | Notes:
- [ ] Data lake vs data warehouse | Notes:
- [ ] Cold vs warm vs hot storage tiers | Notes:
- [ ] Storage cost estimation | Notes:

---

## Chapter 8: Distributed Systems

- [ ] Why distributed systems are hard | Notes:
- [ ] The eight fallacies of distributed computing | Notes:
- [ ] CAP theorem — Consistency, Availability, Partition tolerance | Notes:
- [ ] CP vs AP systems — examples of each | Notes:
- [ ] PACELC theorem — extending CAP | Notes:
- [ ] Consistency models: strong, sequential, causal, eventual | Notes:
- [ ] Linearizability explained | Notes:
- [ ] Happens-before relationships | Notes:
- [ ] Lamport timestamps | Notes:
- [ ] Vector clocks | Notes:
- [ ] Physical clocks vs logical clocks | Notes:
- [ ] Distributed consensus — the problem statement | Notes:
- [ ] Leader election | Notes:
- [ ] Split-brain problem | Notes:
- [ ] Quorum — majority reads and writes | Notes:
- [ ] Gossip protocol | Notes:
- [ ] Merkle trees and anti-entropy | Notes:
- [ ] Two-phase commit (2PC) | Notes:
- [ ] Three-phase commit (3PC) | Notes:

---

## Chapter 9: Message Queues

- [ ] Why asynchronous communication matters | Notes:
- [ ] Message queue vs message broker vs event bus | Notes:
- [ ] Producer, consumer, and broker model | Notes:
- [ ] Point-to-point queuing vs publish-subscribe | Notes:
- [ ] At-most-once, at-least-once, exactly-once delivery semantics | Notes:
- [ ] Message ordering guarantees | Notes:
- [ ] Dead letter queues | Notes:
- [ ] RabbitMQ — AMQP, exchanges, queues, bindings | Notes:
- [ ] Kafka — topics, partitions, consumer groups, offsets | Notes:
- [ ] Kafka retention and log compaction | Notes:
- [ ] Consumer group rebalancing | Notes:
- [ ] Backpressure and flow control | Notes:
- [ ] Event-driven architecture | Notes:
- [ ] Event sourcing — storing state as events | Notes:
- [ ] Outbox pattern for reliable event publishing | Notes:
- [ ] Fan-out patterns | Notes:
- [ ] Queue vs stream — when to use which | Notes:

---

## Chapter 10: Consistency and Consensus

- [ ] Why consistency is a spectrum, not a binary | Notes:
- [ ] Strong consistency and its cost | Notes:
- [ ] Eventual consistency and convergence | Notes:
- [ ] Read-your-own-writes consistency | Notes:
- [ ] Monotonic reads | Notes:
- [ ] Consistent prefix reads | Notes:
- [ ] The consensus problem definition | Notes:
- [ ] Paxos — intuition and phases | Notes:
- [ ] Multi-Paxos | Notes:
- [ ] Raft — leader election, log replication, safety | Notes:
- [ ] Raft vs Paxos — practical differences | Notes:
- [ ] Distributed transactions | Notes:
- [ ] Two-phase commit — guarantees and failure modes | Notes:
- [ ] Saga pattern — choreography vs orchestration | Notes:
- [ ] Compensating transactions | Notes:
- [ ] Idempotency keys | Notes:
- [ ] CRDTs — Conflict-free Replicated Data Types | Notes:
- [ ] Operational transformation | Notes:

---

## Chapter 11: Reliability and Fault Tolerance

- [ ] Reliability vs availability vs durability | Notes:
- [ ] SLI, SLO, and SLA — definitions and differences | Notes:
- [ ] The nines of availability (99.9%, 99.99%, 99.999%) | Notes:
- [ ] Failure modes: crash, omission, Byzantine | Notes:
- [ ] Single points of failure — identification and elimination | Notes:
- [ ] Redundancy strategies: active-active, active-passive | Notes:
- [ ] Failover — automatic and manual | Notes:
- [ ] Graceful degradation | Notes:
- [ ] Circuit breaker pattern | Notes:
- [ ] Retry with exponential backoff and jitter | Notes:
- [ ] Bulkhead pattern | Notes:
- [ ] Timeout strategies | Notes:
- [ ] Rate limiting as a reliability tool | Notes:
- [ ] Chaos engineering — deliberately injecting failures | Notes:
- [ ] Game day exercises | Notes:
- [ ] Disaster recovery — RTO and RPO | Notes:
- [ ] Backup strategies | Notes:
- [ ] Multi-region failover | Notes:

---

## Chapter 12: Microservices

- [ ] Monolith vs microservices — honest tradeoffs | Notes:
- [ ] When to start with a monolith | Notes:
- [ ] Domain-Driven Design (DDD) basics | Notes:
- [ ] Bounded contexts | Notes:
- [ ] Service decomposition strategies | Notes:
- [ ] Inter-service communication: synchronous vs asynchronous | Notes:
- [ ] gRPC for service-to-service communication | Notes:
- [ ] Service discovery — client-side vs server-side | Notes:
- [ ] Service registry (Consul, Eureka, etcd) | Notes:
- [ ] API gateway pattern | Notes:
- [ ] Backend for Frontend (BFF) pattern | Notes:
- [ ] Service mesh — what it is and what it does | Notes:
- [ ] Sidecar proxy pattern | Notes:
- [ ] Istio and Envoy basics | Notes:
- [ ] Distributed tracing across services | Notes:
- [ ] Data ownership in microservices | Notes:
- [ ] Avoiding distributed monolith antipattern | Notes:
- [ ] Strangler Fig pattern for migration | Notes:

---

## Chapter 13: API Design

- [ ] REST principles and constraints | Notes:
- [ ] RESTful resource naming conventions | Notes:
- [ ] HTTP verbs and idempotency | Notes:
- [ ] HTTP status codes used correctly | Notes:
- [ ] Pagination: offset, cursor, keyset | Notes:
- [ ] Filtering, sorting, and searching in REST APIs | Notes:
- [ ] API versioning strategies | Notes:
- [ ] GraphQL — queries, mutations, subscriptions | Notes:
- [ ] GraphQL tradeoffs vs REST | Notes:
- [ ] gRPC — protocol buffers, streaming | Notes:
- [ ] gRPC vs REST performance | Notes:
- [ ] Rate limiting — token bucket, leaky bucket, sliding window | Notes:
- [ ] API throttling and quotas | Notes:
- [ ] API keys vs OAuth vs JWT | Notes:
- [ ] CORS and why it exists | Notes:
- [ ] API gateway responsibilities | Notes:
- [ ] Backward compatibility and deprecation | Notes:
- [ ] Webhooks and event callbacks | Notes:

---

## Chapter 14: Security

- [ ] Authentication vs authorization | Notes:
- [ ] Session-based authentication | Notes:
- [ ] Token-based authentication — JWT structure and validation | Notes:
- [ ] OAuth 2.0 flows — authorization code, client credentials | Notes:
- [ ] OpenID Connect | Notes:
- [ ] Single Sign-On (SSO) | Notes:
- [ ] Role-Based Access Control (RBAC) | Notes:
- [ ] Attribute-Based Access Control (ABAC) | Notes:
- [ ] TLS — certificates, handshake, mutual TLS (mTLS) | Notes:
- [ ] Encryption at rest vs in transit | Notes:
- [ ] Secrets management — environment variables, vaults, rotation | Notes:
- [ ] HashiCorp Vault basics | Notes:
- [ ] OWASP Top 10 applied to system design | Notes:
- [ ] SQL injection and parameterized queries | Notes:
- [ ] CSRF and XSS mitigations | Notes:
- [ ] DDoS mitigation strategies | Notes:
- [ ] Defense in depth | Notes:
- [ ] Zero trust architecture | Notes:
- [ ] Threat modeling framework | Notes:

---

## Chapter 15: Observability

- [ ] The three pillars: logs, metrics, traces | Notes:
- [ ] Structured logging vs unstructured logging | Notes:
- [ ] Log levels and when to use each | Notes:
- [ ] Centralized log aggregation (ELK, Loki) | Notes:
- [ ] Metrics — counters, gauges, histograms, summaries | Notes:
- [ ] Prometheus data model and PromQL basics | Notes:
- [ ] Grafana dashboards | Notes:
- [ ] The RED method (Rate, Errors, Duration) | Notes:
- [ ] The USE method (Utilization, Saturation, Errors) | Notes:
- [ ] Distributed tracing — trace ID, span, parent span | Notes:
- [ ] OpenTelemetry standard | Notes:
- [ ] Jaeger and Zipkin | Notes:
- [ ] Alerting — on symptoms, not causes | Notes:
- [ ] On-call rotation and runbooks | Notes:
- [ ] SLO-based alerting | Notes:
- [ ] Error budgets | Notes:
- [ ] Health check endpoints | Notes:
- [ ] Synthetic monitoring | Notes:

---

## Chapter 16: Performance

- [ ] Defining performance: latency vs throughput vs concurrency | Notes:
- [ ] Profiling — finding the real bottleneck | Notes:
- [ ] Amdahl's Law — limits of parallelization | Notes:
- [ ] Database query optimization | Notes:
- [ ] Slow query logs and EXPLAIN plans | Notes:
- [ ] Index selection for write-heavy vs read-heavy workloads | Notes:
- [ ] Connection pooling configuration | Notes:
- [ ] N+1 query problem detection and fix | Notes:
- [ ] Asynchronous I/O and non-blocking operations | Notes:
- [ ] Thread pools vs event loop models | Notes:
- [ ] Payload compression (gzip, Brotli) | Notes:
- [ ] Efficient serialization (Protocol Buffers vs JSON) | Notes:
- [ ] HTTP/2 multiplexing benefits | Notes:
- [ ] Database denormalization for read performance | Notes:
- [ ] Read replicas for query offloading | Notes:
- [ ] CQRS — separating read and write models | Notes:
- [ ] Materialized views | Notes:
- [ ] Background job processing | Notes:

---

## Chapter 17: Cloud and Infrastructure

- [ ] Containers — what Docker provides | Notes:
- [ ] Container images and layers | Notes:
- [ ] Container orchestration — what Kubernetes solves | Notes:
- [ ] Kubernetes concepts: Pod, Deployment, Service, Ingress | Notes:
- [ ] Horizontal Pod Autoscaler | Notes:
- [ ] Infrastructure as Code — Terraform basics | Notes:
- [ ] Immutable infrastructure | Notes:
- [ ] CI/CD pipeline stages | Notes:
- [ ] Blue-green deployment | Notes:
- [ ] Canary deployment | Notes:
- [ ] Feature flags | Notes:
- [ ] Cloud provider services overview (compute, storage, DB, messaging) | Notes:
- [ ] Managed services vs self-hosted tradeoffs | Notes:
- [ ] Serverless functions — use cases and cold start | Notes:
- [ ] VPC, subnets, security groups | Notes:
- [ ] Multi-AZ vs multi-region deployment | Notes:
- [ ] Cloud cost optimization basics | Notes:

---

## Chapter 18: Large Scale Architecture

- [ ] Designing for internet scale — what changes at 100M users | Notes:
- [ ] Multi-region architecture | Notes:
- [ ] Active-active vs active-passive multi-region | Notes:
- [ ] Geo-routing and latency-based routing | Notes:
- [ ] Data residency and sovereignty requirements | Notes:
- [ ] Global CDN architecture | Notes:
- [ ] Distributed ID generation (Snowflake, UUIDs) | Notes:
- [ ] Global database patterns: CockroachDB, Spanner | Notes:
- [ ] Federated architecture | Notes:
- [ ] Cell-based architecture | Notes:
- [ ] Traffic shaping and global load shedding | Notes:
- [ ] Dark launches and traffic shadowing | Notes:
- [ ] The fallback hierarchy | Notes:

---

## Chapter 19: Case Studies

- [ ] Twitter / X — tweet fanout, timelines, search | Notes:
- [ ] YouTube — video upload, processing, streaming, recommendations | Notes:
- [ ] Uber / Lyft — matching, location, real-time dispatch | Notes:
- [ ] WhatsApp — messaging, group chats, delivery receipts | Notes:
- [ ] Google Search — crawling, indexing, ranking | Notes:
- [ ] Netflix — content delivery, recommendation, streaming | Notes:
- [ ] Dropbox / Google Drive — file sync, conflict resolution | Notes:
- [ ] Airbnb — search, booking, availability, payments | Notes:
- [ ] Slack — real-time messaging, channels, notifications | Notes:
- [ ] Amazon / E-commerce — catalog, cart, inventory, checkout | Notes:

---

## Chapter 20: Interview Problems

- [ ] The 6-step interview framework | Notes:
- [ ] How to clarify requirements (questions to ask) | Notes:
- [ ] How to estimate capacity | Notes:
- [ ] How to structure a 45-minute design session | Notes:
- [ ] Common mistakes candidates make | Notes:
- [ ] Design a URL shortener | Notes:
- [ ] Design a web crawler | Notes:
- [ ] Design a search autocomplete | Notes:
- [ ] Design a notification system | Notes:
- [ ] Design a rate limiter | Notes:
- [ ] Design a distributed cache | Notes:
- [ ] Design a unique ID generator | Notes:
- [ ] Design a key-value store | Notes:
- [ ] Design a news feed | Notes:
- [ ] Design a chat system | Notes:
- [ ] Design a ride-sharing service | Notes:
- [ ] Design a video streaming service | Notes:
- [ ] Design a payment system | Notes:
- [ ] Design a distributed message queue | Notes:
- [ ] Design a collaborative document editor | Notes:

---

## Personal Milestones

Use this section to record your own progress checkpoints.

- [ ] Completed Phase 1 — can design a basic scalable web app | Date:
- [ ] Completed Phase 2 — can design with caching, queues, and storage | Date:
- [ ] Completed Phase 3 — comfortable with distributed systems theory | Date:
- [ ] Completed Phase 4 — can reason about production-grade systems | Date:
- [ ] Completed Phase 5 — interview ready | Date:
- [ ] Completed first mock interview | Date:
- [ ] Completed 5 mock interviews | Date:
- [ ] Passed a real system design interview | Date:
