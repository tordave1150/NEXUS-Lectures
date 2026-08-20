---
title: "Spark Shared Variables"
topic_number: 108
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - spark
  - broadcast
  - accumulator
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Spark Shared Variables

> [!abstract] Summary
> Spark มี shared-variable patterns สำหรับ distributed closures: broadcast variables กระจาย read-only data ไป workers อย่างมีประสิทธิภาพ และ accumulators รวม associative updates กลับเป็น metrics/counters.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Broadcast: efficient read-only shared lookup/reference data.
- Accumulator: add-only/associative aggregation semantics for counters/metrics.

## Technical Detail

Closure variables ปกติถูก serialize/copy ไป tasks; การแก้ Python/global variable ใน worker ไม่ได้กลายเป็น shared mutable state แบบ single process.

## Practical Example

broadcast lookup dictionary ให้ executors ใช้ enrich records; accumulator นับ malformed rows.

## When to use

ใช้เมื่อต้อง share small reference data หรือ collect distributed metrics.

## Limitations / Assumptions

- Broadcast object ต้องเล็กพอเหมาะ.
- Accumulator updates และ task retries ต้องตีความอย่างระวัง; ไม่ควรใช้เป็น business-result source of truth.

## Common Mistakes

- แก้ global variable ใน closure แล้วคาดว่า driver เห็น deterministic shared state.
- broadcast dataset ใหญ่เกิน memory.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lab ใช้ `global c` กับ accumulator syntax เก่า; canonical note เน้น semantics มากกว่าคัดลอก syntax version-specific.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Spark มี shared-variable patterns สำหรับ distributed closures: broadcast variables กระจาย read-only data ไป workers อย่างมีประสิทธิภาพ และ accumulators รวม associative updates กลับเป็น metrics/counters.
- **Use when:** ใช้เมื่อต้อง share small reference data หรือ collect distributed metrics.
- **Main caution:** แก้ global variable ใน closure แล้วคาดว่า driver เห็น deterministic shared state.

## Related Notes

- [[Apache Spark]]
- [[Spark RDD]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 5 - Spark]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 5 Lab - Spark]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
