---
title: "Breadth-First Search"
topic_number: 120
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - bfs
  - graph-algorithms
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Breadth-First Search

> [!abstract] Summary
> Breadth-First Search (BFS) explores graph vertices level by level from a source and yields shortest paths by number of edges in an unweighted graph.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Queue/frontier expansion.
- Visit distance 0,1,2,... levels.
- Shortest path guarantee for unweighted edges.

## Technical Detail

With weighted edges, BFS is generally not a shortest-weight-path algorithm; use algorithms such as Dijkstra when nonnegative edge weights matter.

## Practical Example

Find closest social-network connection from Esther to any user age < 32.

## When to use

ใช้สำหรับ reachability, hop distance, unweighted shortest paths.

## Limitations / Assumptions

- Memory/frontier can explode on high-degree graphs.
- Distributed BFS incurs iterative communication.

## Common Mistakes

- เรียก BFS shortest path โดยไม่ระบุ unweighted/hop-distance assumption.

## Cross-check / Corrections

> [!warning] Source cross-check
> Canonical note adds unweighted shortest-path condition missing from simplified lecture phrasing.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Breadth-First Search (BFS) explores graph vertices level by level from a source and yields shortest paths by number of edges in an unweighted graph.
- **Use when:** ใช้สำหรับ reachability, hop distance, unweighted shortest paths.
- **Main caution:** เรียก BFS shortest path โดยไม่ระบุ unweighted/hop-distance assumption.

## Related Notes

- [[Graph Analytics and Property Graphs]]
- [[GraphX and GraphFrames]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 9 - Graph Analytics]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
