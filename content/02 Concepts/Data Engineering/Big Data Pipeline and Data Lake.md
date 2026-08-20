---
title: "Big Data Pipeline and Data Lake"
topic_number: 88
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - data-pipeline
  - data-lake
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Big Data Pipeline and Data Lake

> [!abstract] Summary
> Big Data pipeline เชื่อม ingestion → staging/transform/storage → computation/analytics → workflow management/operationalization; Data Lake เป็น storage layer ที่รองรับข้อมูลหลายรูปแบบก่อนนำไป curate ต่อ.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Ingestion นำข้อมูลเข้า platform.
- Staging/transform ทำข้อมูลให้พร้อมใช้และจัดเก็บ.
- Computation สร้าง model/insight.
- Workflow management ทำ orchestration, scheduling, retry, monitoring.
- Data Lake เก็บ raw/curated data ได้หลายรูปแบบ.

## Technical Detail

อย่าเท่ากับ ETL เพียงอย่างเดียว: pipeline สมัยใหม่มักมี batch + streaming, metadata, quality checks, observability และ governance. Data lake คือ storage/organization concept; data warehouse คือ curated analytical serving model — ทั้งสองอยู่ร่วมกันได้.

## Practical Example

Raw web logs → ingest → object/distributed storage → clean/partition → Spark transform → feature table → model/dashboard.

## When to use

ใช้เมื่อต้องออกแบบ end-to-end data flow และกำหนด ownership/quality checkpoints.

## Limitations / Assumptions

- “Data lake” ที่ไร้ metadata/governance อาจกลายเป็น data swamp.
- Pipeline architecture ขึ้นกับ latency, consistency, cost และ consumer needs.

## Common Mistakes

- คิดว่า data lake “แทน” warehouse เสมอ.
- ละเลย schema evolution และ lineage.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture อธิบาย data lake → ETL → warehouse/mart; canonical note ขยายว่า lake/warehouse เป็น complementary patterns มากกว่าความสัมพันธ์แทนที่กัน.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Big Data pipeline เชื่อม ingestion → staging/transform/storage → computation/analytics → workflow management/operationalization; Data Lake เป็น storage layer ที่รองรับข้อมูลหลายรูปแบบก่อนนำไป curate ต่อ.
- **Use when:** ใช้เมื่อต้องออกแบบ end-to-end data flow และกำหนด ownership/quality checkpoints.
- **Main caution:** คิดว่า data lake “แทน” warehouse เสมอ.

## Related Notes

- [[Data Ingestion for Big Data]]
- [[Apache Spark]]
- [[Apache Hive]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 1 - Hadoop]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
