---
title: "Random Variables PMF PDF CDF"
topic_number: 129
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - probability
  - random-variable
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Random Variables PMF PDF CDF

> [!abstract] Summary
> Random variable แปลง outcomes จาก sample space เป็นค่าตัวเลข และ probability distribution อธิบายว่าค่าเหล่านั้นกระจายอย่างไร.

## Why this concept matters

ทำให้สามารถใช้ mean, variance, quantiles และ sampling distributions กับ random outcomes ได้อย่างเป็นระบบ.

## Core Idea

- Discrete random variable: ใช้ **PMF** $p_X(x)=P(X=x)$
- Continuous random variable: ใช้ **PDF** $f_X(x)$; probability เป็นพื้นที่ใต้ curve
- **CDF** ใช้ได้ทั้งสองแบบ: $F_X(x)=P(X\le x)$

## Mathematical Formulation / Technical Detail

Discrete: $p_X(x)\ge0$ และ $\sum_x p_X(x)=1$.

Continuous: $f_X(x)\ge0$ และ $\int_{-\infty}^{\infty}f_X(x)dx=1$.

สำหรับ continuous $X$, $P(X=x)=0$ และ $P(a<X\le b)=F(b)-F(a)$.

## Worked / Practical Example

จำนวนหัวจากการโยนเหรียญ 3 ครั้งเป็น discrete random variable $X\in\{0,1,2,3\}$; อายุการใช้งานหลอดไฟเป็น continuous random variable.

## Assumptions / When to use

เลือก representation ตาม support ของตัวแปร ไม่ใช่ตามจำนวน observations ที่มีใน sample.

## Common Mistakes

- เรียก PDF ว่า probability ที่จุด $x$
- ลืมว่า density อาจมากกว่า 1 ได้ แต่พื้นที่รวมต้องเท่ากับ 1
- สับสน sample distribution กับ sampling distribution

## Cross-check / Corrections

Canonical note distinguishes PMF/PDF/CDF explicitly because PDF value itself is density, not point probability.

## Quick Review

- **Concept:** Random variable แปลง outcomes จาก sample space เป็นค่าตัวเลข และ probability distribution อธิบายว่าค่าเหล่านั้นกระจายอย่างไร.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Probability Foundations]]
- [[Expected Value Variance and Covariance]]
- [[Bernoulli and Binomial Distribution]]
- [[Normal Distribution and Standardization]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[1Probability_mod]] | Random variable / discrete and continuous distribution sections | definitions and distribution functions |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
