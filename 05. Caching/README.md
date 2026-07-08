# Chapter 05: Caching

## Why This Chapter Exists

Every system eventually hits a wall. Your database cannot answer a million queries per second cheaply. Your users cannot wait 800ms for a page to load. Caching is the single most effective tool for breaking through that wall. It is not optional knowledge — every senior engineer and every system design interview expects you to know it cold.

This chapter takes you from zero ("what even is a cache?") all the way to advanced production concerns ("how does Facebook serve a billion users with Memcache?"). Each file builds on the previous one.

---

## Learning Objectives

By the end of this chapter you will be able to:

- Explain what a cache is and why it matters
- Choose the right caching strategy (Cache-Aside, Write-Through, etc.) for a given situation
- Explain eviction policies and implement an LRU cache conceptually
- Use Redis data structures intelligently in system design
- Reason about cache invalidation and the problems it causes
- Design a distributed caching layer that handles failures and hot keys
- Explain CDN caching and its role in global content delivery
- Answer caching questions confidently in system design interviews

---

## Prerequisites

- Basic understanding of databases (Chapter 04)
- Basic networking concepts — HTTP, latency (Chapter 02)
- Understanding of scalability problems (Chapter 03)

---

## Chapter Map

| # | File | Level | What You Learn |
|---|------|-------|----------------|
| 01 | [What is Caching](./01.%20What%20is%20Caching%20(BEGINNER).md) | Beginner | Cache fundamentals, hit/miss, hierarchy, why it matters |
| 02 | [Caching Strategies](./02.%20Caching%20Strategies%20(INTERMEDIATE).md) | Intermediate | 5 patterns: Cache-Aside, Write-Through, Write-Behind, Read-Through, Refresh-Ahead |
| 03 | [Cache Eviction Policies](./03.%20Cache%20Eviction%20Policies%20(INTERMEDIATE).md) | Intermediate | LRU, LFU, FIFO, MRU, TTL — when the cache fills up |
| 04 | [Redis Deep Dive](./04.%20Redis%20Deep%20Dive%20(INTERMEDIATE).md) | Intermediate | Redis data structures, persistence, real-world usage at Twitter/Uber |
| 05 | [Cache Invalidation](./05.%20Cache%20Invalidation%20(INTERMEDIATE).md) | Intermediate | The hardest problem — stale data, stampede, thundering herd |
| 06 | [Distributed Caching](./06.%20Distributed%20Caching%20(INTERMEDIATE).md) | Intermediate | Consistent hashing, Redis Cluster, hot keys, Facebook TAO |
| 07 | [CDN as a Cache](./07.%20CDN%20as%20a%20Cache%20(BEGINNER).md) | Beginner | Edge caching, push vs pull CDN, cache-control headers |

---

## How to Read This Chapter

**If you are new to caching:** Read files 01, 07, then 02 in that order. Then come back for the rest.

**If you have used Redis before:** Skim 01, then go deep on 02, 03, 05.

**If you are preparing for a system design interview:** All files are relevant. Focus especially on 02, 04, 05, and 06. These come up the most.

---

## Core Theme Running Through This Chapter

Every caching decision is a trade-off between:

- **Speed** (how fast do you want reads to be?)
- **Freshness** (how stale can the data be?)
- **Complexity** (how much code do you want to maintain?)
- **Cost** (memory is more expensive than disk)

There is no universal "best" caching strategy. The right answer always depends on your use case. This chapter teaches you to reason through those trade-offs, not to memorize a single answer.

---

## Related Chapters

- [Chapter 02: Networking](../02.%20Networking/) — HTTP headers, CDN basics, latency
- [Chapter 03: Scalability](../03.%20Scalability/) — Why we need caching to scale
- [Chapter 04: Databases](../04.%20Databases/) — What we are caching in front of
- [Chapter 06: Load Balancing](../06.%20Load%20Balancing/) — Distributing cache nodes
- [Chapter 08: Distributed Systems](../08.%20Distributed%20Systems/) — Consistency in distributed caches
