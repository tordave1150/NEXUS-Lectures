---
title: "Confidence Interval for a Population Mean"
topic_number: 137
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - inference
  - confidence-interval
  - mean
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Confidence Interval for a Population Mean

> [!abstract] Summary
> CI สำหรับ population mean ใช้ standard error ของ sample mean และ z/t critical value ตามสิ่งที่ทราบเกี่ยวกับ population variance และ sampling model.

## Why this concept matters

เป็น interval estimator พื้นฐานที่สุดและเป็นต้นแบบของ t procedures.

## Core Idea

ถ้า $\sigma$ รู้และ normal model หรือ large-sample approximation: ใช้ z. ถ้า $\sigma$ ไม่รู้และ normal sampling model: ใช้ t โดยแทน $\sigma$ ด้วย sample SD $S$.

## Mathematical Formulation / Technical Detail

Known $\sigma$: $\bar X\pm z_{1-\alpha/2}\sigma/\sqrt n$.

Unknown $\sigma$: $\bar X\pm t_{1-\alpha/2,n-1}S/\sqrt n$.

## Worked / Practical Example

ถ้า $\bar x=50$, $s=10$, $n=25$, 95% CI ใช้ $t_{0.975,24}$ และ SE = 2; margin of error ≈ critical × 2.

## Assumptions / When to use

Random/representative sampling and independence matter. Exact small-sample t interval assumes normal population; large-sample robustness depends on distribution shape and n.

## Common Mistakes

- ใช้ SD แทน SE
- ลืมหาร $\sqrt n$
- ใช้ z=1.96 ทุกกรณีโดยไม่ดู $\sigma$ และ sample size

## Cross-check / Corrections

Cross-check with NIST confirms the standard t interval $\bar Y\pm t_{1-\alpha/2,N-1}s/\sqrt N$ and repeated-sampling interpretation.

## Quick Review

- **Concept:** CI สำหรับ population mean ใช้ standard error ของ sample mean และ z/t critical value ตามสิ่งที่ทราบเกี่ยวกับ population variance และ sampling model.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Confidence Intervals]]
- [[Student t Chi-Square and F Distributions]]
- [[One-Sample Mean and Proportion Tests]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[2ConfidenceInterval_mod]] | Confidence interval for population mean | z/t interval formulas |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
