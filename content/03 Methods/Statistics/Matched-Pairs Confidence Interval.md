---
title: "Matched-Pairs Confidence Interval"
topic_number: 140
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - inference
  - paired-data
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Matched-Pairs Confidence Interval

> [!abstract] Summary
> Matched-pairs CI ลด paired observations ให้เป็น difference scores $D_i$ แล้วทำ one-sample t interval บน mean difference $\mu_D$.

## Why this concept matters

เหมาะกับ before/after, twins, matched subjects หรือ repeated measurements สองเวลา ที่แต่ละคู่มีความสัมพันธ์กัน.

## Core Idea

หัวใจคือ unit of analysis = **pair difference**, ไม่ใช่สอง independent samples. Pairing ที่ดีสามารถลด nuisance variation และเพิ่ม precision.

## Mathematical Formulation / Technical Detail

ให้ $D_i=X_i-Y_i$.
CI: $\bar D\pm t_{1-\alpha/2,n-1}S_D/\sqrt n$.

## Worked / Practical Example

คะแนนก่อน/หลังของนักศึกษา 20 คน: คำนวณ difference ของแต่ละคนก่อน แล้วหา mean/SD ของ differences เพื่อสร้าง CI.

## Assumptions / When to use

Pairs ต้องถูกจับคู่ตาม design และ differences ควรเหมาะกับ t inference. ห้าม “จับคู่” ภายหลังเพื่อเพิ่ม significance.

## Common Mistakes

- ใช้ two-sample independent SE ทั้งที่ข้อมูล paired
- ดู correlation ของ X/Y แล้วสรุป effect แทน difference
- ลบในทิศทางไม่สม่ำเสมอ

## Cross-check / Corrections

Canonical note emphasizes reduction to one-sample inference on differences; this matches lecture treatment of matched-pair cases.

## Quick Review

- **Concept:** Matched-pairs CI ลด paired observations ให้เป็น difference scores $D_i$ แล้วทำ one-sample t interval บน mean difference $\mu_D$.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Confidence Interval for Difference of Means]]
- [[Two-Sample and Paired Tests]]
- [[Permutation Tests]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[2ConfidenceInterval_mod]] | Matched-pair interval sections | paired mean difference |
| [[5PermutationTest]] | Classical matched-pair review | paired-test context |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
