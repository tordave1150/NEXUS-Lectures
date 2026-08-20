---
title: "Inference for Pearson Correlation"
topic_number: 156
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - correlation
  - inference
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Inference for Pearson Correlation

> [!abstract] Summary
> Classical test for Pearson correlation evaluates $H_0:\rho=0$ using a t statistic with $n-2$ degrees of freedom under an iid bivariate-normal model.

## Why this concept matters

แยก descriptive correlation $r$ จาก uncertainty/inference เกี่ยวกับ population correlation $\rho$.

## Core Idea

Observed pairs $(X_i,Y_i)$ เป็น sampling units. Exact t test is derived under joint/bivariate normality, not from treating X observations and Y observations as two independent samples.

## Mathematical Formulation / Technical Detail

$t=r\sqrt{\frac{n-2}{1-r^2}}\sim t_{n-2}$ under $H_0:\rho=0$ in the classical model.

## Worked / Practical Example

ถ้า $r=0.6$, $n=30$, $t=0.6\sqrt{28/(1-0.36)}\approx3.97$, evidence against zero correlation is strong under model assumptions.

## Assumptions / When to use

Pairs should be independent across units; relationship should not be dominated by outliers. For non-normal/robust settings consider resampling or rank-based methods depending target.

## Common Mistakes

- คิดว่า X sample ต้อง independent จาก Y sample; ใน correlation แต่ละ $(X_i,Y_i)$ ต้องเป็น pair
- significant correlation = practically large
- test $r$ โดยไม่ดู scatterplot

## Cross-check / Corrections

Lecture wording lists X and Y as separate random samples; canonical note clarifies the classical derivation uses iid **pairs** from a bivariate normal population.

## Quick Review

- **Concept:** Classical test for Pearson correlation evaluates $H_0:\rho=0$ using a t statistic with $n-2$ degrees of freedom under an iid bivariate-normal model.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Pearson Correlation]]
- [[Permutation Tests]]
- [[Hypothesis Testing Fundamentals]]
- [[Simple Linear Regression]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[8Correlation-Regression1_2_68_260502_155920]] | Hypothesis test for population correlation coefficient | t test for rho |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
