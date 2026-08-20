---
title: "Hive SerDe and Schema-on-Read"
topic_number: 96
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - serde
  - schema-on-read
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Hive SerDe and Schema-on-Read

> [!abstract] Summary
> SerDe (Serializer/Deserializer) แปลง bytes/records ระหว่าง physical file format กับ logical columns ของ Hive; schema-on-read หมายถึง schema ถูกใช้ตอน query/read มากกว่าการบังคับทุก record ตอน ingest.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- SerDe parse/serialize records.
- RegexSerDe ใช้ regular expressions กับ log-like text.
- Schema mismatch อาจให้ null/error/parse issues ตาม SerDe/type behavior.

## Technical Detail

แนวคิด schema-on-read ให้ flexibility แต่ย้ายความเสี่ยง data quality ไปที่ query time; production pipeline จึงควรมี validation contracts แม้ storage layer ยืดหยุ่น.

## Practical Example

Apache log text ถูก parse เป็น host/request/status ผ่าน RegexSerDe แล้ว SQL aggregate ได้.

## When to use

เหมาะกับ semi-structured/raw files ที่ต้อง query ด้วย SQL abstraction.

## Limitations / Assumptions

- Complex regex fragile และ costly.
- Schema-on-read ไม่ได้แปลว่า “ไม่ต้องมี schema governance”.

## Common Mistakes

- ปล่อย malformed data โดยไม่มี validation.
- ใช้ regex ซับซ้อนแทน structured formats เมื่อมี schema-native option.

## Cross-check / Corrections

> [!warning] Source cross-check
> Canonical note เก็บ RegexSerDe lab เป็น example แต่ไม่แนะนำให้เป็น default ingestion pattern สำหรับทุก workload.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** SerDe (Serializer/Deserializer) แปลง bytes/records ระหว่าง physical file format กับ logical columns ของ Hive; schema-on-read หมายถึง schema ถูกใช้ตอน query/read มากกว่าการบังคับทุก record ตอน ingest.
- **Use when:** เหมาะกับ semi-structured/raw files ที่ต้อง query ด้วย SQL abstraction.
- **Main caution:** ปล่อย malformed data โดยไม่มี validation.

## Related Notes

- [[Apache Hive]]
- [[Data Ingestion for Big Data]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 2 - Hive]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 2 Lab - Hive]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
