---
title: "MapReduce"
topic_number: 93
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - mapreduce
  - distributed-computing
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# MapReduce

> [!abstract] Summary
> MapReduce เป็น distributed batch computation pattern ที่ map records เป็น intermediate key/value pairs, shuffle/group ตาม key แล้ว reduce เพื่อ aggregate/process ผล.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Map: independent transformation → intermediate key/value.
- Shuffle/sort/group เป็น distributed data movement สำคัญ.
- Reduce: aggregate/process values per key.
- Word count เป็น canonical example.

## Technical Detail

Pipeline: input splits → mapper → optional combiner → partition/shuffle/sort → reducers → output. Cost ใหญ่ของหลาย jobs มาจาก materialization/shuffle/network/disk I/O.

## Practical Example

Word count: map(word→1), group values by word, reduce(sum).

## When to use

เหมาะกับ large batch jobs ที่ express เป็น map + shuffle + reduce ได้ดี.

## Limitations / Assumptions

- ไม่เหมาะกับ iterative/interactive workflows เมื่อแต่ละ stage ต้อง materialize intermediate data.
- Data skew ทำให้ reducer บางตัวช้า.

## Common Mistakes

- เรียก reduceByKey ของ Spark ว่า action — ใน Spark RDD มันเป็น transformation.
- มองข้าม shuffle cost.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture ใช้ MapReduce เป็น contrast กับ Spark; canonical note เก็บ batch model และชี้ว่า framework semantics ของ Spark ไม่เหมือน Hadoop MapReduce แม้ชื่อ operation คล้ายกัน.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** MapReduce เป็น distributed batch computation pattern ที่ map records เป็น intermediate key/value pairs, shuffle/group ตาม key แล้ว reduce เพื่อ aggregate/process ผล.
- **Use when:** เหมาะกับ large batch jobs ที่ express เป็น map + shuffle + reduce ได้ดี.
- **Main caution:** เรียก reduceByKey ของ Spark ว่า action — ใน Spark RDD มันเป็น transformation.

## Related Notes

- [[HDFS]]
- [[Apache Spark]]
- [[Spark Transformations Actions and Lazy Evaluation]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 1 - Hadoop]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 1 Lab - Hadoop]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
