---
title: "Multiple Linear Regression"
aliases:
  - MLR
topic_number: 66
domain:
  - Data Science
  - Statistics
  - Regression
language: th
source_type:
  - lecture
tags:
  - regression
  - multiple-linear-regression
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Multiple Linear Regression

> [!abstract] Summary
> Multiple Linear Regression ขยาย linear regression ให้ response เป็น linear combination ของหลาย predictors; linear หมายถึง linear in coefficients ไม่ได้หมายความว่า features ต้องเป็นเส้นตรงดิบเท่านั้น.

## Why this concept matters

MLR เป็นแกนกลางของ interpretable regression, polynomial features, dummy variables, regularization และ time-series regression.

## Core Idea

- Model: \(\hat y=\beta_0+\sum_{j=1}^{d}\beta_jx_j\).
- Coefficient \(\beta_j\) ตีความ conditional on other included predictors.
- Interaction/polynomial terms ยังอยู่ใน linear-model family หาก coefficients เข้าสมการเชิงเส้น.

## Mathematical Formulation / Technical Detail

\[
\mathbf y=X\beta+\varepsilon,\qquad
\hat\beta=\arg\min_\beta \|X\beta-y\|_2^2.
\]

ถ้า \(X\) full column rank, textbook normal-equation form คือ
\[
\hat\beta=(X^\top X)^{-1}X^\top y.
\]
ใน numerical computing ไม่ควร explicit inverse เมื่อหลีกเลี่ยงได้.

## Worked / Practical Example

House price model อาจมี size, bedrooms, age. \(\beta_{size}\) คือ fitted change ต่อ size หนึ่งหน่วยเมื่อ bedrooms/age คงที่—ซึ่งอาจตีความยากหาก predictors correlated มาก.

## When to use

- continuous response กับ predictors หลายตัว.
- feature engineering เช่น polynomial/interactions และ dummy variables.

## Limitations / Assumptions

- Multicollinearity ทำ coefficient unstable.
- Omitted variables/endogeneity กระทบ causal interpretation.
- Scaling ไม่จำเป็นสำหรับ closed-form OLS prediction แต่สำคัญต่อ gradient methods/regularization.

## Common Mistakes

- ตีความ coefficient แบบ marginal โดยไม่พูดว่า holding others constant.
- ใช้ explicit matrix inverse ใน code production.
- ใช้ high-degree polynomial โดยไม่ validation.

## Cross-check / Corrections

- ไม่พบ correction สำคัญ; เพิ่มเฉพาะ context และ implementation caveats.

## Quick Review

- **Concept:** Multiple Linear Regression ขยาย linear regression ให้ response เป็น linear combination ของหลาย predictors; linear หมายถึง linear in coefficients ไม่ได้หมายความว่า features ต้องเป็นเส้นตรงดิบเท่านั้น.
- **จำให้ได้:** Model: \(\hat y=\beta_0+\sum_{j=1}^{d}\beta_jx_j\).
- **ใช้งาน:** continuous response กับ predictors หลายตัว.
- **ระวัง:** ตีความ coefficient แบบ marginal โดยไม่พูดว่า holding others constant.

## Related Notes

- [[Simple Linear Regression]]
- [[Ordinary Least Squares and Normal Equation]]
- [[Polynomial Regression]]
- [[Regularized Regression]]
- [[Categorical and Dummy Variables]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 3 - Multiple Linear Regression]] | Slides 2–5 | matrix representation and batch gradient objective |

## External References

- scikit-learn Linear Models: https://scikit-learn.org/stable/modules/linear_model.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.


## Statistics Course Enrichment — 2026-08-15

- Added inferential/statistical-model context from [[8Correlation-Regression1_2_68_260502_155920]]: Regression model framing and coefficient significance.
- Detailed coefficient tests, $R^2$, and mean-response vs new-observation uncertainty are separated into [[Regression Inference]], [[Coefficient of Determination R-Squared]], and [[Regression Confidence vs Prediction Intervals]] to preserve one canonical concept per note.
