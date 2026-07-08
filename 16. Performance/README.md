# Chapter 16: Performance

## Why This Chapter Exists

You can design a system that is correct, scalable, and fault-tolerant — and still have users complain it is slow. Performance is the chapter that bridges the gap between "the system works" and "the system feels fast." Every engineering decision you make has a performance cost or benefit. The goal of this chapter is to give you the mental models, vocabulary, and techniques to reason about performance systematically rather than by guessing.

Performance problems are sneaky. They often do not appear during development because your test data is small. They show up in production at 3 AM when you have 10,000 concurrent users. This chapter teaches you to anticipate those problems before they happen.

---

## What Is Performance in System Design?

Performance is how efficiently a system uses its resources to respond to user requests. It is measured in several dimensions:

| Dimension | What It Measures | Example Metric |
|---|---|---|
| Latency | How fast does one request complete? | 50ms for a search query |
| Throughput | How many requests per second can we handle? | 10,000 RPS |
| Resource Utilization | How much CPU/memory/disk are we using? | 70% CPU at peak load |
| Availability | What percentage of time is the system up? | 99.9% uptime |
| Error Rate | What fraction of requests fail? | 0.01% error rate |

These dimensions interact. Squeezing more throughput out of a system often increases latency. Reducing latency often costs more money. This chapter is fundamentally about navigating those trade-offs.

---

## Topics in This Chapter

### 01. Latency vs Throughput (BEGINNER)

**File:** [01. Latency vs Throughput (BEGINNER).md](./01.%20Latency%20vs%20Throughput%20%28BEGINNER%29.md)

The foundation of all performance discussions. Latency measures how long one request takes. Throughput measures how many requests a system handles per second. They sound similar but are independent — you can have a system with high throughput and high latency at the same time. This file also covers P50/P95/P99 percentiles, tail latency, and Little's Law, which are the vocabulary every engineer uses to talk about performance in interviews and on the job.

**Key Topics:** Latency, Throughput, Percentiles, Tail Latency, Little's Law

---

### 02. Performance Optimization Techniques (INTERMEDIATE)

**File:** [02. Performance Optimization Techniques (INTERMEDIATE).md](./02.%20Performance%20Optimization%20Techniques%20%28INTERMEDIATE%29.md)

A systematic toolkit for improving performance. Rather than blindly applying every technique, this file gives you a decision framework: profile first, identify the bottleneck, then pick the right tool. Covers caching at different levels, connection pooling, asynchronous processing, batching, compression, denormalization, read replicas, database query optimization, and lazy loading — with guidance on when to use each.

**Key Topics:** Caching, Connection Pooling, Async I/O, Batching, Compression, Denormalization, Indexes

---

### 03. Database Performance (INTERMEDIATE)

**File:** [03. Database Performance (INTERMEDIATE).md](./03.%20Database%20Performance%20%28INTERMEDIATE%29.md)

The database is almost always the bottleneck in a web system. This file goes deep on database-specific performance techniques: how to read EXPLAIN plans, when to add indexes (and when not to), composite vs. covering indexes, connection pooling tools like PgBouncer, the N+1 query problem and how to fix it, and write optimization strategies. Includes a real worked example: optimizing a slow Instagram-style feed query from 8 seconds to 80 milliseconds.

**Key Topics:** EXPLAIN Plans, Indexes, Connection Pooling, N+1 Problem, Read Replicas, Partitioning

---

### 04. Frontend Performance (BEGINNER)

**File:** [04. Frontend Performance (BEGINNER).md](./04.%20Frontend%20Performance%20%28BEGINNER%29.md)

System design interviews at senior level often include the frontend. This file covers the critical rendering path (how a browser converts HTML to pixels), Google's Core Web Vitals (LCP, INP, CLS) and why they matter for SEO and user experience, CDN for static assets, code splitting, image optimization, HTTP/2 multiplexing, and service workers. Includes how Netflix dramatically reduced their web client startup time.

**Key Topics:** Critical Rendering Path, Core Web Vitals, CDN, Code Splitting, Image Optimization, Service Workers

---

### 05. Load Testing and Benchmarking (INTERMEDIATE)

**File:** [05. Load Testing and Benchmarking (INTERMEDIATE).md](./05.%20Load%20Testing%20and%20Benchmarking%20%28INTERMEDIATE%29.md)

You cannot optimize what you do not measure. Load testing simulates real user traffic so you can find bottlenecks before your users do. This file covers four types of tests (load, stress, spike, soak), the most popular tools (k6, JMeter, Gatling, wrk), how to interpret results, and how to work backwards from test results to find the actual bottleneck. Includes a complete example: designing and running a load test for a URL shortener service.

**Key Topics:** Load Testing, Stress Testing, Spike Testing, Soak Testing, k6, JMeter, Bottleneck Analysis

---

## How to Read This Chapter

If you are new to performance:
1. Start with **Latency vs Throughput** — get the vocabulary right.
2. Read **Frontend Performance** — it is the most concrete and beginner-friendly.
3. Read **Performance Optimization Techniques** — the big picture toolkit.
4. Then go to **Database Performance** and **Load Testing**.

If you are preparing for a senior/staff interview:
1. Skim **Latency vs Throughput** to make sure you can cite percentiles and Little's Law fluently.
2. Focus on **Database Performance** — this is where most interview deep-dives go.
3. Study **Load Testing** — staff engineers are expected to know how to validate performance claims.

---

## Performance in System Design Interviews

In an interview, performance usually comes up in one of three ways:

**1. Estimation:** "How many requests per second will this handle?" You need throughput numbers and Little's Law.

**2. Bottleneck identification:** "Where will this system slow down under load?" You need to understand which component is the limiting factor (usually the database or network).

**3. Optimization:** "How would you make this faster?" You need the toolkit from Chapter 02 and 03.

The key interview insight: **never optimize blindly**. Always say "I would first measure with a profiler / load test to find the actual bottleneck, then apply the appropriate technique." This is what separates senior engineers from juniors.

---

## Related Chapters

- [Chapter 06: Caching](../06.%20Caching/README.md) — Caching is the single most impactful performance technique; it gets its own chapter.
- [Chapter 07: Databases](../07.%20Databases/README.md) — Understanding database internals is required to optimize them.
- [Chapter 09: Load Balancing](../09.%20Load%20Balancing/README.md) — Distributing load is a form of throughput scaling.
- [Chapter 15: Scalability](../15.%20Scalability/README.md) — Scalability and performance are related but different concerns.
- [Chapter 17: Reliability](../17.%20Reliability/README.md) — Reliability techniques like circuit breakers also affect latency.
