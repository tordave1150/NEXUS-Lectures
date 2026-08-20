---
title: "Triangle Count and Clustering Coefficient"
topic_number: 123
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - triangle-count
  - clustering-coefficient
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Triangle Count and Clustering Coefficient

> [!abstract] Summary
> Triangle count measures local closed triplets; local clustering coefficient normalizes observed connections among a vertex’s neighbors by the number possible, indicating local transitivity/cohesiveness.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Triangle = three mutually connected vertices in an undirected simple-graph interpretation.
- Local coefficient often \(C_v=2T_v/[d_v(d_v-1)]\) for undirected simple graph.
- Graph-level coefficient has multiple definitions.

## Technical Detail

Formula depends on directed/undirected and graph conventions. Do not apply a single coefficient formula to multigraph/directed graphs without defining treatment.

## Practical Example

If degree d=4 and vertex participates in T=3 neighbor-neighbor triangles, local coefficient = 2×3/(4×3)=0.5.

## When to use

ใช้วัด local closure, network transitivity และ feature engineering.

## Limitations / Assumptions

- High triangle count partly driven by degree.
- Coefficient undefined/defined specially for degree <2 depending convention.

## Common Mistakes

- compare raw triangle counts across very different degree nodes.
- use formula without defining graph type.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture formula extraction is visually ambiguous; canonical note writes standard undirected simple-graph local coefficient explicitly and flags convention dependence.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Triangle count measures local closed triplets; local clustering coefficient normalizes observed connections among a vertex’s neighbors by the number possible, indicating local transitivity/cohesiveness.
- **Use when:** ใช้วัด local closure, network transitivity และ feature engineering.
- **Main caution:** compare raw triangle counts across very different degree nodes.

## Related Notes

- [[Graph Analytics and Property Graphs]]
- [[Label Propagation]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 9 - Graph Analytics]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
