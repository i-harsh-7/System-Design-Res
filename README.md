# System Design: From Zero to Staff Engineer

A structured, self-paced curriculum that takes you from first principles to confidently designing large-scale distributed systems — and acing system design interviews at any level.

---

## Course Overview

System design is the practice of defining the architecture, components, modules, interfaces, and data flow for a system to satisfy given requirements. It is the skill that separates mid-level engineers from senior and staff engineers.

This course covers everything you need to know:

- How networks, servers, and databases work at a conceptual level
- How to scale systems from one user to one billion users
- The fundamental building blocks: caches, queues, load balancers, databases
- Distributed systems theory — consistency, consensus, replication
- Reliability patterns: circuit breakers, retries, failover
- Real-world architectural patterns: microservices, event sourcing, CQRS
- API design, security, observability, and performance tuning
- Cloud and infrastructure fundamentals
- Designing real systems from scratch (URL shorteners to YouTube)
- How to perform well in system design interviews

**Who this is for:**

- Software engineers preparing for interviews at product companies (FAANG, startups, mid-size)
- Engineers who want to grow from junior/mid-level to senior/staff
- Anyone who builds or maintains software and wants to understand the bigger picture
- Self-learners who prefer structured notes over scattered blog posts

---

## Prerequisites

- Curiosity and a willingness to think at scale
- Basic programming knowledge in any language
- No prior system design experience required — we start from zero

---

## Complete Chapter List

| # | Chapter | Description |
|---|---------|-------------|
| 01 | **Basics** | What system design is, why it matters, and the vocabulary used throughout the course |
| 02 | **Networking** | HTTP, DNS, TCP/UDP, proxies, CDNs, and how data moves across the internet |
| 03 | **Scalability** | Horizontal vs vertical scaling, stateless design, and how systems grow |
| 04 | **Databases** | SQL vs NoSQL, indexing, normalization, sharding, and replication |
| 05 | **Caching** | Cache strategies, eviction policies, Redis, and where caching fits in a stack |
| 06 | **Load Balancing** | Algorithms, health checks, Layer 4 vs Layer 7, and sticky sessions |
| 07 | **Storage** | Object storage, block storage, file systems, and distributed storage systems |
| 08 | **Distributed Systems** | CAP theorem, consistency models, distributed clocks, and coordination |
| 09 | **Message Queues** | Async communication, Kafka, RabbitMQ, pub/sub, and event-driven design |
| 10 | **Consistency and Consensus** | Strong vs eventual consistency, Paxos, Raft, and distributed transactions |
| 11 | **Reliability and Fault Tolerance** | Failure modes, redundancy, circuit breakers, retries, and chaos engineering |
| 12 | **Microservices** | Service decomposition, inter-service communication, service mesh, and tradeoffs |
| 13 | **API Design** | REST, GraphQL, gRPC, versioning, rate limiting, and API gateways |
| 14 | **Security** | Authentication, authorization, encryption, secrets management, and threat modeling |
| 15 | **Observability** | Logging, metrics, tracing, alerting, dashboards, and SLOs/SLAs |
| 16 | **Performance** | Profiling, bottleneck analysis, query optimization, and throughput tuning |
| 17 | **Cloud and Infrastructure** | Docker, Kubernetes, IaC, cloud providers, and deployment strategies |
| 18 | **Large Scale Architecture** | Designing systems at internet scale — multi-region, global distribution |
| 19 | **Case Studies** | Deep dives into real systems: Twitter, YouTube, Uber, WhatsApp, and more |
| 20 | **Interview Problems** | Structured practice problems with worked solutions and evaluation rubrics |

---

## Learning Order

Follow the numbered order. Each chapter builds on the one before it. The dependency chain is intentional:

```
01 Basics -> 02 Networking -> 03 Scalability -> 04 Databases
    -> 05 Caching -> 06 Load Balancing -> 07 Storage
    -> 08 Distributed Systems -> 09 Message Queues
    -> 10 Consistency and Consensus -> 11 Reliability
    -> 12 Microservices -> 13 API Design
    -> 14 Security -> 15 Observability -> 16 Performance
    -> 17 Cloud and Infrastructure -> 18 Large Scale Architecture
    -> 19 Case Studies -> 20 Interview Problems
```

