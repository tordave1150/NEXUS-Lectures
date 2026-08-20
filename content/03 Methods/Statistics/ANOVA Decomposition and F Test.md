---
title: "ANOVA Decomposition and F Test"
topic_number: 153
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - anova
  - sum-of-squares
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# ANOVA Decomposition and F Test

> [!abstract] Summary
> ANOVA decomposes total sum of squares into between-group and within-group components แล้วสร้าง F ratio จาก mean squares.

## Why this concept matters

ช่วยให้เห็นว่า ANOVA ไม่ได้ “วิเคราะห์ variance แทน mean” แต่ใช้ variance decomposition เพื่อทดสอบ mean differences.

## Core Idea

Identity:
$SS_T=SS_{between}+SS_E$.
Between SS วัด group means รอบ grand mean; SSE วัด observations รอบ group mean.

## Mathematical Formulation / Technical Detail

$SS_B=\sum_i n_i(\bar X_i-\bar X)^2$.
$SS_E=\sum_i\sum_j(X_{ij}-\bar X_i)^2$.
$MS_B=SS_B/(k-1)$, $MSE=SS_E/(n-k)$, $F=MS_B/MSE$.

## Worked / Practical Example

ถ้า group means ใกล้กัน SS_B เล็กและ F ใกล้ 1; ถ้าห่างกันมากเทียบกับ within variance F สูง.

## Assumptions / When to use

Classical F null distribution depends on the one-way ANOVA assumptions. Sum-of-squares definitions vary for unbalanced multifactor designs, but one-way decomposition above is stable.

## Common Mistakes

- สับสน SST notation ระหว่าง “total” กับ “treatment” ในหนังสือต่างเล่ม
- ดู F ใหญ่โดยไม่ดู df/p-value
- ตีความ MSE เป็น prediction MSE คนละบริบท

## Cross-check / Corrections

NIST one-way ANOVA table confirms the between/residual/total decomposition and F ratio. Canonical noteใช้ explicit subscripts เพื่อลด notation collision.

## Quick Review

- **Concept:** ANOVA decomposes total sum of squares into between-group and within-group components แล้วสร้าง F ratio จาก mean squares.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[One-Way ANOVA]]
- [[Multiple Comparisons and Post Hoc Tests]]
- [[Student t Chi-Square and F Distributions]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[7ANOVA_2_68_260425_131156]] | Sum-of-squares / ANOVA table sections | decomposition and F statistic |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
