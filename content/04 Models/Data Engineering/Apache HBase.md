---
title: "Apache HBase"
topic_number: 97
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - hbase
  - nosql
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Apache HBase

> [!abstract] Summary
> HBase เป็น distributed wide-column / column-family NoSQL database ที่ให้ row-key-based random read/write และ sparse, flexible columns บน large distributed datasets.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Rows identified by byte-array row keys.
- Columns grouped into column families.
- Cells versioned by timestamp.
- Tables partition into regions served by RegionServers.
- Designed for key/range access, not relational joins.

## Technical Detail

HBase data model นิยมเขียนเป็น `(row key, family:qualifier, timestamp) -> value`. Physical design โดยเฉพาะ row key มีผลต่อ locality, range scans และ hotspot risk.

## Practical Example

Event/customer profile table อาจใช้ customer_id เป็น row key และ column families แยก profile/activity.

## When to use

เหมาะกับ sparse/wide data และ low-latency key/range access บน distributed storage.

## Limitations / Assumptions

- ไม่รองรับ relational joins แบบ RDBMS.
- Schema design ต้องคิด access pattern ล่วงหน้า โดยเฉพาะ row key.

## Common Mistakes

- เรียก HBase ว่า “column-oriented” เหมือน analytical columnar file format; ควรใช้ wide-column/column-family ชัดกว่า.
- คิดว่า schema-less = ไม่มี schema design.

## Cross-check / Corrections

> [!warning] Source cross-check
> Canonical note ใช้คำ **wide-column / column-family** เพื่อแยกจาก columnar analytics formats เช่น Parquet.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** HBase เป็น distributed wide-column / column-family NoSQL database ที่ให้ row-key-based random read/write และ sparse, flexible columns บน large distributed datasets.
- **Use when:** เหมาะกับ sparse/wide data และ low-latency key/range access บน distributed storage.
- **Main caution:** เรียก HBase ว่า “column-oriented” เหมือน analytical columnar file format; ควรใช้ wide-column/column-family ชัดกว่า.

## Related Notes

- [[HBase Data Model and Row Key Design]]
- [[HBase Storage Engine]]
- [[HDFS]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 3 - HBase]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 3 Lab - HBase]] | Relevant lecture/lab section | Concept, examples, caveats |

## External Verification

> [!cite] Verified with official Apache HBase documentation
> The current HBase Reference Guide confirms lexicographic row-key ordering and emphasizes that row-key design directly affects scans and hotspotting. This supports treating row-key design as a first-class physical design decision rather than a cosmetic identifier.
>
> Reference: [Apache HBase Reference Guide](https://hbase.apache.org/book.html)

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
