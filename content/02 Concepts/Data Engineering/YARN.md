---
title: "YARN"
topic_number: 92
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - yarn
  - resource-management
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# YARN

> [!abstract] Summary
> YARN แยก cluster resource management ออกจาก application-specific computation โดยมี ResourceManager, per-application coordination และ NodeManagers บน workers.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- ResourceManager ดู resource allocation/scheduling ระดับ cluster.
- ApplicationMaster coordinate application หนึ่งตัว.
- NodeManager ดู containers/tasks/resources บน worker node.

## Technical Detail

แนวคิดหลักคือ compute frameworks หลายชนิดสามารถ share cluster ผ่าน resource abstraction ได้ แทนการผูก storage กับ MapReduce engine อย่างเดียว.

## Practical Example

Spark application บน YARN ขอ resources จาก ResourceManager แล้ว executors ทำงานบน worker nodes.

## When to use

ใช้เมื่อทำความเข้าใจ resource scheduling บน Hadoop cluster.

## Limitations / Assumptions

- รายละเอียด deployment/security/scheduler ต่างตาม cluster distribution.
- YARN ไม่ใช่ storage layer.

## Common Mistakes

- สับสน ResourceManager กับ HDFS NameNode.
- คิดว่า ApplicationMaster = application driver ในทุก framework แบบหนึ่งต่อหนึ่งโดยไม่มี nuance.

## Cross-check / Corrections

> [!warning] Source cross-check
> Canonical note แยกหน้าที่ YARN กับ HDFS ชัดเจน เพื่อไม่ให้ “Hadoop architecture” ถูกมองเป็น process ชุดเดียว.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** YARN แยก cluster resource management ออกจาก application-specific computation โดยมี ResourceManager, per-application coordination และ NodeManagers บน workers.
- **Use when:** ใช้เมื่อทำความเข้าใจ resource scheduling บน Hadoop cluster.
- **Main caution:** สับสน ResourceManager กับ HDFS NameNode.

## Related Notes

- [[HDFS]]
- [[Apache Spark]]
- [[MapReduce]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 1 - Hadoop]] | Relevant lecture/lab section | Concept, examples, caveats |

## External Verification

> [!cite] Verified with official Apache Hadoop documentation
> Current YARN documentation retains the core roles used in this note: the **ResourceManager** arbitrates cluster resources, the per-application **ApplicationMaster** negotiates resources and coordinates application execution, and each **NodeManager** manages containers/resources on its machine.
>
> Reference: [Apache Hadoop — YARN](https://hadoop.apache.org/docs/current/hadoop-yarn/hadoop-yarn-site/YARN.html)

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
