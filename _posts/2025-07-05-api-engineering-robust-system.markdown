---
layout: post
comments: false
title:  "API engineering and building robust systems"
excerpt: "Modern software are built on API-first policy. Without APIs your product is isolated in its own boundaries. In this post I disucss essential things you need to engineer your APIs elegantly and build robust systems."
date:   2025-07-05 10:00:00
---

Modern software are built on API-first policy. Without APIs your product is isolated in its own boundaries. In this post I disucss essential things you need to engineer your APIs elegantly and build robust systems.

- Check this post on [A survival kit to beat APIs interview](https://newsletter.systemdesignclassroom.com/p/a-survival-kit-to-beat-apis-interview) by [Raul Junco](https://substack.com/@rauljuncov). Though this article is written in an "interview prep" way, but it's a masterpiece on elegant API design and engineering, covering nearly all the important topics.

    - CRUD operations and HTTP verb
    - HTTP status codes and the ones which are most frequently used
    - Stateless APIs
    - Different ways you can secure your APIs using AuthN and AuthZ, rate limiting, input validation, HTTPS and encrypting data on storage
    - API Keys (for application identification) vs tokens (for user identification)
    - Versioning your APIs either by URL based versioning or using custom headers
    - Pagination using limit-offset, cursor, page numbers or keysets
    - Rate Limiting and why it is important
    - Idempotency and ensuring it with an `IdempotencyKey` added by the client for each request, that violates a unique constraint on the database when executed more than once
    - Ways to make your APIs faster using caching on the client, server, or CDN, distributed caching, query optimization, connection pooling, data serialization and compressiong
    - Documenting APIs using OpenAPI (Swagger) including endpoint descriptions, req-res examples, query parameters, headers, error codes, etc

- Next, this post on [Siz strategies to build secure APIs](https://newsletter.systemdesigncodex.com/p/6-strategies-to-build-secure-apis) by [Saurabh Dashora](https://substack.com/@saurabhdashora). Must read! Describes six strategies that help you bullet-proof your APIs:

    - Using HTTPs
    - Rate limiting and throttling
    - Validation of inputs
    - AuthN and AuthZ 
    - Role-based access control (RBAC)
    - Monitoring and logging

- We can't imagine a software system that doesn't use a database.. and with database, comes the responsibility to manage data and transactions. Another article by [Raul Junco](https://substack.com/@rauljuncov) on [Transaction Isolation](https://newsletter.systemdesignclassroom.com/p/transaction-isolation-and-read-and-write-anomalies?r=1m1f9z&utm_campaign=post&utm_medium=web).

    - What transactions are
    - Read Write anomalies: Dirty reads, non-repeatable reads, phantom reads and write skew 
    - Transaction Isolation Levels: Read uncommitted, read committed, repeatable read and serializable.
    - Performance trade-offs
    - Choosing isolation levels

- Improving application and API performance need caching. We need to cache data at many levels. This can quickly start becoming an overhead as we cache more and more data. Wisdom says, you cache what is frequently required, and remove anything that's not required often. However, as scenarios call for it, there could be needs for different strategies. Read on [Seven cache eviction strategies](https://blog.algomaster.io/p/7-cache-eviction-strategies?r=1m1f9z&utm_campaign=post&utm_medium=web) by [Ashish Pratap Singh](https://substack.com/@ashishps).

    - Least recently used (LRU)
    - Least frequently used (LFU)
    - First In, First Out (FIFO)
    - Random replacement (RR)
    - Most recently used (MRU)
    - Time to live (TTL)
    - Two-tiered caching  

- Like any other machine, software (an intangible machine with moving parts) quality and maintainability degrade overtime. I asked ChatGPT for a very short summary on *Software Entropy*:

    > In software, entropy refers to the increasing disorder, complexity, or unpredictability within a system over time. In software design, high entropy means the code becomes harder to understand, maintain, or extend, often due to quick fixes, poor documentation, or lack of refactoring. This leads to software rot and reduced reliability. 

    Read on how to [Embrace Software Entropy](https://thetshaped.dev/p/embrace-software-entropy-imperfect-code-flexibility-maintainability) by [Petar Ivanov](https://substack.com/@petarivanovv9).

    - Accept that change is inevitable
    - Build for now *(very very very important!)*
    - Stay flexible
    - Embrace entropy

The software industry has many people of wisdom who write technical articles like above. Thanks to all the authors. I try to collect such well crafted knowledge articles and document them on this blog.
