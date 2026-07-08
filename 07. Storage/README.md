# Chapter 07: Storage

## Chapter Overview

Storage is the foundation of every system you will ever build. Every database, every file upload, every photo, every video, every log — it all ends up somewhere on disk. Senior engineers are expected to understand not just *what* storage is available, but *why* different storage systems exist, *what trade-offs* they make, and *when* to pick one over another.

This chapter takes you from the basics (what is block storage?) all the way to advanced internals (how does RocksDB actually write data to disk?). By the end, you will be able to walk into any system design interview and reason confidently about storage choices.

---

## Why Storage Matters in System Design

Most performance problems in large-scale systems are storage problems in disguise:

- Your API is slow — probably because a database query is doing a full table scan.
- Your upload pipeline is bottlenecked — probably because you are routing large files through your application server instead of directly to object storage.
- Your system went down and lost data — probably because replication was not configured correctly.
- Your writes are fast but reads are slow — probably because you are using an LSM-tree engine but your workload is read-heavy.

Understanding storage deeply means you can anticipate these problems before they happen.

---

## Topics in This Chapter

| # | File | Level | Description |
|---|------|-------|-------------|
| 01 | [Types of Storage](./01.%20Types%20of%20Storage%20(BEGINNER).md) | Beginner | The four storage types every engineer must know: block, file, object, and in-memory. Comparison table, analogies, and when to use each. |
| 02 | [Object Storage Deep Dive](./02.%20Object%20Storage%20Deep%20Dive%20(INTERMEDIATE).md) | Intermediate | How S3, GCS, and Azure Blob Storage actually work. Buckets, keys, versioning, storage classes, lifecycle policies, multipart upload, and pre-signed URLs. Design Instagram's photo storage. |
| 03 | [RAID and Disk Reliability](./03.%20RAID%20and%20Disk%20Reliability%20(INTERMEDIATE).md) | Intermediate | Disks fail. RAID spreads data across multiple disks for redundancy and/or performance. RAID 0, 1, 5, 6, and 10 explained with analogies and a comparison table. |
| 04 | [Distributed File Systems](./04.%20Distributed%20File%20Systems%20(INTERMEDIATE).md) | Intermediate | When data does not fit on one machine. HDFS, the Google File System paper, NameNode/DataNode architecture, and when to use S3 + Spark instead of HDFS. |
| 05 | [Data Replication Strategies](./05.%20Data%20Replication%20Strategies%20(INTERMEDIATE).md) | Intermediate | Keeping multiple copies of data for reliability. Synchronous vs asynchronous replication, quorum reads/writes, geo-replication, and conflict resolution. Cassandra as a real-world example. |
| 06 | [Database Storage Engines](./06.%20Database%20Storage%20Engines%20(ADV).md) | Advanced | What actually happens on disk when a database stores data. B-trees vs LSM-trees, write-ahead logs, SSTables, memtables, and compaction. Why Cassandra is write-optimized and PostgreSQL is read-optimized. |

---

## How to Read This Chapter

If you are a beginner, start with **Topic 01** and read sequentially. Each topic builds on the last.

If you already know the basics and want to target interviews, focus on:
- **Topic 02** (Object Storage) — comes up in almost every design round involving media or files.
- **Topic 05** (Replication) — comes up whenever availability and consistency are discussed.
- **Topic 06** (Storage Engines) — comes up in advanced rounds at companies like Google, Meta, and Stripe.

---

## Key Mental Models for This Chapter

Before diving in, hold these three ideas in your head:

**1. Every storage trade-off is about the same three things: speed, durability, and cost.**
Fast storage (RAM) is expensive and volatile. Slow storage (tape) is cheap and durable. Everything else is somewhere in between.

**2. Distributed systems use replication to survive hardware failure.**
A single disk will fail eventually. The question is not *if*, it is *when*. Replication ensures that when a disk dies, no data is lost.

**3. Write patterns and read patterns demand different data structures.**
If you mostly write data, LSM-trees are your friend. If you mostly read data, B-trees are your friend. Picking the wrong engine for your workload is a common and expensive mistake.

---

## Prerequisites for This Chapter

- Basic understanding of how a hard drive works (spinning disk vs SSD)
- Familiarity with what a database is
- Basic knowledge of what latency means (milliseconds vs microseconds)
- Completed Chapters 01–06 of this series (or equivalent experience)

---

## Related Chapters

- [Chapter 05: Databases](../05.%20Databases/README.md) — Storage engines power databases; these chapters are deeply connected.
- [Chapter 06: Caching](../06.%20Caching/README.md) — In-memory storage (Redis) is covered as a storage type here and as a caching layer there.
- [Chapter 08: Networking](../08.%20Networking/README.md) — Data transfer speeds affect how quickly storage can be read from or written to.
- [Chapter 10: Consistency and Replication](../10.%20Consistency%20and%20Replication/README.md) — Chapter 05 of Storage (Replication Strategies) is a warm-up for that deeper chapter.
