---
title: "One-Sample Mean and Proportion Tests"
topic_number: 147
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - inference
  - one-sample
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# One-Sample Mean and Proportion Tests

> [!abstract] Summary
> One-sample tests เปรียบเทียบ population mean หรือ proportion กับค่าที่กำหนด โดย standardize ความต่างด้วย standard error ภายใต้ null.

## Why this concept matters

เป็น building block ของ classical testing และเชื่อมกับ confidence intervals.

## Core Idea

Mean: z procedure เมื่อ $\sigma$ รู้/appropriate; t procedure เมื่อ $\sigma$ ไม่รู้ภายใต้ normal/robustness conditions. Proportion: normal approximation ใช้ standardized $\hat p-p_0$ เมื่อ expected counts เพียงพอ.

## Mathematical Formulation / Technical Detail

Mean t statistic: $t=(\bar X-\mu_0)/(S/\sqrt n)$.
Proportion z: $z=(\hat p-p_0)/\sqrt{p_0(1-p_0)/n}$ under $H_0$.

## Worked / Practical Example

ถ้า $\bar x=105$, $s=12$, $n=36$, ทดสอบ $H_0:\mu=100$: $t=(5)/(12/6)=2.5$.

## Assumptions / When to use

Independence/random sampling and distribution/large-sample conditions matter. For proportions near boundaries or small samples, exact/binomial alternatives may be preferable.

## Common Mistakes

- ใช้ $\hat p$ แทน $p_0$ ใน null SE โดยไม่รู้ว่าเป็น test/CI คนละสูตร
- ใช้ t distribution สำหรับ proportion
- ไม่กำหนด alternative direction

## Cross-check / Corrections

Canonical note distinguishes test standard error under $H_0$ from CI standard error, which are often conflated in introductory notes.

## Quick Review

- **Concept:** One-sample tests เปรียบเทียบ population mean หรือ proportion กับค่าที่กำหนด โดย standardize ความต่างด้วย standard error ภายใต้ null.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Hypothesis Testing Fundamentals]]
- [[Confidence Interval for a Population Mean]]
- [[Confidence Interval for a Population Proportion]]
- [[Bernoulli and Binomial Distribution]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[4TestHypo]] | One-population test examples and test statistics | mean/proportion tests |
| [[2ConfidenceInterval_mod]] | CI formulas | test-CI connection |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
