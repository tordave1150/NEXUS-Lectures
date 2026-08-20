---
title: "Big Data Fundamentals and 5Vs"
topic_number: 87
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - big-data
  - data-engineering
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Big Data Fundamentals and 5Vs

> [!abstract] Summary
> Big Data คือบริบทที่ขนาด ความหลากหลาย ความเร็ว และคุณภาพ/ความไม่แน่นอนของข้อมูลทำให้การจัดเก็บ ประมวลผล และสร้าง value ต้องพึ่ง distributed systems และ specialized data platforms.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Three broad data forms: structured, semi-structured, unstructured.
- 5Vs: Volume, Variety, Velocity, Veracity, Value.
- Big Data ไม่ได้แปลว่า “ไฟล์ใหญ่” อย่างเดียว; ความเร็วและรูปแบบข้อมูลมีผลต่อ architecture ด้วย.

## Technical Detail

มอง 5Vs เป็น **design pressures** ไม่ใช่ checklist ทางคณิตศาสตร์: Volume กดดัน storage/parallelism, Velocity กดดัน ingestion/stream processing, Variety กดดัน schema/modeling, Veracity กดดัน quality/governance, Value เชื่อม technical design กับ business outcome.

## Practical Example

ระบบ clickstream อาจมี JSON events จำนวนมากไหลต่อเนื่อง: Volume/Velocity ต้อง scale ingestion, Variety ต้อง parse semi-structured data, Veracity ต้องจัดการ duplicate/bot events, Value คือ feature/insight ที่นำไปใช้จริง.

## When to use

ใช้เป็นกรอบเริ่มต้นตอนออกแบบ data platform หรืออธิบายว่าทำไม single-node/RDBMS workflow บางแบบไม่เพียงพอ.

## Limitations / Assumptions

- 5Vs เป็น conceptual framework ไม่ใช่มาตรฐานสากลที่กำหนด threshold.
- ข้อมูลไม่จำเป็นต้อง “ใหญ่” ทุก V พร้อมกันจึงจะต้องใช้ distributed architecture.

## Common Mistakes

- คิดว่า Big Data = Hadoop เท่านั้น.
- คิดว่า unstructured data ไม่มี schema — ในทางปฏิบัติมักมี implicit structure/metadata.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture ใช้ 5Vs เป็นนิยามหลัก; canonical note เก็บเป็น heuristic framework ไม่ใช่เกณฑ์ตัดสินแบบตายตัว.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Big Data คือบริบทที่ขนาด ความหลากหลาย ความเร็ว และคุณภาพ/ความไม่แน่นอนของข้อมูลทำให้การจัดเก็บ ประมวลผล และสร้าง value ต้องพึ่ง distributed systems และ specialized data platforms.
- **Use when:** ใช้เป็นกรอบเริ่มต้นตอนออกแบบ data platform หรืออธิบายว่าทำไม single-node/RDBMS workflow บางแบบไม่เพียงพอ.
- **Main caution:** คิดว่า Big Data = Hadoop เท่านั้น.

## Related Notes

- [[Big Data Pipeline and Data Lake]]
- [[Distributed Systems for Big Data]]
- [[Hadoop Ecosystem]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 1 - Hadoop]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
