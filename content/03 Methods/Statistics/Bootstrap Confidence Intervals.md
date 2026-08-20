---
title: "Bootstrap Confidence Intervals"
topic_number: 143
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - resampling
  - confidence-interval
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Bootstrap Confidence Intervals

> [!abstract] Summary
> Bootstrap confidence intervals ใช้ empirical bootstrap distribution เพื่อสร้าง uncertainty interval ของ parameter โดย lecture เน้น normal/SE และ percentile approaches.

## Why this concept matters

เหมาะเมื่อ sampling distribution ไม่สะดวก derive analytically แต่ต้องระวัง bias, skewness และ small-sample behavior.

## Core Idea

สองแนวทางพื้นฐาน:
1. Normal/SE: $\hat\theta\pm z^*\widehat{SE}_{boot}$
2. Percentile: ใช้ empirical quantiles ของ $\hat\theta^*$ เช่น 2.5% และ 97.5%.

## Mathematical Formulation / Technical Detail

Percentile 95% CI = $[Q_{0.025}(\hat\theta^*), Q_{0.975}(\hat\theta^*)]$.

## Worked / Practical Example

ถ้า bootstrap medians เบ้ไปขวา percentile interval จะสะท้อน asymmetry ของ bootstrap distribution มากกว่า symmetric normal interval.

## Assumptions / When to use

ต้องเลือก bootstrap scheme ถูกต้องและ $B$ เพียงพอ. Percentile interval ไม่แก้ bias/acceleration โดยอัตโนมัติ; advanced methods เช่น BCa อาจเหมาะกว่า.

## Common Mistakes

- คิดว่า bootstrap CI distribution-free แบบไม่มีเงื่อนไข
- ใช้ $B$ น้อยมากแล้วรายงาน tail quantiles อย่างมั่นใจ
- เปรียบเทียบ bootstrap CI กับ classical CI โดยไม่แยก target/assumptions

## Cross-check / Corrections

Lecture เน้น percentile method; canonical note adds that percentile CI is only one bootstrap interval family and may have imperfect coverage for biased/skewed estimators.

## Quick Review

- **Concept:** Bootstrap confidence intervals ใช้ empirical bootstrap distribution เพื่อสร้าง uncertainty interval ของ parameter โดย lecture เน้น normal/SE และ percentile approaches.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Bootstrap Resampling]]
- [[Confidence Intervals]]
- [[Statistical Inference and Estimation]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[3Jackknife_Bootstrap]] | Bootstrap confidence interval sections | normal and percentile intervals |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
