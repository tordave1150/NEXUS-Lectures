---
title: "Apache Kafka"
topic_number: 103
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - kafka
  - event-streaming
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Apache Kafka

> [!abstract] Summary
> Kafka เป็น distributed event streaming platform ที่จัด records เป็น topics/partitions; producers publish, consumers read ผ่าน offsets และ consumer groups เพื่อ scale processing.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Topic split into partitions.
- Ordering is naturally scoped within a partition.
- Offset identifies position in a partition log.
- Consumer group distributes partitions among members.
- Replication provides fault tolerance.

## Technical Detail

Partition key เป็น design decision สำคัญ: records ที่ต้องรักษา order ต่อ entity ควร route ไป partition เดียวกันตาม key. Throughput/parallelism เพิ่มได้ด้วย partitions แต่ global ordering ลดลง.

## Practical Example

Orders keyed by customer_id → same customer events routed consistently → consumer group processes partitions in parallel.

## When to use

เหมาะกับ event-driven architectures, streaming ingestion, replayable event pipelines และ decoupling producers/consumers.

## Limitations / Assumptions

- จำนวน partitions มี operational cost.
- Ordering ไม่ global across partitions.
- Delivery semantics ต้องพิจารณา producer/broker/consumer/end-to-end.

## Common Mistakes

- คิดว่า consumer group = broadcast; ในกลุ่มเดียว records ถูกแบ่งงานกัน.
- ใช้ ZooKeeper/Kafka 0.9 lab commands เป็น current instructions.

## Cross-check / Corrections

> [!warning] Source cross-check
> Source lecture/lab เป็น ZooKeeper-era Kafka และ lab ใช้ Kafka 0.9.0.1. Canonical note เก็บ core topic/partition/group model แต่ระบุคำสั่งนั้นเป็น legacy อย่างชัดเจน.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Kafka เป็น distributed event streaming platform ที่จัด records เป็น topics/partitions; producers publish, consumers read ผ่าน offsets และ consumer groups เพื่อ scale processing.
- **Use when:** เหมาะกับ event-driven architectures, streaming ingestion, replayable event pipelines และ decoupling producers/consumers.
- **Main caution:** คิดว่า consumer group = broadcast; ในกลุ่มเดียว records ถูกแบ่งงานกัน.

## Related Notes

- [[Data Ingestion for Big Data]]
- [[Apache Avro]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 4 - Data Ingestion]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 4 Lab - Data Ingestion]] | Relevant lecture/lab section | Concept, examples, caveats |

## External Verification

> [!cite] Verified with official Apache Kafka documentation
> The course lab uses Kafka 0.9.0.1 and ZooKeeper-era commands. Apache Kafka **4.0** became the first major release operating entirely without ZooKeeper and runs in **KRaft** mode. The topic/partition/offset/consumer-group concepts remain useful, but ZooKeeper-based setup commands are historical.
>
> Reference: [Apache Kafka 4.0 Release Announcement](https://kafka.apache.org/blog/2025/03/18/apache-kafka-4.0.0-release-announcement/)

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
