---
title: "Pregel and Graph Message Passing"
topic_number: 125
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - pregel
  - message-passing
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Pregel and Graph Message Passing

> [!abstract] Summary
> Pregel-style graph processing ใช้ iterative vertex-centric message passing: vertices receive aggregated messages, update state, and send messages to neighbors over supersteps until convergence/termination.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Vertex-centric computation.
- Messages sent along edges.
- Aggregate messages per destination/source.
- Iterative supersteps/barrier-style progression.

## Technical Detail

Message-passing abstraction เหมาะกับ PageRank, shortest paths, propagation algorithms. Cost driven by active vertices, edges traversed, serialization and network shuffle.

## Practical Example

Each vertex sends current distance/rank contribution to neighbors; aggregate messages update next state.

## When to use

ใช้พัฒนา custom iterative graph algorithms on distributed graph engines.

## Limitations / Assumptions

- Communication-heavy algorithms may scale poorly on dense/skewed graphs.
- Convergence criteria must be defined.

## Common Mistakes

- send full large state every iteration unnecessarily.
- assume vertex-centric model removes network cost.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture links Pregel and aggregateMessages; canonical note keeps conceptual message-passing model and avoids version-specific exact API syntax.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Pregel-style graph processing ใช้ iterative vertex-centric message passing: vertices receive aggregated messages, update state, and send messages to neighbors over supersteps until convergence/termination.
- **Use when:** ใช้พัฒนา custom iterative graph algorithms on distributed graph engines.
- **Main caution:** send full large state every iteration unnecessarily.

## Related Notes

- [[GraphX and GraphFrames]]
- [[PageRank]]
- [[Breadth-First Search]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 9 - Graph Analytics]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
