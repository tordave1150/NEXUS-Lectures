---
title: "Hive Tables Partitions and Buckets"
topic_number: 95
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - hive
  - partitioning
  - bucketing
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Hive Tables Partitions and Buckets

> [!abstract] Summary
> Hive จัดข้อมูลผ่าน tables, partitions และ buckets เพื่อ map logical schema ไปยัง physical layout และลดงาน scan/shuffle ในบาง query patterns.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Table = logical relation backed by files/locations.
- Partition = directory-level segmentation by partition keys.
- Bucket = hash-based subdivision into files.
- SORT/CLUSTER choices มีผลต่อ specific operations.

## Technical Detail

Partition pruning ช่วยอ่านเฉพาะ partitions ที่ filter ตรง predicate. Bucketing ไม่ใช่ replacement ของ partitioning; เหมาะกับ different query/join/sampling patterns และต้องสอดคล้องกับ engine behavior.

## Practical Example

Sales partitioned by country/year/month ทำให้ query เดือนเดียวไม่ต้อง scan ทุกเดือน ถ้า optimizer/pruning ใช้ได้.

## When to use

ใช้เมื่อ table ใหญ่และมี predictable filter keys หรือ join patterns.

## Limitations / Assumptions

- Over-partitioning สร้าง metadata/small-files overhead.
- High-cardinality partition keys อาจแย่.

## Common Mistakes

- partition ตาม user_id ที่มีล้านค่าโดยไม่คิด overhead.
- คิดว่า bucket รับประกัน query เร็วทุกกรณี.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture บอก “SORT BY → binary search within bucket” แบบ simplified; canonical note ไม่รับประกัน implementation/performance mechanism แบบนั้น universally.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Hive จัดข้อมูลผ่าน tables, partitions และ buckets เพื่อ map logical schema ไปยัง physical layout และลดงาน scan/shuffle ในบาง query patterns.
- **Use when:** ใช้เมื่อ table ใหญ่และมี predictable filter keys หรือ join patterns.
- **Main caution:** partition ตาม user_id ที่มีล้านค่าโดยไม่คิด overhead.

## Related Notes

- [[Apache Hive]]
- [[Hive SerDe and Schema-on-Read]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 2 - Hive]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
