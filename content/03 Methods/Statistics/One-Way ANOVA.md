---
title: "One-Way ANOVA"
topic_number: 152
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - anova
  - hypothesis-testing
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# One-Way ANOVA

> [!abstract] Summary
> One-way ANOVA ทดสอบ global null ว่า means ของ $k>2$ groups เท่ากัน โดยเปรียบเทียบ between-group variation กับ within-group/error variation.

## Why this concept matters

หลีกเลี่ยงการทำ pairwise t-tests หลายคู่โดยไม่ควบคุม family-wise Type I error และให้ global test ก่อน post hoc analysis.

## Core Idea

Fixed-effects one-way model: $Y_{ij}=\mu+\tau_i+\epsilon_{ij}$. $H_0:\mu_1=\cdots=\mu_k$. เมื่อ group means แตกต่างมากเมื่อเทียบกับ within-group noise, F statistic จะใหญ่.

## Mathematical Formulation / Technical Detail

$F=MS_{between}/MS_{within}$, df $(k-1,n-k)$. Under classical model, errors are independent, mean 0, common variance, approximately normal for exact small-sample F inference.

## Worked / Practical Example

เปรียบเทียบค่าเฉลี่ยเงินเดือนเริ่มต้น 3 มหาวิทยาลัย: ANOVA ตอบก่อนว่า “มีอย่างน้อยหนึ่ง mean ต่าง” ไม่ได้ระบุทันทีว่าคู่ไหนต่าง.

## Assumptions / When to use

Independent observations, appropriate factor levels, equal error variance for classical pooled ANOVA, and normal error model for exact inference. Alternatives เช่น Welch ANOVA ใช้เมื่อ equal-variance assumption ไม่เหมาะ.

## Common Mistakes

- สรุปจาก significant ANOVA ว่าทุกคู่ต่างกัน
- ตรวจ normality ของ pooled raw outcomes แทน model residuals โดยไม่คิด design
- ใช้ repeated measures data กับ independent one-way ANOVA

## Cross-check / Corrections

NIST states classical one-way ANOVA in terms of normally and independently distributed errors with common variance. Canonical noteจึงใช้ “errors/residuals” เป็น assumption object แทนการพูดว่าทุกกลุ่มต้องดู perfectly normal.

## Quick Review

- **Concept:** One-way ANOVA ทดสอบ global null ว่า means ของ $k>2$ groups เท่ากัน โดยเปรียบเทียบ between-group variation กับ within-group/error variation.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[ANOVA Decomposition and F Test]]
- [[Multiple Comparisons and Post Hoc Tests]]
- [[Hypothesis Testing Fundamentals]]
- [[Welch vs Pooled Two-Sample t Procedures]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[7ANOVA_2_68_260425_131156]] | ANOVA objective / assumptions / examples | one-way ANOVA framework |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
