---
title: "Apache Flume"
topic_number: 102
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - flume
  - data-ingestion
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Apache Flume

> [!abstract] Summary
> Flume เป็น event/log ingestion system ใน Hadoop-era architecture โดย model agent เป็น Source → Channel → Sink และสามารถ chain/fan-in agents เพื่อส่ง events ไป storage.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Source receives events.
- Channel buffers/queues events.
- Sink forwards to next agent or storage.
- File channel improves durability relative to volatile buffering.

## Technical Detail

Agent topology แยก event capture ออกจาก persistence destination; channel ทำหน้าที่ decouple source/sink rates บางส่วน. Source lab ใช้ spooldir + Avro + HDFS sink.

## Practical Example

Web-server logs → Flume source → file channel → HDFS sink.

## When to use

ใช้เพื่อเข้าใจ legacy/log ingestion pipelines และ existing Hadoop systems.

## Limitations / Assumptions

- Operational/release relevance ต้องตรวจ current stack.
- Flume architecture ไม่ได้แทน durable event log platform ทุก use case.

## Common Mistakes

- คิดว่า channel = Kafka topic.
- ใช้ chmod 777 / hard-coded lab config ใน production.

## Cross-check / Corrections

> [!warning] Source cross-check
> Canonical note เก็บ source/channel/sink architecture แต่ mark lab setup เป็น legacy, ไม่คัดลอก security-unsafe permissions เป็น recommendation.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Flume เป็น event/log ingestion system ใน Hadoop-era architecture โดย model agent เป็น Source → Channel → Sink และสามารถ chain/fan-in agents เพื่อส่ง events ไป storage.
- **Use when:** ใช้เพื่อเข้าใจ legacy/log ingestion pipelines และ existing Hadoop systems.
- **Main caution:** คิดว่า channel = Kafka topic.

## Related Notes

- [[Data Ingestion for Big Data]]
- [[Apache Kafka]]
- [[Apache Avro]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 4 - Data Ingestion]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 4 Lab - Data Ingestion]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
