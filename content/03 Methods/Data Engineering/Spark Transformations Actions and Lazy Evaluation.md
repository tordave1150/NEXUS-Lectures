---
title: "Spark Transformations Actions and Lazy Evaluation"
topic_number: 107
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - spark
  - lazy-evaluation
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Spark Transformations Actions and Lazy Evaluation

> [!abstract] Summary
> Spark แยก transformations ที่สร้าง logical lineage/plan ออกจาก actions ที่ trigger execution/return or persist results; lazy evaluation เปิดโอกาสให้ optimize execution ก่อนรัน.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Transformations: map, filter, flatMap, distinct, reduceByKey, groupByKey เป็นต้น.
- Actions: count, collect, take, reduce, save... เป็นต้น.
- Narrow vs wide dependencies มีผลต่อ shuffle.
- Lazy evaluation means transformations are not immediately executed.

## Technical Detail

Wide transformations เช่น group/reduceByKey มักต้อง shuffle across partitions. `reduceByKey` มักมี pre-aggregation opportunity และดีกว่า `groupByKey` สำหรับ aggregation.

## Practical Example

นับยอดต่อ key: prefer `reduceByKey(sum)` แทน group all values แล้ว sum เมื่อ semantics ตรงกัน.

## When to use

ใช้เพื่อ reason เรื่อง Spark execution, performance และ job boundaries.

## Limitations / Assumptions

- `collect()` อาจทำ driver OOM ถ้าข้อมูลใหญ่.
- Lazy plan ยัง trigger computation เมื่อ action invoked.

## Common Mistakes

- ใช้ collect เพื่อ “ดูทั้งหมด” บน big data.
- สับสน transformation/action.
- ใช้ groupByKey สำหรับ simple aggregation โดยไม่จำเป็น.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture ระบุ `reduceByKey` เป็น action; canonical note แก้เป็น transformation.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Spark แยก transformations ที่สร้าง logical lineage/plan ออกจาก actions ที่ trigger execution/return or persist results; lazy evaluation เปิดโอกาสให้ optimize execution ก่อนรัน.
- **Use when:** ใช้เพื่อ reason เรื่อง Spark execution, performance และ job boundaries.
- **Main caution:** ใช้ collect เพื่อ “ดูทั้งหมด” บน big data.

## Related Notes

- [[Spark RDD]]
- [[Apache Spark]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 5 - Spark]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 5 Lab - Spark]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
