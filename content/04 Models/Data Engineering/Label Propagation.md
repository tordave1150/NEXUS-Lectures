---
title: "Label Propagation"
topic_number: 124
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - label-propagation
  - community-detection
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Label Propagation

> [!abstract] Summary
> Label Propagation Algorithm (LPA) สำหรับ community detection เริ่มด้วย labels บน vertices แล้วอัปเดตแต่ละ vertex ตาม labels ของ neighbors จน stabilize หรือถึง iteration limit.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Initialize labels.
- Propagate majority neighbor label.
- Repeat iteratively.
- Can be fast and scalable but unstable/tie-sensitive.

## Technical Detail

มี “label propagation” หลาย formulations. Community-detection LPA แบบ unsupervised ไม่เหมือน semi-supervised classification algorithm ทุกตัวที่ใช้ชื่อ label propagation.

## Practical Example

Communities in social graph emerge as neighboring vertices converge to common labels.

## When to use

ใช้สำหรับ fast exploratory community detection.

## Limitations / Assumptions

- Can produce different partitions across runs/order/ties.
- May collapse into giant community.

## Common Mistakes

- เรียก LPA เป็น semi-supervised โดยอัตโนมัติใน context community detection.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture ผสมคำอธิบาย semi-supervised label propagation กับ graph community LPA; canonical note แยกสองบริบทและ note นี้เน้น community-detection variant.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Label Propagation Algorithm (LPA) สำหรับ community detection เริ่มด้วย labels บน vertices แล้วอัปเดตแต่ละ vertex ตาม labels ของ neighbors จน stabilize หรือถึง iteration limit.
- **Use when:** ใช้สำหรับ fast exploratory community detection.
- **Main caution:** เรียก LPA เป็น semi-supervised โดยอัตโนมัติใน context community detection.

## Related Notes

- [[Graph Analytics and Property Graphs]]
- [[GraphX and GraphFrames]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 9 - Graph Analytics]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
