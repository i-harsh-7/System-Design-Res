# Resources

Curated learning materials for system design. Every resource listed here is worth your time. Each entry includes a brief note on why it is valuable.

---

## Books

### Essential Reading

**Designing Data-Intensive Applications — Martin Kleppmann**
The single best book on distributed systems and data engineering. Covers replication, partitioning, transactions, consistency, and consensus with rare clarity. Dense but worth every page. Read this alongside Chapters 8-10 of this course.

**System Design Interview: An Insider's Guide (Vol. 1) — Alex Xu**
The most practical interview prep book. Covers 15 common interview problems with clean, well-structured solutions. Best used in Phase 5 to compare your designs against worked examples.

**System Design Interview: An Insider's Guide (Vol. 2) — Alex Xu, Sahn Lam**
The sequel adds 13 more designs covering proximity services, real-time gaming, payments, hotel reservations, and more. Read after Vol. 1.

**Clean Architecture — Robert C. Martin**
Covers software architecture principles: SOLID, component cohesion, boundaries, and the dependency rule. Foundational for thinking about how code is structured, not just how systems are connected.

**Building Microservices (2nd Ed.) — Sam Newman**
The definitive guide to microservices. Covers decomposition, communication, deployment, testing, and migration. Best read alongside Chapter 12.

**The Art of Scalability — Martin Abbott, Michael Fisher**
Introduces the Scale Cube and provides a business-oriented framework for thinking about scalability across people, processes, and technology.

**Release It! (2nd Ed.) — Michael Nygard**
Focuses on patterns for building production-grade systems: stability patterns, capacity antipatterns, and networking. Pairs well with Chapter 11.

**Site Reliability Engineering — Google (free online)**
The book that defined SRE. Covers error budgets, SLOs, toil, on-call, and the philosophy behind running services at scale. Read selectively — focus on chapters relevant to Chapters 15 and 11.

---

## Online Courses and Platforms

**System Design Primer — Donne Martin (GitHub)**
A free, comprehensive GitHub repository covering system design concepts. Excellent for self-study and has a large collection of interview questions. Use it as supplementary reading alongside the course notes.
URL: https://github.com/donnemartin/system-design-primer

**Grokking the System Design Interview — Educative.io**
A paid interactive course with structured design problems. Good for interview prep in Phase 5, especially if you prefer interactive problem sets over static reading.

**ByteByteGo — Alex Xu (Newsletter and Course)**
Alex Xu's subscription platform with animated explainers and visual deep dives. Excellent for visual learners. The weekly newsletter alone is worth subscribing to.
URL: https://bytebytego.com

**High Scalability Blog — highscalability.com**
Long-running blog with case studies on how real companies architect their systems. Invaluable for Chapter 19 case study preparation. Use the "Building X" articles for inspiration.
URL: http://highscalability.com

---

## YouTube Channels

**System Design with Gaurav Sen**
Covers system design concepts and interview questions with clear visual explanations. The video on consistent hashing is one of the best explanations anywhere.
URL: https://www.youtube.com/@gkcs

**Tech Dummies (Narendra L)**
Longer, detailed system design videos covering real systems like Uber, Instagram, WhatsApp. Good for understanding end-to-end architectures.
URL: https://www.youtube.com/@TechDummiesNarendraL

**Arpit Bhayani**
Deep dives into specific system design topics like database internals, distributed systems, and engineering concepts. Detailed and rigorous — pairs well with Chapters 8-10.
URL: https://www.youtube.com/@ArpitBhayani

**Hussein Nasser**
Networking and backend fundamentals explained clearly, including excellent videos on HTTP, proxies, databases, and protocols. Best for Chapters 2 and 13.
URL: https://www.youtube.com/@hnasr

**MIT 6.824 Distributed Systems (MIT OpenCourseWare)**
MIT's graduate distributed systems course. The lectures by Robert Morris cover Raft, Spanner, ZooKeeper, and more. Highly technical — use alongside Chapters 8, 10, 11.
URL: https://www.youtube.com/playlist?list=PLrw6a1wE39_tb2fErI4-WkMbsvGQk9_UB

---

## Blogs and Articles

**Martin Fowler's Blog — martinfowler.com**
The definitive resource on software architecture patterns. Articles on microservices, event sourcing, CQRS, circuit breakers, and the Strangler Fig are canonical.
URL: https://martinfowler.com

**The Netflix Tech Blog — netflixtechblog.com**
Real engineering posts from Netflix's engineers covering CDN design, chaos engineering, A/B testing infrastructure, and more. Read the chaos engineering articles before Chapter 11.
URL: https://netflixtechblog.com

**Uber Engineering Blog — eng.uber.com**
Deep engineering posts on geospatial systems, Kafka usage, Schemaless database, and large-scale services. Directly useful for Chapter 19 case studies.
URL: https://eng.uber.com

