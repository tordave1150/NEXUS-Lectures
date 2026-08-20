---
title: "Graph Analytics and Property Graphs"
topic_number: 118
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - graph-analytics
  - property-graph
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Graph Analytics and Property Graphs

> [!abstract] Summary
> Graph analytics models entities as vertices and relationships as edges; property graphs attach attributes/labels to vertices and edges so topology and metadata can be analyzed together.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Directed vs undirected graphs.
- Multigraph allows multiple edges between same vertices.
- Property graph stores vertex/edge attributes.
- Degree, paths, components and motifs are core structures.

## Technical Detail

Graph choice is valuable when relationships are first-class, e.g. social, fraud, dependency, logistics networks. Adjacency structure enables algorithms that tabular joins may express awkwardly.

## Practical Example

Users = vertices, follows = directed edges, edge property = since date.

## When to use

ใช้กับ social network, fraud rings, recommendations, routing, knowledge graphs.

## Limitations / Assumptions

- Graphs can be huge/high-degree/skewed.
- Direction/edge semantics must be explicit.

## Common Mistakes

- discard edge direction inadvertently.
- treat every connected group as a community.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture defines property graph as directed multigraph with data; canonical note preserves this as common property-graph model but notes graph systems may support variants.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Graph analytics models entities as vertices and relationships as edges; property graphs attach attributes/labels to vertices and edges so topology and metadata can be analyzed together.
- **Use when:** ใช้กับ social network, fraud rings, recommendations, routing, knowledge graphs.
- **Main caution:** discard edge direction inadvertently.

## Related Notes

- [[GraphX and GraphFrames]]
- [[Breadth-First Search]]
- [[Connected Components and SCC]]
- [[PageRank]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 9 - Graph Analytics]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
