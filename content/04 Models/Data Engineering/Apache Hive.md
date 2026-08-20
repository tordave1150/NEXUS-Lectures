---
title: "Apache Hive"
topic_number: 94
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - hive
  - sql
  - data-warehouse
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Apache Hive

> [!abstract] Summary
> Apache Hive เป็น SQL data-warehouse/query layer สำหรับข้อมูลขนาดใหญ่ โดยใช้ metastore/schema/table abstractions เหนือ distributed storage และ execution engines.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- HiveQL ให้ SQL-like interface.
- Metastore เก็บ metadata ของ databases/tables/partitions.
- Managed/external tables ต่างกันที่ lifecycle/ownership ของ data.
- Partitioning/bucketing ช่วย physical organization.

## Technical Detail

Hive แยก logical table metadata ออกจาก physical files. Query planner/engine แปลง SQL เป็น execution plan บน distributed compute engine. ACID/transaction behavior เป็น version/configuration sensitive.

## Practical Example

External table ชี้ไปยัง existing data location; dropping table โดยหลัก conceptual คือ metadata lifecycle ต่างจาก managed table.

## When to use

เหมาะกับ batch/analytical SQL บน large datasets และ shared table metadata.

## Limitations / Assumptions

- ไม่ใช่ low-latency OLTP database.
- Performance ขึ้นกับ file format, partition pruning, engine, statistics และ storage.

## Common Mistakes

- คิดว่า Hive query ทุกครั้ง = MapReduce job เสมอ.
- ใช้ indexing claim จาก lecture โดยไม่ตรวจ version.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture อธิบาย MapReduce-centric execution และ Hive indexes แบบเก่า; canonical note ไม่ผูก Hive กับ MapReduce engine เพียงตัวเดียว และ mark index details เป็น legacy/version-sensitive.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Apache Hive เป็น SQL data-warehouse/query layer สำหรับข้อมูลขนาดใหญ่ โดยใช้ metastore/schema/table abstractions เหนือ distributed storage และ execution engines.
- **Use when:** เหมาะกับ batch/analytical SQL บน large datasets และ shared table metadata.
- **Main caution:** คิดว่า Hive query ทุกครั้ง = MapReduce job เสมอ.

## Related Notes

- [[Hive Tables Partitions and Buckets]]
- [[Hive SerDe and Schema-on-Read]]
- [[HDFS]]
- [[Spark SQL and DataFrames]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 2 - Hive]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 2 Lab - Hive]] | Relevant lecture/lab section | Concept, examples, caveats |

## External Verification

> [!cite] Verified with official Apache Hive documentation
> Hive's official language manual states that the historical Hive indexing feature was **removed in Hive 3.0**. Modern performance work should instead consider techniques such as partition pruning, columnar formats, statistics and materialized views where appropriate; old `CREATE INDEX` material should be treated as legacy.
>
> Reference: [Apache Hive — LanguageManual Indexing](https://hive.apache.org/docs/latest/language/languagemanual-indexing/)

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
