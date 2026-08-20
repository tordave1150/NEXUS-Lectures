---
title: "Apache Avro"
topic_number: 104
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - avro
  - serialization
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Apache Avro

> [!abstract] Summary
> Avro เป็น schema-based data serialization format/protocol ที่ใช้ compact binary encoding และเก็บ/แลก schema เพื่อช่วย interoperability และ schema evolution ใน data pipelines.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Schema expressed in JSON.
- Binary serialization is compact.
- Container files can carry schema metadata.
- RPC/protocol support exists in ecosystem.

## Technical Detail

ประเด็นสำคัญไม่ใช่แค่ “binary vs text” แต่คือ contract ระหว่าง writer/reader schemas และ rules ของ schema evolution.

## Practical Example

Event records serialize ด้วย Avro schema ก่อนส่ง/เก็บ; downstream reader ใช้ compatible schema อ่าน fields.

## When to use

เหมาะกับ structured event/data exchange ที่ต้องการ compact representation + explicit schema.

## Limitations / Assumptions

- Schema evolution ต้องออกแบบ compatibility.
- Avro ไม่ใช่ message broker.

## Common Mistakes

- คิดว่า schema stored with every individual record.
- สับสน Avro file format กับ Kafka/Flume transport.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture อธิบาย self-describing Avro Data File; canonical note แยก serialization format ออกจาก transport layer ให้ชัด.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Avro เป็น schema-based data serialization format/protocol ที่ใช้ compact binary encoding และเก็บ/แลก schema เพื่อช่วย interoperability และ schema evolution ใน data pipelines.
- **Use when:** เหมาะกับ structured event/data exchange ที่ต้องการ compact representation + explicit schema.
- **Main caution:** คิดว่า schema stored with every individual record.

## Related Notes

- [[Data Ingestion for Big Data]]
- [[Apache Kafka]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 4 - Data Ingestion]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
