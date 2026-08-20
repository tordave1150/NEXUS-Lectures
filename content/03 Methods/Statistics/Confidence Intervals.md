---
title: "Confidence Intervals"
topic_number: 136
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - inference
  - confidence-interval
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Confidence Intervals

> [!abstract] Summary
> Confidence interval เป็น random interval procedure ที่ออกแบบให้มี long-run coverage ตามระดับ $1-\alpha$ ภายใต้ model/assumptions.

## Why this concept matters

CI สื่อ uncertainty ของ parameter estimate และเชื่อมโดยตรงกับ hypothesis testing.

## Core Idea

CI มีรูปแบบทั่วไป “estimate ± critical value × standard error” แต่ exact formula ขึ้นกับ parameter, sampling distribution และสิ่งที่รู้/ไม่รู้เกี่ยวกับ variance.

## Mathematical Formulation / Technical Detail

Frequentist coverage:
$P_\theta(L(X)\le\theta\le U(X))=1-\alpha$ สำหรับ procedure ที่ออกแบบไว้.

เมื่อสังเกต sample แล้ว interval เป็นค่าคงที่; 95% confidence หมายถึง procedure ครอบคลุม parameter ประมาณ 95% ใน repeated sampling ภายใต้ assumptions.

## Worked / Practical Example

ถ้า 95% CI ของ mean = [10.2, 12.8] เราพูดว่า interval procedure มี 95% coverage; ไม่ใช่ว่า parameter fixed มี probability 0.95 หลังเห็น interval ใน frequentist interpretation.

## Assumptions / When to use

ต้องระบุ target parameter, sampling design, confidence level และ method. Higher confidence มักให้ wider intervals; larger n มักลด SE.

## Common Mistakes

- ตีความ 95% CI เป็น “95% probability parameter อยู่ในช่วงนี้” แบบ frequentist
- ใช้ CI จาก model ผิด assumptions
- มอง CI แค่ว่า significant/non-significant ไม่ดู width และ practical scale

## Cross-check / Corrections

Canonical interpretation follows repeated-sampling coverage; note explicitly distinguishes confidence interval from [[Regression Confidence vs Prediction Intervals]] for a new observation.

## Quick Review

- **Concept:** Confidence interval เป็น random interval procedure ที่ออกแบบให้มี long-run coverage ตามระดับ $1-\alpha$ ภายใต้ model/assumptions.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Statistical Inference and Estimation]]
- [[Confidence Interval for a Population Mean]]
- [[Hypothesis Testing Fundamentals]]
- [[Regression Confidence vs Prediction Intervals]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[2ConfidenceInterval_mod]] | Interval estimation / confidence-level sections | definition and interpretation |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
