---
title: "Student t Chi-Square and F Distributions"
topic_number: 134
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - probability
  - sampling-distribution
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Student t Chi-Square and F Distributions

> [!abstract] Summary
> Student t, chi-square และ F distributions เป็น sampling distributions หลักของ classical inference เกี่ยวกับ means, variances และ variance ratios.

## Why this concept matters

ช่วยให้เข้าใจว่าทำไม t-test, confidence intervals, ANOVA และ variance procedures ใช้ critical values คนละ distribution.

## Core Idea

- **t distribution:** symmetric, heavier tails than normal; degrees of freedom control shape
- **chi-square:** nonnegative and right-skewed; arises from sums of squared standard normals
- **F:** nonnegative ratio of scaled chi-square variables; depends on two degrees of freedom

## Mathematical Formulation / Technical Detail

สำหรับ normal sample:
$\frac{\bar X-\mu}{S/\sqrt n}\sim t_{n-1}$

$\frac{(n-1)S^2}{\sigma^2}\sim\chi^2_{n-1}$.

ANOVA uses an $F$ ratio of mean squares under $H_0$.

## Worked / Practical Example

เมื่อ $n$ เล็กและ $\sigma$ ไม่ทราบ การใช้ t critical value ทำให้ interval กว้างกว่า z เพราะต้องสะท้อน uncertainty จากการประมาณ $\sigma$.

## Assumptions / When to use

Exact textbook results ข้างต้นอาศัย normal sampling model. Large-sample approximations อาจผ่อนเงื่อนไขบางส่วนได้.

## Common Mistakes

- ใช้ z เมื่อ $\sigma$ ไม่ทราบและ n เล็กโดยไม่พิจารณา t
- คิดว่า chi-square symmetric
- สับสน numerator/denominator df ใน F distribution

## Cross-check / Corrections

No major correction; canonical note groups the three distributions by their role in inference rather than treating them as isolated formulas.

## Quick Review

- **Concept:** Student t, chi-square และ F distributions เป็น sampling distributions หลักของ classical inference เกี่ยวกับ means, variances และ variance ratios.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Normal Distribution and Standardization]]
- [[Confidence Interval for a Population Mean]]
- [[One-Way ANOVA]]
- [[ANOVA Decomposition and F Test]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[1Probability_mod]] | Standard normal / t / chi-square / F sections | sampling distributions |
| [[2ConfidenceInterval_mod]] | Distribution of statistics review | CI use |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
