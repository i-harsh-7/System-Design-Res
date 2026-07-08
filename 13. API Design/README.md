# 13. API Design — Chapter Overview

## Why This Chapter Exists

Every system you build needs to communicate with other systems, mobile apps, browsers, or third-party services. That communication happens through APIs. An API (Application Programming Interface) is the contract between your system and the outside world.

Bad API design causes cascading pain. Clients break when you change things. Developers spend hours reading confusing documentation. Security holes appear because endpoints were never hardened. Performance degrades because clients fetch far more data than they need.

Good API design is one of the most visible and long-lasting decisions you make as a backend engineer. The APIs you ship today will be called by clients you have never met, in ways you never anticipated, years from now.

This chapter takes you from "I know what a REST endpoint is" to "I can design, version, secure, and evolve production-grade APIs at scale."

---

## What You Will Learn

By the end of this chapter you will be able to:

- Design clean, intuitive REST APIs that follow industry conventions
- Understand when GraphQL or gRPC is a better fit than REST
- Version APIs safely so existing clients never break
- Secure APIs using OAuth 2.0, JWT, and industry best practices
- Choose between polling and webhooks for event-driven integration
- Avoid the most common API design mistakes that show up in system design interviews

---

## Chapter Structure

| File | Topic | Level | What It Covers |
|------|-------|-------|----------------|
| [01. REST API Design Best Practices](./01.%20REST%20API%20Design%20Best%20Practices%20%28INTERMEDIATE%29.md) | REST | Intermediate | Resource naming, HTTP methods, status codes, versioning, pagination, idempotency, error formats |
| [02. GraphQL](./02.%20GraphQL%20%28INTERMEDIATE%29.md) | GraphQL | Intermediate | Schema, queries, mutations, subscriptions, N+1 problem, DataLoader |
| [03. gRPC](./03.%20gRPC%20%28INTERMEDIATE%29.md) | gRPC | Intermediate | Protocol Buffers, code generation, streaming modes, HTTP/2 |
| [04. API Versioning and Evolution](./04.%20API%20Versioning%20and%20Evolution%20%28INTERMEDIATE%29.md) | Versioning | Intermediate | Breaking vs non-breaking changes, versioning strategies, deprecation |
| [05. API Security](./05.%20API%20Security%20%28INTERMEDIATE%29.md) | Security | Intermediate | API keys, OAuth 2.0, JWT, rate limiting, CORS, OWASP API Top 10 |
| [06. Webhooks and Polling](./06.%20Webhooks%20and%20Polling%20%28BEGINNER%29.md) | Webhooks | Beginner | Polling patterns, webhook design, signature verification, idempotency |

---

## How to Read This Chapter

**If you are new to API design**, start with REST best practices (File 01), then jump to security (File 05) and webhooks (File 06). These three files give you the foundation that matters most in day-to-day engineering.

**If you are preparing for a system design interview**, read all six files in order. Interviewers at senior level expect you to compare REST vs GraphQL vs gRPC and justify your choice, discuss versioning strategy, and describe how you would secure an API.

**If you already know REST well**, skip to GraphQL (File 02) and gRPC (File 03) to fill the gaps, then review versioning and security.

---

## Key Vocabulary Before You Start

| Term | Plain English |
|------|---------------|
| API | A contract — a defined way two programs talk to each other |
| REST | A style of API design using HTTP, URLs, and verbs (GET, POST, etc.) |
| GraphQL | A query language where the client specifies exactly what data it wants |
| gRPC | A high-performance RPC framework using binary encoding (Protobuf) |
| Idempotent | Calling the same operation multiple times gives the same result |
| Versioning | Releasing v2 of your API without breaking existing v1 clients |
| Webhook | Your server calling someone else's URL when an event happens |
| JWT | A signed token carrying user identity and claims |

---

## The Big Picture: Which API Style When?

```
         ┌─────────────────────────────────────────────┐
         │              API Style Selection             │
         └─────────────────────────────────────────────┘

  Public API for        →  REST
  web/mobile clients

  Client needs custom   →  GraphQL
  shapes of data

  Internal microservice →  gRPC
  calls (low latency)

  Real-time events      →  WebSockets / SSE
  from server

  Notify your server    →  Webhooks
  when remote event fires
```

---

## Prerequisites for This Chapter

Before reading this chapter, you should be comfortable with:

- Basic HTTP (methods, status codes, headers, request/response cycle)
- JSON format
- What a microservices architecture looks like (Chapter 12)
- Basic security concepts like HTTPS and authentication (Chapter 14 will go deeper)

---

## Related Chapters

- [12. Microservices](../12.%20Microservices/README.md) — APIs are how microservices talk to each other
- [14. Security](../14.%20Security/README.md) — Deeper security patterns beyond API-level auth
- [15. Observability](../15.%20Observability/README.md) — Monitoring and tracing API calls in production
- [05. Caching](../05.%20Caching/README.md) — Caching API responses at the gateway or client level
