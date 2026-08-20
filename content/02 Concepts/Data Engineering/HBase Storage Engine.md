---
title: "HBase Storage Engine"
topic_number: 99
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - hbase
  - storage-engine
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# HBase Storage Engine

> [!abstract] Summary
> HBase write/read path ใช้ WAL, MemStore, HFiles, cache และ compaction เพื่อรองรับ durable writes และ efficient reads บน distributed storage.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- WAL ช่วย durability/recovery.
- MemStore buffer writes in memory.
- Flush สร้าง immutable HFiles.
- BlockCache ช่วย reads.
- Compaction รวม HFiles และจัดการ storage/read amplification.

## Technical Detail

Write path แบบ log + memory buffer + immutable sorted files คล้าย LSM-tree family. Reads อาจตรวจ memory/cache/files หลายชั้น; compaction เป็นกลไกสำคัญในการควบคุม file count และ stale versions/tombstones ตาม policy.

## Practical Example

write → WAL + MemStore → flush → HFile; repeated flushes → compaction.

## When to use

ใช้เพื่อเข้าใจ performance tuning, write amplification/read amplification และ failure recovery.

## Limitations / Assumptions

- Compaction can be I/O intensive.
- Exact cache/compaction behavior is implementation/config dependent.

## Common Mistakes

- บอกว่า major compaction “merge all HFiles into one HFile” เป็นกฎเสมอในทุก current setup.
- คิดว่า HBase update เป็น in-place disk write.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture statement เรื่อง binary search/major compaction ถูกเก็บเป็น conceptual simplification; canonical note ใช้ LSM-style mental model ที่ไม่ผูกกับ exact file count.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** HBase write/read path ใช้ WAL, MemStore, HFiles, cache และ compaction เพื่อรองรับ durable writes และ efficient reads บน distributed storage.
- **Use when:** ใช้เพื่อเข้าใจ performance tuning, write amplification/read amplification และ failure recovery.
- **Main caution:** บอกว่า major compaction “merge all HFiles into one HFile” เป็นกฎเสมอในทุก current setup.

## Related Notes

- [[Apache HBase]]
- [[HBase Data Model and Row Key Design]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 3 - HBase]] | Relevant lecture/lab section | Concept, examples, caveats |

## External Verification

> [!cite] Verified with official Apache HBase documentation
> Current HBase documentation describes the write path as **WAL → MemStore → StoreFiles/HFiles**, with WAL replay supporting recovery when a RegionServer fails before MemStore contents are flushed. Compaction then consolidates StoreFiles over time.
>
> Reference: [Apache HBase — RegionServer / WAL](https://hbase.apache.org/docs/architecture/regionserver/)

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
