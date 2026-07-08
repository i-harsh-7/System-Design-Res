# Chapter 20: System Design Interview Preparation

This is the final chapter of the System Design course. Everything in the previous 19 chapters has been building toward this: walking into a system design interview and performing with confidence. This chapter is not about new concepts — it is about applying what you know, under pressure, in 45–60 minutes, in front of an interviewer who is evaluating not just your technical knowledge but your thinking process.

---

## Files in This Chapter

| File | Topic | Purpose |
|------|-------|---------|
| [01. System Design Interview Framework](./01.%20System%20Design%20Interview%20Framework.md) | Step-by-step framework | How to structure any system design answer |
| [02. Capacity Estimation Cheat Sheet](./02.%20Capacity%20Estimation%20Cheat%20Sheet.md) | Back-of-envelope calculations | Numbers, formulas, worked examples |
| [03. Common Interview Questions and Answers](./03.%20Common%20Interview%20Questions%20and%20Answers.md) | 50+ questions with approaches | Beginner to advanced, every major system |
| [04. Design Patterns Reference Card](./04.%20Design%20Patterns%20Reference%20Card.md) | Architectural patterns | When to use each pattern, with diagrams |
| [05. Numbers Every Engineer Should Know](./05.%20Numbers%20Every%20Engineer%20Should%20Know.md) | Latency, throughput, storage | The reference numbers that come up constantly |
| [06. SQL vs NoSQL Decision Guide](./06.%20SQL%20vs%20NoSQL%20Decision%20Guide.md) | Database selection | Decision tree + per-database breakdown |
| [07. Architecture Diagrams Guide](./07.%20Architecture%20Diagrams%20Guide.md) | Drawing systems | What to draw, how to draw it, common mistakes |
| [08. Behavioral Signals in System Design](./08.%20Behavioral%20Signals%20in%20System%20Design%20Interviews.md) | Soft skills | What interviewers really evaluate |
| [09. 30-Day Study Plan](./09.%2030-Day%20Study%20Plan.md) | Study schedule | Structured preparation from zero to ready |

---

## What to Expect in a FAANG System Design Interview

System design interviews are standard at Meta, Amazon, Apple, Netflix, Google, and most other top-tier tech companies for software engineering roles at SDE-2 level and above. At the L3/E3 level (junior), you may or may not encounter one. At L4/E4 (mid-level) and above, it is almost guaranteed.

### Interview Format

A typical system design interview runs **45 to 60 minutes**. The structure is loosely:

- **0–5 min:** Introductions, problem statement delivery. You are given a vague prompt like "Design Twitter" or "Design a distributed cache."
- **5–10 min:** Requirements clarification. You ask questions. The interviewer answers them to help you scope the problem.
- **10–15 min:** High-level design. You sketch the major components.
- **15–35 min:** Deep dive. The interviewer picks one or two components and asks you to go deep. This is where the real evaluation happens.
- **35–45 min:** Bottlenecks, scaling, trade-offs. You identify what breaks and how you'd fix it.
- **45–55 min:** Questions from you to the interviewer (sometimes).

The format varies by company and interviewer, but this is the most common structure. At Google, interviewers tend to guide less and let you drive more. At Amazon, there is often explicit focus on scale from the start. At Meta, interviewers tend to go deep on one specific component.

### Virtual vs. Whiteboard Interviews

- **On-site (whiteboard):** You draw on a physical whiteboard. Have a plan before you start drawing. Use boxes for services, cylinders for databases, arrows for data flow.
- **Virtual (collaborative whiteboard):** You use a shared tool — CoderPad, Excalidraw, Miro, or a Google Doc. Practice with these tools beforehand. Fumbling with a tool while trying to think kills your pacing.

---

## Evaluation Criteria: What Interviewers Actually Look For

Most companies evaluate system design interviews on a rubric, even if interviewers don't share it explicitly. The dimensions are consistent across companies:

### 1. Problem Navigation
Can you take a vague, open-ended problem and scope it into something you can actually design? Interviewers deliberately give you under-specified problems. They want to see you ask smart questions, define boundaries, and make reasonable assumptions rather than freezing up.

**Strong signal:** "I'll scope this to a system handling 100 million daily active users with eventual consistency on the feed. Does that match what you have in mind?"

**Weak signal:** Starting to draw boxes before asking a single question.

### 2. Technical Breadth
Do you know the building blocks? Candidates who have never heard of consistent hashing, don't know the difference between SQL and NoSQL, or can't explain why you'd use a message queue versus a direct API call will struggle with follow-up questions.

**Strong signal:** Using the right tool for the job without needing to be told what tools exist.

**Weak signal:** Defaulting to "just use MySQL" for every data storage problem.

### 3. Technical Depth
Can you go deep on specific components when asked? An interviewer who says "tell me more about how your database handles write spikes" is probing whether you have real depth or just surface knowledge.

