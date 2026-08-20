---
title: "Apache Sqoop (Legacy)"
topic_number: 101
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - sqoop
  - legacy
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Apache Sqoop (Legacy)

> [!abstract] Summary
> Sqoop เป็นเครื่องมือ historical Hadoop ecosystem สำหรับ bulk transfer ระหว่าง relational databases กับ HDFS/Hive/HBase โดย leverage parallel import/export jobs.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Reads RDBMS metadata/schema.
- Parallelizes bulk import with mapper tasks.
- Targets HDFS/Hive/HBase in lecture examples.

## Technical Detail

Conceptual value คือ pattern **bulk RDBMS ↔ distributed storage transfer**. อย่างไรก็ตาม lab commands/versions ใน source เป็น legacy environment จึงควรเรียนเป็น historical tool pattern มากกว่าคู่มือ production ปัจจุบัน.

## Practical Example

MySQL table → Sqoop import → HDFS directory หรือ Hive/HBase target.

## When to use

ใช้เพื่อเข้าใจ historical Hadoop ingestion architecture และอ่านระบบ legacy.

## Limitations / Assumptions

- Version/connector compatibility สำคัญ.
- ไม่เหมาะกับ continuous streaming.

## Common Mistakes

- นำ password ใส่ command line production.
- ใช้ lab command โดยไม่ตรวจ compatibility.

## Cross-check / Corrections

> [!warning] Source cross-check
> Note นี้ตั้งชื่อ `(Legacy)` โดยเจตนา เนื่องจาก source เป็น old Hadoop distribution workflow; ไม่ใช้เป็น default recommendation สำหรับ greenfield systems.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Sqoop เป็นเครื่องมือ historical Hadoop ecosystem สำหรับ bulk transfer ระหว่าง relational databases กับ HDFS/Hive/HBase โดย leverage parallel import/export jobs.
- **Use when:** ใช้เพื่อเข้าใจ historical Hadoop ingestion architecture และอ่านระบบ legacy.
- **Main caution:** นำ password ใส่ command line production.

## Related Notes

- [[Data Ingestion for Big Data]]
- [[Apache Kafka]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 4 - Data Ingestion]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 4 Lab - Data Ingestion]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
