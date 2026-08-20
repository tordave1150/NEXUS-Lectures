---
title: "Apache Spark"
topic_number: 105
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - spark
  - distributed-computing
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Apache Spark

> [!abstract] Summary
> Apache Spark เป็น distributed compute engine สำหรับ batch/interactive/iterative data processing ที่ใช้ DAG scheduling, lazy transformations และ reusable in-memory/cache abstractions เพื่อหลีกเลี่ยงข้อจำกัดของ multi-stage disk-heavy MapReduce workflows.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Driver defines computation.
- Executors/workers run distributed tasks.
- DAG captures dependencies.
- Caching/persistence can accelerate reuse.
- APIs include DataFrame/SQL, ML, streaming and lower-level RDD.

## Technical Detail

Spark ไม่ได้แปลว่า “ทุกอย่างอยู่ใน RAM”; persistence level, spill, shuffle และ storage ขึ้นกับ workload/configuration. Performance มาจาก optimized execution + avoiding unnecessary materialization, not memory alone.

## Practical Example

Iterative ML repeatedly reuses transformed dataset; caching may avoid re-reading/recomputing expensive stages.

## When to use

เหมาะกับ distributed ETL, SQL analytics, ML pipelines และ iterative processing.

## Limitations / Assumptions

- Shuffle/skew/serialization can dominate runtime.
- Caching data ที่ไม่ reuse อาจเสีย memory.

## Common Mistakes

- เชื่อ claim “10–100x” แบบ universal.
- คิดว่า Spark = storage system.
- คิดว่า RDD always default/best abstraction.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture เน้น RDD-centric Spark; canonical note ให้ RDD เป็น lower-level abstraction และเชื่อม DataFrame/SQL เป็น primary structured-data layer โดยไม่ผูกกับ legacy API style.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Apache Spark เป็น distributed compute engine สำหรับ batch/interactive/iterative data processing ที่ใช้ DAG scheduling, lazy transformations และ reusable in-memory/cache abstractions เพื่อหลีกเลี่ยงข้อจำกัดของ multi-stage disk-heavy MapReduce workflows.
- **Use when:** เหมาะกับ distributed ETL, SQL analytics, ML pipelines และ iterative processing.
- **Main caution:** เชื่อ claim “10–100x” แบบ universal.

## Related Notes

- [[Spark RDD]]
- [[Spark SQL and DataFrames]]
- [[Spark Transformations Actions and Lazy Evaluation]]
- [[Spark ML and MLlib]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 5 - Spark]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 5 Lab - Spark]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
