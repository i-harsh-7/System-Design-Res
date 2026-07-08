# Glossary

Alphabetically organized definitions for 80+ system design terms. Each entry includes a one-line definition and the chapter where it is covered in depth.

---

## A

**ABAC (Attribute-Based Access Control)**
An authorization model where access decisions are based on attributes of the user, resource, and environment rather than fixed roles.
*Covered in depth: Chapter 14 — Security*

**ACID**
A set of database transaction properties: Atomicity (all-or-nothing), Consistency (valid state before and after), Isolation (transactions don't interfere), Durability (committed data persists).
*Covered in depth: Chapter 4 — Databases*

**Anycast**
A network routing technique where the same IP address is announced from multiple locations and traffic is routed to the nearest one.
*Covered in depth: Chapter 2 — Networking*

**API Gateway**
A server that acts as the single entry point for client requests, routing them to appropriate backend services while handling cross-cutting concerns like authentication, rate limiting, and logging.
*Covered in depth: Chapter 13 — API Design*

**Availability**
The percentage of time a system is operational and accessible, expressed as uptime (e.g., 99.9% = ~8.7 hours downtime/year).
*Covered in depth: Chapter 11 — Reliability and Fault Tolerance*

**Auto-scaling**
The automatic adjustment of compute resources (up or down) in response to changing load.
*Covered in depth: Chapter 3 — Scalability*

---

## B

**Backpressure**
A flow control mechanism where a downstream consumer signals to an upstream producer to slow down when it cannot keep up.
*Covered in depth: Chapter 9 — Message Queues*

**BASE**
An alternative to ACID for distributed systems: Basically Available, Soft state, Eventually consistent.
*Covered in depth: Chapter 4 — Databases*

**Batch Processing**
Processing large volumes of data in groups (batches) rather than individually or in real-time.
*Covered in depth: Chapter 9 — Message Queues*

**BFF (Backend for Frontend)**
An API layer designed specifically for a particular client (e.g., mobile app vs web app) to avoid forcing all clients to use the same generic API.
*Covered in depth: Chapter 12 — Microservices*

**Block Storage**
Storage that exposes raw disk volumes, allowing the operating system to manage the filesystem; typically used by databases and virtual machines.
*Covered in depth: Chapter 7 — Storage*

**Blue-Green Deployment**
A release strategy that maintains two identical production environments (blue and green) and switches traffic between them for zero-downtime deployments.
*Covered in depth: Chapter 17 — Cloud and Infrastructure*

**Bulkhead Pattern**
An isolation pattern that partitions system resources so that a failure in one component does not cascade to others.
*Covered in depth: Chapter 11 — Reliability and Fault Tolerance*

---

## C

**CAP Theorem**
States that a distributed system can guarantee at most two of three properties: Consistency, Availability, and Partition tolerance.
*Covered in depth: Chapter 8 — Distributed Systems*

**Canary Deployment**
A release strategy that gradually rolls out a change to a small subset of users before expanding to the full user base.
*Covered in depth: Chapter 17 — Cloud and Infrastructure*

**CDN (Content Delivery Network)**
A geographically distributed network of servers that caches content close to end users to reduce latency and origin server load.
*Covered in depth: Chapter 2 — Networking*

**Cell-Based Architecture**
An architecture that divides the system into isolated, self-contained cells that each handle a subset of users, limiting blast radius during failures.
*Covered in depth: Chapter 18 — Large Scale Architecture*

**Circuit Breaker**
A fault tolerance pattern that detects failures in a downstream service and short-circuits calls to it for a period, preventing cascading failures.
*Covered in depth: Chapter 11 — Reliability and Fault Tolerance*

**Consistent Hashing**
A hashing technique where adding or removing nodes minimizes key remapping, used in distributed caches and databases to avoid full rebalancing.
*Covered in depth: Chapter 5 — Caching; Chapter 6 — Load Balancing*

**CORS (Cross-Origin Resource Sharing)**
A browser mechanism that controls which cross-origin requests are permitted, enforced via HTTP headers.
*Covered in depth: Chapter 13 — API Design*

**CQRS (Command Query Responsibility Segregation)**
An architectural pattern that separates the model used for writes (commands) from the model used for reads (queries).
*Covered in depth: Chapter 16 — Performance*

**CRDT (Conflict-free Replicated Data Type)**
A data structure that can be replicated across nodes and merged automatically without conflicts, enabling eventual consistency.
*Covered in depth: Chapter 10 — Consistency and Consensus*

**Cursor-Based Pagination**
A pagination technique that uses a pointer (cursor) to the last retrieved item instead of a numeric offset, avoiding drift issues on live datasets.
*Covered in depth: Chapter 13 — API Design*

---

## D

**Data Lake**
A centralized repository that stores large volumes of raw, unstructured, or semi-structured data in its native format until needed.
*Covered in depth: Chapter 7 — Storage*

**Data Warehouse**
A structured storage system optimized for analytical queries (OLAP), typically storing cleaned and transformed data.
*Covered in depth: Chapter 7 — Storage*

**Database Replication**
Copying data from one database node (primary) to one or more others (replicas) to improve availability and read throughput.
*Covered in depth: Chapter 4 — Databases*

**Database Sharding**
Horizontal partitioning of a database across multiple nodes, where each node stores a subset of the data.
*Covered in depth: Chapter 4 — Databases*

**DDoS (Distributed Denial of Service)**
An attack that floods a system with traffic from many sources to exhaust its resources and make it unavailable to legitimate users.
*Covered in depth: Chapter 14 — Security*

**Dead Letter Queue (DLQ)**
A queue that stores messages that could not be successfully processed, allowing inspection and reprocessing later.
*Covered in depth: Chapter 9 — Message Queues*

**DNS (Domain Name System)**
The internet's distributed directory that maps human-readable domain names to IP addresses.
*Covered in depth: Chapter 2 — Networking*

**Docker**
A platform for building, packaging, and running applications in isolated containers that include all their dependencies.
*Covered in depth: Chapter 17 — Cloud and Infrastructure*

**Durability**
The guarantee that committed data persists even after system failures; one of the ACID properties.
*Covered in depth: Chapter 4 — Databases*

---

## E

**Edge Computing**
Processing data close to where it is generated (the edge of the network) rather than in a centralized data center.
*Covered in depth: Chapter 18 — Large Scale Architecture*

**Erasure Coding**
A data protection technique that encodes data into fragments with redundancy, allowing recovery from partial failures using less storage than full replication.
*Covered in depth: Chapter 7 — Storage*

**Event Sourcing**
A pattern where application state is derived entirely from an append-only log of events, rather than stored directly.
*Covered in depth: Chapter 9 — Message Queues*

**Eventual Consistency**
A consistency model where, given enough time without new updates, all replicas will converge to the same value.
*Covered in depth: Chapter 8 — Distributed Systems; Chapter 10 — Consistency and Consensus*

**Exponential Backoff**
A retry strategy where the wait time between retries grows exponentially, reducing load on a struggling downstream system.
*Covered in depth: Chapter 11 — Reliability and Fault Tolerance*

---

## F

**Failover**
The automatic or manual switch from a failed component to a standby replacement.
*Covered in depth: Chapter 11 — Reliability and Fault Tolerance*

**Fan-out**
The pattern of distributing a single event or message to multiple downstream consumers or queues.
*Covered in depth: Chapter 9 — Message Queues; Chapter 19 — Case Studies*

**Fault Tolerance**
A system's ability to continue operating correctly in the presence of component failures.
*Covered in depth: Chapter 11 — Reliability and Fault Tolerance*

**Feature Flag**
A software mechanism to enable or disable features at runtime without deploying new code.
*Covered in depth: Chapter 17 — Cloud and Infrastructure*

**Federation**
Splitting a database or system by function so different services each own their own data store.
*Covered in depth: Chapter 18 — Large Scale Architecture*

---

## G

**Geo-Routing**
Routing user traffic to the nearest data center or region based on geographic location.
*Covered in depth: Chapter 18 — Large Scale Architecture*

**Gossip Protocol**
A peer-to-peer communication protocol where nodes periodically share state with random neighbors, achieving eventual propagation without a central coordinator.
*Covered in depth: Chapter 8 — Distributed Systems*

**gRPC**
A high-performance RPC framework from Google that uses Protocol Buffers for serialization and HTTP/2 for transport.
*Covered in depth: Chapter 13 — API Design*

**GraphQL**
A query language for APIs that allows clients to request exactly the data they need, reducing over-fetching and under-fetching.
*Covered in depth: Chapter 13 — API Design*

---

## H

**Horizontal Scaling (Scale Out)**
Adding more machines to a system to increase capacity, rather than upgrading a single machine.
*Covered in depth: Chapter 3 — Scalability*

**Hot Key Problem**
A situation in a distributed cache or database where a disproportionate amount of traffic targets a single key or partition.
*Covered in depth: Chapter 5 — Caching*

**HTTP/2**
An HTTP protocol revision that adds multiplexing, header compression, and server push over a single TCP connection.
*Covered in depth: Chapter 2 — Networking*

**HTTP/3**
The latest HTTP version that runs over QUIC (UDP-based) instead of TCP, reducing latency especially on unreliable networks.
*Covered in depth: Chapter 2 — Networking*

---

## I

**Idempotency**
A property where performing an operation multiple times produces the same result as performing it once; critical for safe retries.
*Covered in depth: Chapter 10 — Consistency and Consensus; Chapter 13 — API Design*

**Idempotency Key**
A client-generated unique key included with a request so the server can detect and ignore duplicate requests.
*Covered in depth: Chapter 10 — Consistency and Consensus*

**Immutable Infrastructure**
A deployment philosophy where servers are never modified after creation; updates are made by replacing them entirely.
*Covered in depth: Chapter 17 — Cloud and Infrastructure*

**Infrastructure as Code (IaC)**
Managing and provisioning infrastructure through machine-readable configuration files rather than manual processes.
*Covered in depth: Chapter 17 — Cloud and Infrastructure*

---

## J

**JWT (JSON Web Token)**
A compact, self-contained token format for transmitting claims between parties, commonly used for authentication.
*Covered in depth: Chapter 14 — Security*

---

## K

**Kafka**
A distributed event streaming platform designed for high-throughput, durable, ordered event logs; commonly used as a message bus.
*Covered in depth: Chapter 9 — Message Queues*

**Kubernetes (K8s)**
An open-source container orchestration system for automating deployment, scaling, and management of containerized applications.
*Covered in depth: Chapter 17 — Cloud and Infrastructure*

---

## L

**Lamport Timestamp**
A logical clock mechanism that assigns ordered sequence numbers to events across distributed systems without synchronized physical clocks.
*Covered in depth: Chapter 8 — Distributed Systems*

**Latency**
The time elapsed between a request being made and the response being received; typically measured in milliseconds.
*Covered in depth: Chapter 1 — Basics*

**Leader Election**
A distributed algorithm by which nodes agree on a single leader responsible for coordination tasks.
*Covered in depth: Chapter 8 — Distributed Systems*

**Leaky Bucket**
A rate limiting algorithm that smooths out bursty traffic by processing requests at a fixed rate, dropping excess.
*Covered in depth: Chapter 13 — API Design*

**Linearizability**
The strongest consistency guarantee: every operation appears to take effect atomically at some point between its start and end.
*Covered in depth: Chapter 10 — Consistency and Consensus*

**Load Balancer**
A component that distributes incoming traffic across multiple backend servers to improve throughput and availability.
*Covered in depth: Chapter 6 — Load Balancing*

**Log Compaction**
A Kafka feature that retains only the latest value for each key in a topic, reducing storage while preserving current state.
*Covered in depth: Chapter 9 — Message Queues*

---

## M

**Materialized View**
A pre-computed, stored query result that is updated when the underlying data changes, speeding up complex read queries.
*Covered in depth: Chapter 16 — Performance*

**Merkle Tree**
A tree of hash values where each parent node is the hash of its children, allowing efficient verification of data consistency across distributed nodes.
*Covered in depth: Chapter 8 — Distributed Systems*

**Message Queue**
A component that enables asynchronous communication by storing messages until consumers are ready to process them.
*Covered in depth: Chapter 9 — Message Queues*

**Microservices**
An architectural style that structures an application as a collection of small, independently deployable services, each owning its data.
*Covered in depth: Chapter 12 — Microservices*

**mTLS (Mutual TLS)**
An extension of TLS where both client and server authenticate each other with certificates; used in service-to-service communication.
*Covered in depth: Chapter 14 — Security*

---

## N

**NoSQL**
A broad category of databases that do not use the relational model; types include document, key-value, column-family, and graph.
*Covered in depth: Chapter 4 — Databases*

**N+1 Problem**
A database performance antipattern where fetching N related records triggers N additional queries instead of one batch query.
*Covered in depth: Chapter 4 — Databases; Chapter 16 — Performance*

---

## O

**OAuth 2.0**
An authorization framework that allows third-party applications to access resources on behalf of a user without sharing credentials.
*Covered in depth: Chapter 14 — Security*

**Object Storage**
A storage architecture that manages data as discrete objects (with metadata) in a flat namespace; exemplified by Amazon S3.
*Covered in depth: Chapter 7 — Storage*

**OpenTelemetry**
A vendor-neutral observability framework providing standard APIs, SDKs, and tools for collecting logs, metrics, and traces.
*Covered in depth: Chapter 15 — Observability*

**Outbox Pattern**
A pattern for reliably publishing events by writing them to a database outbox table transactionally with the business operation, then publishing from there.
*Covered in depth: Chapter 9 — Message Queues*

---

## P

**PACELC Theorem**
An extension of CAP that states: if a partition occurs, choose between Availability and Consistency; else, choose between Latency and Consistency.
*Covered in depth: Chapter 8 — Distributed Systems*

**Partitioning**
Dividing data across multiple nodes or storage units; horizontal partitioning (by row) is sharding; vertical partitioning (by column) splits tables.
*Covered in depth: Chapter 4 — Databases*

**Paxos**
A consensus algorithm that ensures distributed nodes agree on a value even when some nodes are unreachable.
*Covered in depth: Chapter 10 — Consistency and Consensus*

**Proxy (Forward Proxy)**
A server that sits between clients and the internet, forwarding requests on behalf of clients; used for caching, filtering, and anonymization.
*Covered in depth: Chapter 2 — Networking*

**Pub/Sub (Publish-Subscribe)**
A messaging pattern where producers publish messages to topics and consumers subscribe to receive them, decoupling publishers from subscribers.
*Covered in depth: Chapter 9 — Message Queues*

---

## Q

**Quorum**
A majority vote used in distributed systems to ensure consistency; a write quorum requires acknowledgment from a majority of replicas.
*Covered in depth: Chapter 8 — Distributed Systems*

---

## R

**Raft**
A consensus algorithm designed to be more understandable than Paxos, using leader election and log replication.
*Covered in depth: Chapter 10 — Consistency and Consensus*

**Rate Limiting**
Controlling how many requests a client can make in a given time window to protect system resources and ensure fair usage.
*Covered in depth: Chapter 13 — API Design*

**RBAC (Role-Based Access Control)**
An authorization model where permissions are assigned to roles and users are assigned to roles.
*Covered in depth: Chapter 14 — Security*

**Redis**
An open-source, in-memory data structure store used as a cache, message broker, and database.
*Covered in depth: Chapter 5 — Caching*

**Replication**
Copying data to multiple nodes for redundancy, availability, or read scaling.
*Covered in depth: Chapter 4 — Databases; Chapter 8 — Distributed Systems*

**REST (Representational State Transfer)**
An architectural style for distributed hypermedia systems based on stateless client-server communication over HTTP.
*Covered in depth: Chapter 13 — API Design*

**Reverse Proxy**
A server that sits in front of backend servers, forwarding client requests and returning responses; enables load balancing, caching, and SSL termination.
*Covered in depth: Chapter 2 — Networking*

**RPC (Remote Procedure Call)**
A protocol for executing code on a remote server as if it were a local function call.
*Covered in depth: Chapter 13 — API Design*

**RPO (Recovery Point Objective)**
The maximum amount of data loss acceptable after a disaster, measured in time.
*Covered in depth: Chapter 11 — Reliability and Fault Tolerance*

**RTO (Recovery Time Objective)**
The maximum acceptable time to restore a system after a disaster.
*Covered in depth: Chapter 11 — Reliability and Fault Tolerance*

---

## S

**Saga Pattern**
A distributed transaction pattern that coordinates a series of local transactions across services, using compensating transactions to handle failures.
*Covered in depth: Chapter 10 — Consistency and Consensus*

**Serverless**
A cloud execution model where the provider dynamically manages infrastructure; developers deploy functions that run on demand.
*Covered in depth: Chapter 17 — Cloud and Infrastructure*

**Service Discovery**
The mechanism by which services locate each other's network addresses dynamically, rather than using hard-coded configuration.
*Covered in depth: Chapter 12 — Microservices*

**Service Mesh**
An infrastructure layer that manages service-to-service communication, providing traffic management, security, and observability.
*Covered in depth: Chapter 12 — Microservices*

**Sidecar Pattern**
A deployment pattern where a helper container (sidecar) is co-deployed alongside a main service container to provide supporting features.
*Covered in depth: Chapter 12 — Microservices*

**Single Point of Failure (SPOF)**
A component whose failure causes the entire system to fail; eliminating SPOFs through redundancy improves availability.
*Covered in depth: Chapter 1 — Basics; Chapter 11 — Reliability and Fault Tolerance*

**SLA (Service Level Agreement)**
A formal contract between a service provider and customer specifying the minimum service standards (e.g., 99.9% uptime).
*Covered in depth: Chapter 11 — Reliability and Fault Tolerance*

**SLI (Service Level Indicator)**
A metric used to measure service performance (e.g., request error rate, latency p99).
*Covered in depth: Chapter 15 — Observability*

**SLO (Service Level Objective)**
An internal target for an SLI (e.g., p99 latency < 200ms), typically stricter than the SLA.
*Covered in depth: Chapter 15 — Observability*

**SQL**
A standardized language for managing relational databases, and by extension, the relational database paradigm itself.
*Covered in depth: Chapter 4 — Databases*

**SSO (Single Sign-On)**
An authentication scheme allowing users to log in once and access multiple related applications without re-authenticating.
*Covered in depth: Chapter 14 — Security*

**Strangler Fig Pattern**
A migration strategy where new functionality is built alongside the old system and gradually takes over, eventually replacing it.
*Covered in depth: Chapter 12 — Microservices*

**Strong Consistency**
A consistency model guaranteeing that all reads reflect the most recent write, regardless of which replica is queried.
*Covered in depth: Chapter 10 — Consistency and Consensus*

---

## T

**Terraform**
An open-source IaC tool that provisions and manages infrastructure across multiple cloud providers using declarative configuration.
*Covered in depth: Chapter 17 — Cloud and Infrastructure*

**Throughput**
The number of operations (requests, transactions, messages) a system can process per unit of time, typically measured in RPS or TPS.
*Covered in depth: Chapter 1 — Basics*

**TLS (Transport Layer Security)**
A cryptographic protocol that provides secure communication over a network by encrypting data in transit.
*Covered in depth: Chapter 14 — Security*

**Token Bucket**
A rate limiting algorithm that allows burst traffic up to a bucket size, refilling tokens at a steady rate.
*Covered in depth: Chapter 13 — API Design*

**Two-Phase Commit (2PC)**
A distributed transaction protocol where a coordinator asks all participants to prepare, then commits only if all agree.
*Covered in depth: Chapter 8 — Distributed Systems; Chapter 10 — Consistency and Consensus*

---

## U

**UUID (Universally Unique Identifier)**
A 128-bit identifier designed to be unique without central coordination, commonly used for distributed ID generation.
*Covered in depth: Chapter 18 — Large Scale Architecture*

---

## V

**Vector Clock**
A mechanism for tracking causality in distributed systems by maintaining a logical timestamp per node.
*Covered in depth: Chapter 8 — Distributed Systems*

**Vertical Scaling (Scale Up)**
Increasing the resources (CPU, RAM, disk) of a single machine to handle more load.
*Covered in depth: Chapter 3 — Scalability*

**VPC (Virtual Private Cloud)**
An isolated virtual network within a cloud provider where resources are deployed with controlled ingress and egress.
*Covered in depth: Chapter 17 — Cloud and Infrastructure*

---

## W

**WebSocket**
A full-duplex communication protocol over a single TCP connection, enabling real-time bidirectional messaging between client and server.
*Covered in depth: Chapter 2 — Networking*

**Write-Through Cache**
A caching strategy where every write updates both the cache and the backing store simultaneously.
*Covered in depth: Chapter 5 — Caching*

**Write-Back Cache**
A caching strategy where writes go to the cache first and are asynchronously flushed to the backing store later.
*Covered in depth: Chapter 5 — Caching*

---

## Z

**Zero Trust Architecture**
A security model that assumes no implicit trust inside or outside the network perimeter, requiring continuous verification for every request.
*Covered in depth: Chapter 14 — Security*

**Zookeeper**
A distributed coordination service providing leader election, distributed locks, and configuration management for distributed systems.
*Covered in depth: Chapter 8 — Distributed Systems*

---

*Total: 85 terms. If you encounter a term not listed here, look it up and add it — keeping this glossary is part of learning.*