**Strong signal:** Walking through write-ahead logs, replica lag, and how your application handles a primary failover.

**Weak signal:** "I'd add more servers."

### 4. Trade-off Awareness
Every design decision has a cost. Strong candidates articulate what they are giving up. "I'm choosing Cassandra here because it scales writes horizontally, but the trade-off is eventual consistency — reads might return stale data for a few seconds. That's acceptable for a social feed."

**Strong signal:** Comparing two options and explaining why you chose one given your specific constraints.

**Weak signal:** Presenting a design as if it has no downsides.

### 5. Communication
System design is collaborative. You are expected to think out loud, check in with the interviewer, and adjust based on their feedback. Silence is a bad sign. Monologuing without checking in is also a bad sign.

**Strong signal:** "I'm going to design the notification service next — does that sound like the right area to focus on, or would you prefer I dive deeper into the feed generation?"

**Weak signal:** Designing in silence for 10 minutes and then revealing a finished diagram.

### 6. Ownership and Pragmatism
Senior engineers are expected to own systems, which means thinking about operational concerns: monitoring, failure modes, maintenance burden. Mentioning these signals seniority.

**Strong signal:** "I'd add a dead-letter queue here so failed messages don't get silently dropped, and I'd alert on the DLQ depth."

**Weak signal:** Designing a happy-path-only system with no thought for what breaks.

---

## Common Mistakes Candidates Make

Understanding these mistakes is as valuable as knowing the right answers. Avoid every one of these.

### Jumping Straight to the Solution
The most common and costly mistake. You hear "Design Twitter" and immediately start drawing boxes. You have not asked what features to build, what scale to target, or what constraints matter. You are now designing a solution to a problem you do not fully understand.

**Fix:** Spend 5 full minutes on requirements. Write them down visibly. Confirm them with the interviewer before drawing anything.

### Over-engineering from the Start
You have 45 minutes to design a system. You do not have time to describe a fully microservices-native, Kubernetes-orchestrated, multi-region active-active system with 47 services. More importantly, an interview problem at the scale they give you probably does not need it.

**Fix:** Start simple. Add complexity only when you can explain what problem it solves. "I'd add a CDN here because 80% of reads are for popular content, and serving from origin would be unnecessary load."

### Ignoring the Database
A surprising number of candidates sketch out a beautiful microservices diagram and forget to think seriously about data storage. What database? What schema? How do you handle relationships? What happens when it fills up?

**Fix:** Make data modeling an explicit step in your framework. Always ask: "What data am I storing? How is it queried? What are the read/write patterns?"

### Vague Answers to Follow-up Questions
"I'd cache that" is not an answer. Where? What caching strategy? What is the eviction policy? What happens on a cache miss? Vague answers signal surface-level knowledge.

**Fix:** Be specific. "I'd use Redis with an LRU eviction policy. The TTL would be 5 minutes. On a cache miss, the request falls through to the database, and the result is written back to cache."

### Not Acknowledging What You Don't Know
Candidates sometimes confidently state things that are wrong because they are afraid to admit uncertainty. Interviewers notice.

**Fix:** "I'm not certain about the exact Kafka partition limit off the top of my head, but my reasoning here is that we want to maximize parallelism, so I'd use at least as many partitions as consumer instances." Showing reasoning under uncertainty is a strong signal.

### Running Out of Time on Requirements
Five minutes is a recommendation, not a minimum. Some candidates spend 20 minutes asking about edge cases and never get to the design.

**Fix:** Scope to what matters for the design. Ask about scale (DAU, QPS, storage). Ask about the core feature set. Confirm the most important non-functional requirements (consistency? availability? latency?). Then start designing.

### Treating Every Problem as the Same
"Design a URL shortener" and "Design Google Maps" have almost nothing in common architecturally. Candidates who apply the same template to every problem — "put a cache in front of the database, add a load balancer" — signal that they are not actually thinking about the problem.

**Fix:** Start every problem from the requirements. Let the requirements drive the architecture. The architecture for a read-heavy, globally distributed, media-serving system looks nothing like the architecture for a transactional financial ledger.

---

## A Note on Preparation

System design interviews reward people who have spent time thinking deeply about real systems. The best preparation is not memorizing templates — it is understanding why systems are built the way they are. When you read that Cassandra uses a ring topology for consistent hashing, ask why. When you learn that Kafka uses append-only log storage, ask what problems that solves and what trade-offs it introduces.

Use this chapter as a reference and a framework, not a script. The engineers who perform best in system design interviews are the ones who genuinely find distributed systems interesting.

---

*This chapter assumes you have completed Chapters 1–19. If you are jumping directly here for interview prep, start with Chapter 02 (Capacity Estimation Cheat Sheet) and Chapter 05 (Numbers Every Engineer Should Know) — those will give you the raw material you need to make quantitative design decisions.*
