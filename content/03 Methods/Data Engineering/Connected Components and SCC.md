---
title: "Connected Components and SCC"
topic_number: 121
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - connected-components
  - scc
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Connected Components and SCC

> [!abstract] Summary
> Connected components partition an undirected graph into maximal mutually reachable sets; strongly connected components (SCC) do analogous mutual reachability for directed graphs.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Undirected CC: path exists between any two vertices in component.
- Directed SCC: each vertex reachable from every other following directions.
- Component ID is implementation label, not semantic meaning.

## Technical Detail

Weak connectivity and strong connectivity are different concepts for directed graphs. SCC is useful for cycles/mutual reachability, not simply “dense community”.

## Practical Example

Web/service dependency graph SCC can reveal mutually dependent cyclic groups.

## When to use

ใช้กับ network segmentation, reachability structure, cycle/dependency analysis.

## Limitations / Assumptions

- Large-scale algorithms iterative and communication-heavy.
- A component can be structurally loose; it is not necessarily a cohesive community.

## Common Mistakes

- interpret SCC as “people with common interests” without validation.
- assume component ID = meaningful rank.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture gives social-community applications; canonical note labels such interpretation as application hypothesis, not mathematical consequence.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Connected components partition an undirected graph into maximal mutually reachable sets; strongly connected components (SCC) do analogous mutual reachability for directed graphs.
- **Use when:** ใช้กับ network segmentation, reachability structure, cycle/dependency analysis.
- **Main caution:** interpret SCC as “people with common interests” without validation.

## Related Notes

- [[Graph Analytics and Property Graphs]]
- [[Breadth-First Search]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 9 - Graph Analytics]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
