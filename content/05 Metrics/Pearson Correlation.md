---
title: "Pearson Correlation"
topic_number: 155
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - correlation
  - metric
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Pearson Correlation

> [!abstract] Summary
> Pearson correlation coefficient วัด strength และ direction ของ **linear association** ระหว่าง numerical variables ใน scale-free form ตั้งแต่ -1 ถึง 1.

## Why this concept matters

ใช้เป็น descriptive association metric และเชื่อมกับ simple linear regression แต่ไม่เท่ากับ causation หรือ general dependence.

## Core Idea

Population correlation $\rho=Cov(X,Y)/(\sigma_X\sigma_Y)$. Sample correlation $r$ standardize sample covariance. Sign บอก direction; magnitude บอก linear tightness.

## Mathematical Formulation / Technical Detail

$r=\frac{\sum_i(x_i-\bar x)(y_i-\bar y)}{\sqrt{\sum_i(x_i-\bar x)^2\sum_i(y_i-\bar y)^2}}$.

## Worked / Practical Example

$r=0$ อาจเกิดกับ strong nonlinear relationship เช่น symmetric U-shape ดังนั้นควรดู scatterplot ด้วย.

## Assumptions / When to use

Meaningfulเมื่อ variables numerical และ linear association เป็นคำถามที่สนใจ. Outliers, range restriction และ mixtures สามารถเปลี่ยน r อย่างมาก.

## Common Mistakes

- correlation = causation
- $r=0$ = independence
- ใช้ universal strength thresholds โดยไม่ดู domain/context

## Cross-check / Corrections

Lecture ให้ rough guide เช่น 0.70–0.89 = high. Canonical noteเก็บเป็น classroom heuristic เท่านั้น; ไม่มี universal cutoffs สำหรับ “weak/moderate/strong” เพราะ interpretation ขึ้นกับ domain, noise และ decision context.

## Quick Review

- **Concept:** Pearson correlation coefficient วัด strength และ direction ของ **linear association** ระหว่าง numerical variables ใน scale-free form ตั้งแต่ -1 ถึง 1.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Expected Value Variance and Covariance]]
- [[Inference for Pearson Correlation]]
- [[Simple Linear Regression]]
- [[Coefficient of Determination R-Squared]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[8Correlation-Regression1_2_68_260502_155920]] | Correlation / scatterplot / rough guide sections | Pearson r definition and interpretation |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