If you have prior experience, you can skim chapters you know well — but read them at least quickly to make sure you have the vocabulary used in later chapters.

---

## Estimated Time per Chapter

| # | Chapter | Estimated Time | Difficulty |
|---|---------|---------------|------------|
| 01 | Basics | 2-3 hours | Beginner |
| 02 | Networking | 4-5 hours | Beginner |
| 03 | Scalability | 3-4 hours | Beginner |
| 04 | Databases | 5-6 hours | Beginner |
| 05 | Caching | 3-4 hours | Intermediate |
| 06 | Load Balancing | 3-4 hours | Intermediate |
| 07 | Storage | 3-4 hours | Intermediate |
| 08 | Distributed Systems | 5-7 hours | Intermediate |
| 09 | Message Queues | 4-5 hours | Intermediate |
| 10 | Consistency and Consensus | 5-7 hours | Advanced |
| 11 | Reliability and Fault Tolerance | 4-5 hours | Advanced |
| 12 | Microservices | 4-5 hours | Intermediate |
| 13 | API Design | 3-4 hours | Intermediate |
| 14 | Security | 4-5 hours | Intermediate |
| 15 | Observability | 3-4 hours | Intermediate |
| 16 | Performance | 4-5 hours | Advanced |
| 17 | Cloud and Infrastructure | 4-5 hours | Intermediate |
| 18 | Large Scale Architecture | 5-7 hours | Advanced |
| 19 | Case Studies | 6-8 hours | Advanced |
| 20 | Interview Problems | 8-10 hours | Advanced |

**Total estimated time: 80-110 hours** (roughly 3-4 months at 6-8 hours per week)

---

## Difficulty Levels

| Level | Meaning |
|-------|---------|
| **Beginner** | No prior system design knowledge required. Concepts are introduced from first principles. |
| **Intermediate** | Assumes familiarity with basics. Requires connecting multiple concepts together. |
| **Advanced** | Requires solid understanding of prior chapters. Involves nuance, tradeoffs, and depth. |

---

## How to Study Effectively

**Read actively, not passively.**
Do not just skim. After each section, close the notes and try to re-explain the concept in your own words. If you cannot, re-read it.

**Draw diagrams while you read.**
System design is inherently visual. Every time you encounter a new architecture, draw it by hand or in a tool like Excalidraw. The act of drawing forces you to understand the relationships between components.

**Re-explain concepts out loud.**
Teach the concept to an imaginary colleague, a rubber duck, or yourself in a mirror. If you stumble, you have found a gap. Go back and fill it.

**Practice interviewing regularly.**
Starting from Chapter 10, treat every case study as an interview problem. Set a timer for 45 minutes and try to design the system before reading the solution. Then compare your design to the notes.

**Take your own notes.**
The notes in this repo are comprehensive, but your own annotations and margin notes will stick better than anything written here. Use the Course Progress Tracker to add your personal notes alongside each topic.

**Build something small.**
For every major concept — caching, message queues, load balancing — find a way to use it in a small project. Understanding how Redis works in theory is different from debugging a cache miss at 2am.

**Review the Cheat Sheet before every practice session.**
The System Design Cheat Sheet is designed as a pre-interview warm-up. Read it before mock interviews to prime your memory.

---

## How to Use This Repo

```
System-Design-Notes/
├── README.md                      <- You are here. Start here.
├── Learning Roadmap.md            <- Visual phase-by-phase plan with Mermaid diagram
├── Course Progress Tracker.md     <- Checkbox tracker for every topic
├── Glossary.md                    <- 80+ terms defined and cross-referenced
├── Resources.md                   <- Curated books, courses, videos, and tools
├── System Design Cheat Sheet.md   <- Dense reference for interviews
├── 01. Basics/
├── 02. Networking/
├── ...
└── 20. Interview Problems/
```

**Recommended workflow:**

1. Open `Learning Roadmap.md` to understand where you are in the course
2. Read the chapter notes for your current chapter
3. Check off completed topics in `Course Progress Tracker.md`
4. Look up any unfamiliar terms in `Glossary.md`
5. Review `System Design Cheat Sheet.md` before practice sessions
6. Use `Resources.md` to go deeper on topics that interest you

---

*This course is a living document. Add your own notes, correct mistakes, and make it yours.*
