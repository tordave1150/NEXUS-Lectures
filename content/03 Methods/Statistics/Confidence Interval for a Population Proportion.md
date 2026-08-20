---
title: "Confidence Interval for a Population Proportion"
topic_number: 138
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - inference
  - confidence-interval
  - proportion
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Confidence Interval for a Population Proportion

> [!abstract] Summary
> CI สำหรับ population proportion ใช้ sample proportion $\hat p$ และ sampling uncertainty ของ Bernoulli/binomial data.

## Why this concept matters

ใช้กับ survey proportions, rates และ binary outcomes แต่ normal-approximation intervals ต้องระวังเมื่อ sample เล็กหรือ $p$ ใกล้ 0/1.

## Core Idea

Lecture derives Wald-style normal approximation from $\hat p=X/n$. เป็นสูตรเรียนรู้ที่ตรงไปตรงมา แต่ไม่ใช่ interval ที่ดีที่สุดในทุก regime.

## Mathematical Formulation / Technical Detail

Wald form: $\hat p\pm z_{1-\alpha/2}\sqrt{\hat p(1-\hat p)/n}$.

## Worked / Practical Example

ถ้า 240 จาก 400 คนตอบ “ใช่”, $\hat p=0.60$ และ SE ≈ $\sqrt{0.6(0.4)/400}=0.0245$; 95% margin ≈ 0.048.

## Assumptions / When to use

Binary observations ควร independent หรือ sampling design ต้องถูกนำมาคิด. Normal approximation ควรใช้เมื่อ effective expected successes/failures เพียงพอ.

## Common Mistakes

- ใช้ Wald interval เมื่อ $x=0$ หรือ $x=n$ แล้วได้ width ผิดธรรมชาติ
- ลืม finite-population/design effects ใน complex surveys
- ตีความ sample proportion เป็น population proportion แบบไม่มี uncertainty

## Cross-check / Corrections

Canonical note เก็บ Wald formula ตาม lecture แต่ระบุว่า practical work มักพิจารณา Wilson/score หรือ exact/other intervals โดยเฉพาะ small n หรือ extreme proportions.

## Quick Review

- **Concept:** CI สำหรับ population proportion ใช้ sample proportion $\hat p$ และ sampling uncertainty ของ Bernoulli/binomial data.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Bernoulli and Binomial Distribution]]
- [[Confidence Intervals]]
- [[One-Sample Mean and Proportion Tests]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[2ConfidenceInterval_mod]] | Confidence interval for population proportion | normal-approximation CI |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
