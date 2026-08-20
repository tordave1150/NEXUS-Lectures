---
title: "Spark RDD"
topic_number: 106
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - spark
  - rdd
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Spark RDD

> [!abstract] Summary
> RDD (Resilient Distributed Dataset) เป็น immutable distributed collection abstraction ของ Spark ที่ partition ข้อมูลและจำ lineage เพื่อ recompute lost partitions.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Immutable: transformations create new RDDs.
- Partitioned across executors.
- Lineage supports fault recovery.
- Can persist/cache with storage levels.

## Technical Detail

RDD API ให้ functional operations และ control ที่ low-level กว่า DataFrames แต่ไม่มี schema/optimizer benefits แบบ structured APIs.

## Practical Example

`textFile(...).flatMap(...).map(...).reduceByKey(...)` เป็น classic RDD word-count pipeline.

## When to use

ใช้เมื่อต้อง low-level distributed transformations, custom partitioned objects หรือทำความเข้าใจ Spark internals.

## Limitations / Assumptions

- Less optimizer/schema support than DataFrame APIs.
- Python object serialization overhead can matter.

## Common Mistakes

- บอกว่า RDD “stored in memory by default” เสมอ — RDD is lazily computed; persistence happens when explicitly cached/persisted or needed in execution.
- เรียก reduceByKey เป็น action.

## Cross-check / Corrections

> [!warning] Source cross-check
> แก้ lecture จุดสำคัญ: `reduceByKey` เป็น transformation (shuffle transformation), ไม่ใช่ action; `collect`, `count`, `saveAsTextFile` เป็น actions.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** RDD (Resilient Distributed Dataset) เป็น immutable distributed collection abstraction ของ Spark ที่ partition ข้อมูลและจำ lineage เพื่อ recompute lost partitions.
- **Use when:** ใช้เมื่อต้อง low-level distributed transformations, custom partitioned objects หรือทำความเข้าใจ Spark internals.
- **Main caution:** บอกว่า RDD “stored in memory by default” เสมอ — RDD is lazily computed; persistence happens when explicitly cached/persisted or needed in execution.

## Related Notes

- [[Apache Spark]]
- [[Spark Transformations Actions and Lazy Evaluation]]
- [[Spark Shared Variables]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 5 - Spark]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 5 Lab - Spark]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
