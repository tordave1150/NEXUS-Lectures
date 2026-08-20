---
title: "Confidence Interval for Difference of Means"
topic_number: 139
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - inference
  - confidence-interval
  - two-sample
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Confidence Interval for Difference of Means

> [!abstract] Summary
> CI สำหรับ $\mu_1-\mu_2$ ประเมินความแตกต่างระหว่างค่าเฉลี่ยของสองประชากรอิสระ โดย standard error ขึ้นกับ variance และ sample sizes ของทั้งสองกลุ่ม.

## Why this concept matters

ช่วยรายงานทั้ง direction, magnitude และ uncertainty แทนการดูเพียง p-value.

## Core Idea

กรณี independent samples และ variances ไม่จำเป็นต้องเท่ากัน ใช้ Welch-style standard error. ถ้า model สมเหตุผลว่า variances เท่ากัน สามารถใช้ pooled variance t interval.

## Mathematical Formulation / Technical Detail

Welch form:
$(\bar X_1-\bar X_2)\pm t^*\sqrt{S_1^2/n_1+S_2^2/n_2}$
โดย df ใช้ Welch–Satterthwaite approximation.

Pooled form ใช้ $S_p^2$ และ df $n_1+n_2-2$.

## Worked / Practical Example

ถ้า mean difference = 4.0 และ 95% CI = [1.2,6.8], data สอดคล้องกับ positive difference; interval ยังสื่อ plausible effect sizes.

## Assumptions / When to use

ต้องเป็น independent groups สำหรับสูตรนี้. ถ้าข้อมูล paired ต้องใช้ [[Matched-Pairs Confidence Interval]].

## Common Mistakes

- ใช้ independent-sample CI กับ paired data
- pool variances โดยไม่ตรวจ design/model
- รายงานว่า “ไม่มีความแตกต่าง” เพียงเพราะ CI คร่อม 0

## Cross-check / Corrections

Lecture แยก equal/unequal variance cases; canonical note ให้ Welch เป็น default conceptual reference เมื่อ equality ไม่ได้ถูก justify และแยก pooled procedure เป็น model-specific alternative.

## Quick Review

- **Concept:** CI สำหรับ $\mu_1-\mu_2$ ประเมินความแตกต่างระหว่างค่าเฉลี่ยของสองประชากรอิสระ โดย standard error ขึ้นกับ variance และ sample sizes ของทั้งสองกลุ่ม.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Confidence Intervals]]
- [[Welch vs Pooled Two-Sample t Procedures]]
- [[Matched-Pairs Confidence Interval]]
- [[Two-Sample and Paired Tests]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[2ConfidenceInterval_mod]] | Two-population mean confidence intervals | independent-sample CI cases |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
