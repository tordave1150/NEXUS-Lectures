---
title: "Ordinary Least Squares and Normal Equation"
aliases:
  - OLS
  - Normal Equation
  - Least Squares
topic_number: 67
domain:
  - Data Science
  - Statistics
  - Regression
language: th
source_type:
  - lecture
tags:
  - regression
  - ols
  - linear-algebra
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Ordinary Least Squares and Normal Equation

> [!abstract] Summary
> Ordinary Least Squares (OLS) estimate coefficients โดย minimize squared residuals; normal equations เป็น mathematical characterization ของ optimum แต่ practical solvers มักใช้ QR/SVD/lstsq มากกว่าการ invert \(X^TX\) ตรง ๆ.

## Why this concept matters

ช่วยเข้าใจทั้ง closed-form regression, rank deficiency, pseudoinverse และเหตุผลที่ regularization ช่วยเมื่อ design matrix ill-conditioned.

## Core Idea

- Objective: \(\min_\beta\|X\beta-y\|_2^2\).
- First-order condition: \(X^\top X\hat\beta=X^\top y\).
- ถ้า \(X^\top X\) singular ใช้ Moore–Penrose pseudoinverse/SVD เพื่อหา least-squares solution.
- อย่า equate normal equation formula กับ recommended numerical implementation.

## Mathematical Formulation / Technical Detail

\[
\nabla_\beta \|X\beta-y\|_2^2=2X^\top(X\beta-y)=0
\]

จึงได้
\[
X^\top X\hat\beta=X^\top y.
\]

เมื่อ invertible:
\[
\hat\beta=(X^\top X)^{-1}X^\top y.
\]

ทั่วไป:
\[
\hat\beta=X^+y
\]
โดย \(X^+\) คือ pseudoinverse.

## Worked / Practical Example

ถ้า duplicate feature ทำให้ columns ของ X linearly dependent, \(X^TX\) singular. SVD/lstsq ยังคืน least-squares solution ได้ ขณะที่ explicit inverse ล้ม.

## When to use

- small/medium linear least-squares problems.
- ใช้เพื่อเข้าใจ closed-form และ diagnostics ของ rank/conditioning.

## Limitations / Assumptions

- Forming \(X^TX\) ทำให้ condition number แย่ลง.
- complexity ขึ้นกับ samples/features/solver; ไม่ควรพูด O(n³) โดยไม่ระบุ n.
- OLS ไม่ได้แก้ multicollinearity ทาง prediction/inference โดยอัตโนมัติ.

## Common Mistakes

- เขียน inverse ใน production code ทั้งที่ solver มี lstsq.
- สับสน singular matrix กับ 'ไม่มีคำตอบ'; least-squares solution ยังมีผ่าน pseudoinverse.

## Cross-check / Corrections

- Lecture ระบุ inverse complexity O(n³) แบบไม่แยก sample/feature dimension; canonical note ระบุว่าค่า cubic เกี่ยวกับ dimension ของ matrix ที่ invert และ modern SVD-based OLS มี complexity profile ต่างออกไป.

## Quick Review

- **Concept:** Ordinary Least Squares (OLS) estimate coefficients โดย minimize squared residuals; normal equations เป็น mathematical characterization ของ optimum แต่ practical solvers มักใช้ QR/SVD/lstsq มากกว่าการ invert \(X^TX\) ตรง ๆ.
- **จำให้ได้:** Objective: \(\min_\beta\|X\beta-y\|_2^2\).
- **ใช้งาน:** small/medium linear least-squares problems.
- **ระวัง:** เขียน inverse ใน production code ทั้งที่ solver มี lstsq.

## Related Notes

- [[Simple Linear Regression]]
- [[Multiple Linear Regression]]
- [[Gradient Descent]]
- [[Ridge Regression]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 2 - Simple Linear Regression]] | Slides 5–7 | normal equation, invertibility, pseudoinverse |

## External References

- scikit-learn Linear Models: https://scikit-learn.org/stable/modules/linear_model.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.


## Statistics Course Enrichment — 2026-08-15

- Added inferential/statistical-model context from [[8Correlation-Regression1_2_68_260502_155920]]: Least-squares criterion and coefficient estimation.
- Detailed coefficient tests, $R^2$, and mean-response vs new-observation uncertainty are separated into [[Regression Inference]], [[Coefficient of Determination R-Squared]], and [[Regression Confidence vs Prediction Intervals]] to preserve one canonical concept per note.
