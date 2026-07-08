# Chapter 17: Cloud and Infrastructure

## Chapter Overview

This chapter covers how modern systems are built, deployed, and operated in the cloud. Whether you are preparing for a system design interview or building production systems, understanding cloud fundamentals and infrastructure practices is non-negotiable.

At the beginner level, you need to understand what the cloud actually is and why companies use it. At the intermediate and senior level, you need to know specific services, patterns, and trade-offs — the kind of things an interviewer expects you to cite naturally when designing a large system.

---

## Topics in This Chapter

| # | File | Level | Description |
|---|------|-------|-------------|
| 01 | [Cloud Computing Basics](./01.%20Cloud%20Computing%20Basics%20(BEGINNER).md) | Beginner | What the cloud is, IaaS vs PaaS vs SaaS, benefits and trade-offs, the big three providers |
| 02 | [Key AWS Services for System Design](./02.%20Key%20AWS%20Services%20for%20System%20Design%20(INTERMEDIATE).md) | Intermediate | The AWS services interviewers expect you to know — compute, storage, database, networking, messaging |
| 03 | [Serverless Architecture](./03.%20Serverless%20Architecture%20(INTERMEDIATE).md) | Intermediate | How Lambda and FaaS work, cold starts, event-driven patterns, when serverless is a bad idea |
| 04 | [Infrastructure as Code](./04.%20Infrastructure%20as%20Code%20(INTERMEDIATE).md) | Intermediate | Terraform, CloudFormation, GitOps — defining and versioning infrastructure in code files |
| 05 | [CI/CD Pipelines](./05.%20CI-CD%20Pipelines%20(BEGINNER).md) | Beginner | How code travels from a laptop to production safely — build, test, deploy stages, blue-green, canary |
| 06 | [Multi-Region Architecture](./06.%20Multi-Region%20Architecture%20(INTERMEDIATE).md) | Intermediate | Active-active vs active-passive, data residency, latency routing, cross-region replication |

---

## How to Use This Chapter

**If you are a beginner**, start with topics 01 and 05. They require no prior cloud knowledge and give you the vocabulary to understand everything else.

**If you are preparing for a senior/staff interview**, focus on topics 02, 03, 04, and 06. These come up constantly in real system design rounds. Interviewers do not expect you to recite every AWS service, but they do expect you to know which tool to reach for and why.

**If you are studying for FAANG-style interviews**, pay special attention to:
- The trade-offs in each topic, not just the happy path
- When NOT to use each pattern (interviewers probe this heavily)
- The Mermaid diagrams — drawing architecture diagrams on a whiteboard is a core skill

---

## Prerequisites for This Chapter

Before starting this chapter, you should be comfortable with:

- Basic networking (HTTP, DNS, TCP/IP) — covered in Chapter 4
- Databases (SQL, NoSQL) — covered in Chapter 6 and 7
- Caching fundamentals — covered in Chapter 8
- Load balancing — covered in Chapter 5

---

## Key Themes Across This Chapter

**Managed vs. Self-Managed**: Cloud providers offer managed versions of almost every component (managed databases, managed Kubernetes, managed message queues). Managed services reduce operational burden but reduce control and can increase cost.

**Elasticity**: Cloud systems can scale up and down automatically. This is one of the most important reasons to use cloud infrastructure.

**Operational Complexity vs. Developer Productivity**: Serverless and PaaS remove operational burden from developers. IaC and CI/CD pipelines add upfront investment but pay dividends at scale.

**Failure is Normal**: Modern cloud architecture assumes any individual component can fail at any time. Multi-region architecture, circuit breakers, and redundancy are how you design around this reality.

---

## Suggested Reading Order

```
01. Cloud Computing Basics
        |
        v
02. Key AWS Services
        |
        +----> 03. Serverless Architecture
        |
        +----> 04. Infrastructure as Code
        |
        v
05. CI/CD Pipelines
        |
        v
06. Multi-Region Architecture
```

---

## Related Chapters

- [Chapter 5: Load Balancing](../05.%20Load%20Balancing/)
- [Chapter 8: Caching](../08.%20Caching/)
- [Chapter 9: Message Queues](../09.%20Message%20Queues/)
- [Chapter 14: Microservices](../14.%20Microservices/)
- [Chapter 16: Monitoring and Observability](../16.%20Monitoring%20and%20Observability/)
