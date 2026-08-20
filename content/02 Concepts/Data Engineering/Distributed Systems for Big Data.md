---
title: "Distributed Systems for Big Data"
topic_number: 89
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - distributed-systems
  - big-data
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Distributed Systems for Big Data

> [!abstract] Summary
> Distributed data processing แบ่งข้อมูลและ computation ไปหลาย nodes เพื่อ scale throughput/capacity พร้อมจัดการ failure, data locality และ coordination.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Fault tolerance: component failure ไม่ควรทำให้ทั้งระบบล้ม.
- Recoverability: ต้องกู้ data/computation ได้.
- Scalability: เพิ่ม resources แล้วรองรับ load เพิ่ม.
- Data locality ลด network transfer.
- Parallel tasks ควรลด unnecessary coordination.

## Technical Detail

หลักสำคัญคือ trade-off ระหว่าง parallelism กับ communication. งานที่ต้อง shuffle/coordinate มากมักถูกจำกัดด้วย network/serialization มากกว่าจำนวน CPU เพียงอย่างเดียว.

## Practical Example

Word count สามารถแบ่ง file blocks ให้ workers map locally แล้ว shuffle ตาม key ก่อน aggregate.

## When to use

ใช้เป็น mental model ก่อนเรียน HDFS/YARN/MapReduce/Spark.

## Limitations / Assumptions

- Distributed systems เพิ่ม operational complexity.
- Network partitions, skew, stragglers และ partial failure เป็น first-class concerns.

## Common Mistakes

- คิดว่าเพิ่ม nodes แล้ว speed จะ linear เสมอ.
- มองข้าม data skew และ shuffle cost.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture เน้น “tasks independent / no communication” ซึ่งเหมาะกับ MapReduce intuition แต่ distributed workloads ทั่วไปอาจต้อง communication; canonical note จึงไม่ generalize ข้อนี้เป็น universal rule.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Distributed data processing แบ่งข้อมูลและ computation ไปหลาย nodes เพื่อ scale throughput/capacity พร้อมจัดการ failure, data locality และ coordination.
- **Use when:** ใช้เป็น mental model ก่อนเรียน HDFS/YARN/MapReduce/Spark.
- **Main caution:** คิดว่าเพิ่ม nodes แล้ว speed จะ linear เสมอ.

## Related Notes

- [[HDFS]]
- [[YARN]]
- [[MapReduce]]
- [[Apache Spark]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 1 - Hadoop]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
