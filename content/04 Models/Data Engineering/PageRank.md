---
title: "PageRank"
topic_number: 122
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - pagerank
  - centrality
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# PageRank

> [!abstract] Summary
> PageRank assigns recursive importance scores in a directed graph: a vertex receives more importance when linked by important vertices, with contribution divided among their outgoing links plus a random-reset/teleportation component.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Recursive link-based centrality.
- Damping factor often denoted d; random reset probability = 1-d under one convention.
- Out-degree normalizes contribution.

## Technical Detail

A canonical form is $PR(v)=(1-d)/N+d\sum_{u\to v} PR(u)/L(u)$, with convention variants. Dangling nodes and normalization require treatment in implementation.

## Practical Example

Web pages or influence graph: a link from a high-ranked low-outdegree source contributes more.

## When to use

ใช้กับ ranking/centrality in directed networks.

## Limitations / Assumptions

- High PageRank ≠ causal influence.
- Sensitive to graph construction and personalization/teleportation setup.

## Common Mistakes

- assume d=0.85 is mathematical law.
- interpret PageRank as community membership.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture says damping “usually 0.85”; canonical note retains as common default heuristic, not universal optimum.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** PageRank assigns recursive importance scores in a directed graph: a vertex receives more importance when linked by important vertices, with contribution divided among their outgoing links plus a random-reset/teleportation component.
- **Use when:** ใช้กับ ranking/centrality in directed networks.
- **Main caution:** assume d=0.85 is mathematical law.

## Related Notes

- [[Graph Analytics and Property Graphs]]
- [[GraphX and GraphFrames]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 9 - Graph Analytics]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
