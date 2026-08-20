---
title: "HDFS"
topic_number: 91
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - hdfs
  - distributed-storage
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# HDFS

> [!abstract] Summary
> HDFS (Hadoop Distributed File System) เป็น distributed file system สำหรับเก็บไฟล์ขนาดใหญ่เป็น blocks กระจายบน cluster พร้อม redundancy/recovery และ metadata coordination.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- NameNode จัดการ namespace/metadata และ block locations.
- DataNodes เก็บ blocks จริง.
- Files ถูกแบ่งเป็น blocks และกระจาย.
- Data locality ช่วยให้ compute ใกล้ storage.
- HDFS เหมาะกับ large sequential access มากกว่า low-latency random record updates.

## Technical Detail

Client ขอ metadata จาก NameNode แล้วสื่อสารกับ DataNodes สำหรับ data transfer. Fault tolerance เกิดจาก redundancy เช่น replication หรือ erasure coding ตาม deployment/configuration.

## Practical Example

ไฟล์ 500 MB อาจถูกแบ่งหลาย blocks แล้ววางบนหลาย DataNodes; compute engine สามารถ schedule tasks ใกล้ blocks เหล่านั้น.

## When to use

เหมาะกับ large analytical datasets, batch/scan-heavy workloads และ distributed compute storage.

## Limitations / Assumptions

- ไม่เหมาะกับ huge number of tiny files.
- ไม่ใช่ transactional database.
- block size/replication/EC เป็น configuration และ version/deployment dependent.

## Common Mistakes

- คิดว่า Secondary NameNode คือ hot backup ของ NameNode.
- ตีความ WORM แบบเข้มจนคิดว่า HDFS ไม่มี append ในทุก version/use case.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture ถูกต้องที่ Secondary NameNode เน้น checkpointing ไม่ใช่ backup. Canonical note หลีกเลี่ยงตัวเลข block size/default ที่ผูกกับ version.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** HDFS (Hadoop Distributed File System) เป็น distributed file system สำหรับเก็บไฟล์ขนาดใหญ่เป็น blocks กระจายบน cluster พร้อม redundancy/recovery และ metadata coordination.
- **Use when:** เหมาะกับ large analytical datasets, batch/scan-heavy workloads และ distributed compute storage.
- **Main caution:** คิดว่า Secondary NameNode คือ hot backup ของ NameNode.

## Related Notes

- [[Hadoop Ecosystem]]
- [[MapReduce]]
- [[Apache Hive]]
- [[Apache HBase]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 1 - Hadoop]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 1 Lab - Hadoop]] | Relevant lecture/lab section | Concept, examples, caveats |

## External Verification

> [!cite] Verified with official Apache Hadoop documentation
> Apache Hadoop's HDFS Architecture documentation confirms the NameNode/DataNode block architecture and clarifies the coherency model: HDFS files are primarily write-once/read-many, **but current HDFS supports appends and truncates**. Therefore the lecture's absolute "no appends" wording is retained only as historical simplification.
>
> Reference: [Apache Hadoop — HDFS Architecture](https://hadoop.apache.org/docs/stable/hadoop-project-dist/hadoop-hdfs/HdfsDesign.html)

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
