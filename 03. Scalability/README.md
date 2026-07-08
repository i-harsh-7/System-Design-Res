# Chapter 03: Scalability

Scalability is the single most tested topic in system design interviews — and for good reason. Building a system that works for 100 users is easy. Building one that works for 100 million users is engineering. This chapter takes you from zero to confident on every dimension of scalability.

## What This Chapter Covers

This chapter answers one central question: **how do you build systems that grow?**

You will start by understanding what scalability even means, then work through every major tool and technique that engineers use to scale real-world systems — from scaling servers, to scaling databases, to managing state, to caching. The final file gives you a reusable interview framework you can apply to any design problem.

---

## Topics at a Glance

| # | File | Level | What You Will Learn |
|---|------|-------|---------------------|
| 01 | [What is Scalability](./01.%20What%20is%20Scalability%20(BEGINNER).md) | Beginner | The definition of scalability, why systems fail under load, throughput vs latency, vertical vs horizontal at a high level |
| 02 | [Vertical vs Horizontal Scaling](./02.%20Vertical%20vs%20Horizontal%20Scaling%20(BEGINNER).md) | Beginner | When to scale up vs scale out, the limits of each, cost and complexity trade-offs |
| 03 | [Load Balancing Basics](./03.%20Load%20Balancing%20Basics%20(BEGINNER).md) | Beginner | What a load balancer does, common algorithms, Layer 4 vs Layer 7, health checks |
| 04 | [Database Scaling](./04.%20Database%20Scaling%20(BEGINNER).md) | Beginner | Why the DB is the bottleneck, read replicas, connection pooling, an intro to sharding |
| 05 | [Stateless vs Stateful Architecture](./05.%20Stateless%20vs%20Stateful%20Architecture%20(INTERMEDIATE).md) | Intermediate | Why state breaks horizontal scaling, JWT vs sessions, externalized state patterns |
| 06 | [Caching for Scalability](./06.%20Caching%20for%20Scalability%20(BEGINNER).md) | Beginner | Caching as a scalability lever, cache levels, hit ratio, cache invalidation |
| 07 | [The Scalability Interview Framework](./07.%20The%20Scalability%20Interview%20Framework%20(BEGINNER).md) | Beginner | A 5-step framework for answering any "design a scalable X" question |

---

## Learning Path

If you are completely new to system design, read the files in order (01 through 07). Each file builds on the mental model established by the previous one.

If you are preparing for interviews specifically, prioritize files **01**, **02**, **05**, and **07** first — these form the conceptual core. Then read **03** and **04** for the implementation details you will need to draw on a whiteboard.

---

## Prerequisites for This Chapter

Before starting this chapter, you should have a basic understanding of:

- What a server is (a computer that responds to requests)
- What a database is (a system that stores and retrieves data)
- The basic request-response cycle (client sends a request, server sends a response)

These are covered in **Chapter 01: Basics** and **Chapter 02: Networking**.

---

## How This Chapter Connects to the Rest of the Course

Scalability is not an isolated concept. Every chapter in this course touches it:

- **Chapter 04 (Databases)** goes deep on sharding, replication, and NoSQL — all scalability strategies for data
- **Chapter 05 (Caching)** gives you the full picture of caching beyond what this chapter introduces
- **Chapter 06 (Load Balancing)** is a complete deep-dive into load balancers, including advanced patterns
- **Chapter 08 (Distributed Systems)** covers the theoretical foundations (CAP theorem, consistency models) that explain why horizontal scaling is hard

Think of this chapter as the *map*. The later chapters are the detailed *territory*.

---

## Key Questions This Chapter Answers

- What does it mean for a system to be scalable?
- What is the difference between vertical and horizontal scaling?
- How do you distribute traffic across multiple servers?
- Why is the database almost always the bottleneck, and what do you do about it?
- Why does adding more servers sometimes make things worse?
- How do you handle user sessions when you have 10 servers instead of one?
- How does caching reduce load on your system?
- How do you structure your answer to any scalability question in an interview?
