---
title: "Expected Value Variance and Covariance"
topic_number: 130
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - probability
  - moments
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Expected Value Variance and Covariance

> [!abstract] Summary
> Expected value บอกศูนย์กลางเชิงความน่าจะเป็น, variance บอก dispersion และ covariance บอกการเปลี่ยนร่วมกันของตัวแปรสองตัว.

## Why this concept matters

สามปริมาณนี้เป็นพื้นฐานของ standard error, correlation, regression และ risk measurement.

## Core Idea

$E[X]$ คือ long-run probability-weighted average; $Var(X)$ วัด squared deviation รอบ mean; $Cov(X,Y)$ วัดทิศทางการเปลี่ยนร่วมแบบเชิงเส้น.

## Mathematical Formulation / Technical Detail

$Var(X)=E[(X-E[X])^2]=E[X^2]-E[X]^2$.

$Cov(X,Y)=E[(X-E[X])(Y-E[Y])]$.

$Var(aX+b)=a^2Var(X)$. ถ้า independent: $Var(X+Y)=Var(X)+Var(Y)$.

## Worked / Practical Example

ถ้า $X$ เป็น Bernoulli($p$): $E[X]=p$ และ $Var(X)=p(1-p)$.

## Assumptions / When to use

Finite moments ต้องมีอยู่สำหรับสูตรที่ใช้ expectation/variance. Covariance 0 ไม่รับประกัน independence ยกเว้นในบาง distribution families เช่น jointly normal.

## Common Mistakes

- ตีความ covariance magnitude โดยไม่สนใจ units
- คิดว่า zero covariance = independence เสมอ
- ใช้ SD กับ variance สลับกัน

## Cross-check / Corrections

Lecture correlation material emphasizes covariance and standardization; canonical note adds the distinction that covariance depends on measurement scale while correlation is standardized.

## Quick Review

- **Concept:** Expected value บอกศูนย์กลางเชิงความน่าจะเป็น, variance บอก dispersion และ covariance บอกการเปลี่ยนร่วมกันของตัวแปรสองตัว.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Random Variables PMF PDF CDF]]
- [[Pearson Correlation]]
- [[Sampling Distribution and Central Limit Theorem]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[1Probability_mod]] | Random-variable moments sections | expectation and variance |
| [[8Correlation-Regression1_2_68_260502_155920]] | Correlation introduction | covariance connection |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
