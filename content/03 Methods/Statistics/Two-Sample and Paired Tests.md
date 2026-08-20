---
title: "Two-Sample and Paired Tests"
topic_number: 148
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - inference
  - two-sample
  - paired
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Two-Sample and Paired Tests

> [!abstract] Summary
> Two-sample procedures เปรียบเทียบ independent groups; paired procedures วิเคราะห์ within-pair differences. การเลือกผิด design ทำให้ standard error และ inference ผิด.

## Why this concept matters

จำเป็นสำหรับ A/B comparisons, experimental groups และ before/after studies.

## Core Idea

Independent two-sample mean: test $\mu_1-\mu_2=\Delta_0$. Paired: define $D_i=X_i-Y_i$ แล้ว test mean difference. Proportion comparisons ใช้ difference in sample proportions กับ null SE ที่เหมาะสม.

## Mathematical Formulation / Technical Detail

Welch t statistic:
$t=\frac{(\bar X_1-\bar X_2)-\Delta_0}{\sqrt{S_1^2/n_1+S_2^2/n_2}}$.
Paired t: $t=(\bar D-\Delta_0)/(S_D/\sqrt n)$.

## Worked / Practical Example

Before/after blood pressure ของคนเดิมต้อง paired; คนละกลุ่ม treatment/control ที่สุ่มแยกต้อง independent.

## Assumptions / When to use

Design defines dependence structure. Independence between groups does not imply observations within cluster are independent if cluster sampling exists.

## Common Mistakes

- ใช้ pooled test โดย default ทั้งที่ variances unequal/unknown
- ใช้ independent test กับ paired data
- สับสน equal sample size กับ pairing

## Cross-check / Corrections

Lecture covers equal/unequal variance and matched-pair cases; canonical structure separates design choice first, then variance model.

## Quick Review

- **Concept:** Two-sample procedures เปรียบเทียบ independent groups; paired procedures วิเคราะห์ within-pair differences. การเลือกผิด design ทำให้ standard error และ inference ผิด.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Welch vs Pooled Two-Sample t Procedures]]
- [[Matched-Pairs Confidence Interval]]
- [[Permutation Tests]]
- [[Confidence Interval for Difference of Means]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[4TestHypo]] | Two-sample and matched-pair testing sections | classical tests |
| [[2ConfidenceInterval_mod]] | Two-sample and paired interval sections | standard errors |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