**AWS Architecture Blog — aws.amazon.com/blogs/architecture**
Real architectures using AWS services with detailed diagrams. Useful for understanding how cloud-native patterns are implemented.
URL: https://aws.amazon.com/blogs/architecture/

**The Cloudflare Blog — blog.cloudflare.com**
Detailed technical posts on networking, DDoS mitigation, anycast, TLS, and distributed systems at scale. Pairs with Chapter 2 and Chapter 14.
URL: https://blog.cloudflare.com

**Aphyr's Jepsen Reports — jepsen.io**
Kyle Kingsbury's database consistency test reports. Highly technical analyses of how real databases behave under network partitions. Best read after Chapter 10.
URL: https://jepsen.io/analyses

---

## GitHub Repositories

**donnemartin/system-design-primer**
The most starred system design resource on GitHub. Contains comprehensive notes, an Anki flashcard deck, and problem solutions.
URL: https://github.com/donnemartin/system-design-primer

**checkcheckzz/system-design-interview**
A curated list of system design interview questions with links to relevant articles and resources.
URL: https://github.com/checkcheckzz/system-design-interview

**madd86/awesome-system-design**
A broad collection of articles, videos, and resources organized by topic.
URL: https://github.com/madd86/awesome-system-design

**binhnguyennus/awesome-scalability**
An extensive, opinionated collection of articles about scalability, reliability, and performance. Browse by topic as you progress through the course.
URL: https://github.com/binhnguyennus/awesome-scalability

**karanpratapsingh/system-design**
Another well-structured system design guide with clean notes and diagrams.
URL: https://github.com/karanpratapsingh/system-design

---

## Practice Platforms

**Pramp — pramp.com**
Free peer-to-peer mock interview platform. Pairs you with another candidate to practice system design (and coding) interviews in real-time. Use from Phase 3 onward.
URL: https://www.pramp.com

**Interviewing.io — interviewing.io**
Anonymous technical interviews with engineers from top companies. Paid, but offers free practice rounds. Excellent for getting real feedback.
URL: https://interviewing.io

**Exponent — tryexponent.com**
Interview prep platform with system design courses, mock interviews, and a question bank. Also covers product management and behavioral interviews.
URL: https://www.tryexponent.com

**HelloInterview — hellointerview.com**
A newer platform with structured system design problem sets and interactive practice. Good for working through Chapter 20 problems with built-in rubrics.
URL: https://www.hellointerview.com

---

## Official Documentation Worth Reading

**Kafka Documentation — kafka.apache.org/documentation**
The official Kafka docs explain producer configs, consumer groups, partitions, and offset management better than most blog posts. Read alongside Chapter 9.
URL: https://kafka.apache.org/documentation/

**Redis Documentation — redis.io/docs**
The official Redis docs cover every data type and command. Reading the sections on persistence, replication, and cluster mode is directly relevant to Chapter 5.
URL: https://redis.io/docs/

**Kubernetes Documentation — kubernetes.io/docs**
The official K8s docs. The Concepts section covers Pods, Services, Deployments, and Ingress clearly. Read alongside Chapter 17.
URL: https://kubernetes.io/docs/concepts/

**PostgreSQL Documentation — postgresql.org/docs**
Particularly the chapters on indexing, query planning (EXPLAIN), and replication. Directly relevant to Chapters 4 and 16.
URL: https://www.postgresql.org/docs/

**AWS Well-Architected Framework — docs.aws.amazon.com/wellarchitected**
AWS's framework covering five pillars: Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization. A useful checklist for any production system.
URL: https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html

**Google SRE Book — sre.google/sre-book**
Free online. The chapters on SLOs, error budgets, eliminating toil, and postmortems are directly applicable to Chapter 15.
URL: https://sre.google/sre-book/table-of-contents/

---

## Flashcard Decks

**Anki deck from System Design Primer**
Available via the donnemartin/system-design-primer GitHub repo. Useful for memorizing latency numbers, definitions, and key facts.

**Making your own Anki deck**
As you progress through the course, create Anki cards for: latency numbers, capacity estimation shortcuts, definitions from the Glossary, and common tradeoffs. Your own cards are more memorable than pre-made ones.

---

## Recommended Reading Order

For maximum value, use resources in this sequence alongside the course:

| Course Phase | Recommended Supplemental Reading |
|---|---|
| Phase 1 (Basics-Databases) | System Design Primer GitHub repo, Alex Xu Vol. 1 Chapters 1-3 |
| Phase 2 (Caching-Message Queues) | Alex Xu Vol. 1 Chapters 4-8, Redis docs, Kafka docs |
| Phase 3 (Distributed Systems) | DDIA Chapters 5-9, MIT 6.824 lectures |
| Phase 4 (Production Engineering) | Google SRE Book (selected chapters), Netflix Tech Blog |
| Phase 5 (Interview Ready) | Alex Xu Vol. 1 and 2 full read-through, Pramp practice |
