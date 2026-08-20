---
title: "Alternating Least Squares Recommendation"
topic_number: 111
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - als
  - recommendation
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Alternating Least Squares Recommendation

> [!abstract] Summary
> ALS เป็น matrix-factorization approach สำหรับ collaborative filtering ที่ประมาณ latent user/item factors โดยสลับแก้ optimization ของฝั่ง user และ item.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Observed ratings/interactions form sparse user-item matrix.
- Factorize approximately into user factors × item factors.
- Alternate fixing one side and solving the other.
- Distributed formulation เหมาะกับ large sparse interactions.

## Technical Detail

Objective มักรวม squared reconstruction error บน observed interactions + regularization. Implicit-feedback variants ใช้ confidence weighting ต่างจาก explicit ratings.

## Practical Example

ratings `(user,item,rating)` → fit ALS → predict unseen user-item scores → recommend top-N.

## When to use

เหมาะกับ collaborative filtering ที่มี interaction matrix ใหญ่.

## Limitations / Assumptions

- Cold-start users/items.
- Popularity bias and feedback loops.
- Training MSE ไม่เพียงพอสำหรับ ranking/recommendation quality.

## Common Mistakes

- evaluate บน training ratings อย่างเดียวเหมือน lab.
- ใช้ random split โดยเกิด leakage จาก duplicate/time interactions โดยไม่คิด scenario.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lab คำนวณ MSE บน training data; canonical note ระบุว่าควร evaluate on held-out interactions และเลือก ranking/explicit-rating metrics ตาม objective.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** ALS เป็น matrix-factorization approach สำหรับ collaborative filtering ที่ประมาณ latent user/item factors โดยสลับแก้ optimization ของฝั่ง user และ item.
- **Use when:** เหมาะกับ collaborative filtering ที่มี interaction matrix ใหญ่.
- **Main caution:** evaluate บน training ratings อย่างเดียวเหมือน lab.

## Related Notes

- [[Spark ML and MLlib]]
- [[Train Validation Test Split]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 7 - Machine Learning with Spark]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 7 Lab - Machine Learning with Spark]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
