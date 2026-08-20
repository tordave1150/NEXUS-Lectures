---
title: "Data Ingestion for Big Data"
topic_number: 100
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - data-ingestion
  - streaming
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Data Ingestion for Big Data

> [!abstract] Summary
> Data ingestion คือการนำข้อมูลจาก external sources เข้าสู่ storage/processing platform ทั้งแบบ batch และ streaming พร้อมรักษา schema, ordering, durability และ operational reliability ตาม requirement.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Batch ingestion: periodic bulk transfer.
- Streaming ingestion: continuous event flow.
- Source → transport/buffer → sink/storage.
- Design ต้องคิด retries, duplicates, idempotency, schema evolution, backpressure.

## Technical Detail

Ingestion architecture ไม่ได้วัดแค่ throughput; delivery semantics, replay, ordering scope, observability และ security สำคัญต่อ downstream correctness.

## Practical Example

RDBMS snapshot อาจ batch ingest รายคืน; clickstream เข้าผ่าน event broker แบบ streaming.

## When to use

ใช้ตอนออกแบบ data platform entry layer.

## Limitations / Assumptions

- Exactly-once end-to-end เป็น property ที่ต้องพิจารณาทั้ง pipeline ไม่ใช่ broker ตัวเดียว.
- Ordering มักรับประกันใน scope จำกัด เช่น partition/key.

## Common Mistakes

- ใช้ ingestion tool โดยไม่วาง retry/idempotency.
- ไม่เก็บ raw event time/schema version.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture เน้น Sqoop/Flume/Kafka tools; canonical note generalize เป็น ingestion design principles และแยก legacy tools เป็น notes เฉพาะ.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Data ingestion คือการนำข้อมูลจาก external sources เข้าสู่ storage/processing platform ทั้งแบบ batch และ streaming พร้อมรักษา schema, ordering, durability และ operational reliability ตาม requirement.
- **Use when:** ใช้ตอนออกแบบ data platform entry layer.
- **Main caution:** ใช้ ingestion tool โดยไม่วาง retry/idempotency.

## Related Notes

- [[Apache Sqoop (Legacy)]]
- [[Apache Flume]]
- [[Apache Kafka]]
- [[Apache Avro]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 4 - Data Ingestion]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 4 Lab - Data Ingestion]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
