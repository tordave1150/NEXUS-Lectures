---
title: "HBase Data Model and Row Key Design"
topic_number: 98
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - hbase
  - row-key
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# HBase Data Model and Row Key Design

> [!abstract] Summary
> Row key เป็น primary access/indexing dimension ของ HBase; design ที่ดีต้อง balance scan locality, key distribution และ hotspot avoidance.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Rows sorted lexicographically by row key.
- Column families fixed at schema level; qualifiers can vary.
- Cells can keep multiple timestamped versions.
- Sequential keys can create write hotspots.

## Technical Detail

Row-key design มัก encode dimensions ที่สอดคล้องกับ access pattern เช่น tenant/entity/time แต่ต้องระวัง monotonic prefix. Techniques อาจรวม salting/hashing/reversing/prefix design ขึ้นกับ workload.

## Practical Example

ถ้าใช้ timestamp increasing เป็น prefix ของ row key, writes ล่าสุดอาจไปรวม region เดียว; hash/salt prefix สามารถกระจาย writes แต่ทำ range scan ซับซ้อนขึ้น.

## When to use

ใช้เมื่อออกแบบ HBase table schema และ query pattern.

## Limitations / Assumptions

- ไม่มี universal “best row key”.
- Salt/hash ช่วย distribute แต่เสีย natural range locality.

## Common Mistakes

- ใช้ random UUID เสมอโดยไม่ดู range query.
- ใช้ timestamp prefix เสมอจน hotspot.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture เน้น lexicographic sorting/hotspot ได้ดี; canonical note เพิ่ม trade-off locality vs distribution.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Row key เป็น primary access/indexing dimension ของ HBase; design ที่ดีต้อง balance scan locality, key distribution และ hotspot avoidance.
- **Use when:** ใช้เมื่อออกแบบ HBase table schema และ query pattern.
- **Main caution:** ใช้ random UUID เสมอโดยไม่ดู range query.

## Related Notes

- [[Apache HBase]]
- [[HBase Storage Engine]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 3 - HBase]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 3 Lab - HBase]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
