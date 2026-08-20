---
title: "GraphX and GraphFrames"
topic_number: 119
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - graphx
  - graphframes
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# GraphX and GraphFrames

> [!abstract] Summary
> GraphX เป็น Spark graph API บน RDD-oriented abstractions; GraphFrames model vertices/edges as DataFrames เพื่อผสาน graph operations กับ structured Spark APIs.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- GraphX: VertexRDD + Edge/Graph abstractions.
- GraphFrames: vertex DataFrame requires id; edge DataFrame requires src,dst.
- Motif finding/subgraph filters integrate graph patterns with DataFrame expressions.

## Technical Detail

GraphFrames ให้ tabular optimization/query interoperability แต่ package/version compatibility ต้องตรวจ deployment. GraphX/GraphFrames API support differs by language and release.

## Practical Example

vertices DataFrame `(id,name,age)` + edges `(src,dst,relationship)` → GraphFrame → motif/BFS/PageRank.

## When to use

ใช้เมื่อ graph data อยู่ใน Spark ecosystem และต้อง scale graph operations.

## Limitations / Assumptions

- Graph workloads with extreme communication can be expensive.
- GraphFrames often requires separate package/dependency management.

## Common Mistakes

- คิดว่า GraphFrames เป็น rename/replacement ที่ identical กับ GraphX.
- assume every GraphX algorithm exists with same signature in GraphFrames.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture says GraphX “has been developed into GraphFrames”; canonical note avoids implying direct replacement lineage and treats them as related graph APIs with different data abstractions.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** GraphX เป็น Spark graph API บน RDD-oriented abstractions; GraphFrames model vertices/edges as DataFrames เพื่อผสาน graph operations กับ structured Spark APIs.
- **Use when:** ใช้เมื่อ graph data อยู่ใน Spark ecosystem และต้อง scale graph operations.
- **Main caution:** คิดว่า GraphFrames เป็น rename/replacement ที่ identical กับ GraphX.

## Related Notes

- [[Graph Analytics and Property Graphs]]
- [[PageRank]]
- [[Label Propagation]]
- [[Pregel and Graph Message Passing]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 9 - Graph Analytics]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
