---
title: "Simple Linear Regression"
aliases:
  - Single Variable Linear Regression
topic_number: 65
domain:
  - Data Science
  - Statistics
  - Regression
language: th
source_type:
  - lecture
tags:
  - regression
  - linear-regression
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Simple Linear Regression

> [!abstract] Summary
> Simple Linear Regression model ความสัมพันธ์เชิงเส้นระหว่าง predictor หนึ่งตัวกับ continuous response ผ่าน intercept และ slope.

## Why this concept matters

เป็นพื้นฐานของ OLS, multiple regression, logistic regression intuition และ gradient-based optimization.

## Core Idea

- Model: \(\hat y=\beta_0+\beta_1x\).
- Slope \(\beta_1\) คือ expected change ของ fitted mean ต่อการเพิ่ม \(x\) หนึ่งหน่วยภายใต้ linear model.
- OLS เลือก coefficients เพื่อลด sum of squared residuals.

## Mathematical Formulation / Technical Detail

\[
y_i=\beta_0+\beta_1x_i+\varepsilon_i,\qquad
\min_{\beta_0,\beta_1}\sum_i(y_i-\beta_0-\beta_1x_i)^2.
\]

Closed-form slope เมื่อมี intercept:

\[
\hat\beta_1=\frac{\sum_i(x_i-\bar x)(y_i-\bar y)}
{\sum_i(x_i-\bar x)^2},\qquad
\hat\beta_0=\bar y-\hat\beta_1\bar x.
\]

## Worked / Practical Example

ถ้า \(x\)=advertising และ \(\hat y=100+2.5x\), model แปลว่าเพิ่ม ads 1 หน่วยสัมพันธ์กับ fitted sales เพิ่ม 2.5 หน่วยในช่วงข้อมูลที่ model ใช้; ไม่ควรตีความ causal หากไม่มี design/assumptions รองรับ.

## When to use

- baseline regression และ interpretable relationship.
- เมื่อ residual pattern และ linearity reasonably adequate.

## Limitations / Assumptions

- Outliers/high leverage มีอิทธิพลสูง.
- Nonlinearity/heteroskedasticity/autocorrelation อาจทำให้ inference ผิด.
- Extrapolation นอก observed range เสี่ยง.

## Common Mistakes

- สรุป causation จาก slope.
- ดู R² อย่างเดียว.
- ลืมตรวจ residuals.

## Cross-check / Corrections

- ไม่พบ correction สำคัญ; เพิ่มเฉพาะ context และ implementation caveats.

## Quick Review

- **Concept:** Simple Linear Regression model ความสัมพันธ์เชิงเส้นระหว่าง predictor หนึ่งตัวกับ continuous response ผ่าน intercept และ slope.
- **จำให้ได้:** Model: \(\hat y=\beta_0+\beta_1x\).
- **ใช้งาน:** baseline regression และ interpretable relationship.
- **ระวัง:** สรุป causation จาก slope.

## Related Notes

- [[Multiple Linear Regression]]
- [[Ordinary Least Squares and Normal Equation]]
- [[Gradient Descent]]
- [[Regression Assumptions and Diagnostics]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 2 - Simple Linear Regression]] | Slides 2–5 | model representation, MSE objective, solution approaches |

## External References

- scikit-learn Linear Models: https://scikit-learn.org/stable/modules/linear_model.html
- Stanford CS229 Supervised Learning notes index: https://cs229.stanford.edu/notes2021fall/

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.


## Statistics Course Enrichment — 2026-08-15

- Added inferential/statistical-model context from [[8Correlation-Regression1_2_68_260502_155920]]: Simple regression model, OLS, assumptions and inferential interpretation.
- Detailed coefficient tests, $R^2$, and mean-response vs new-observation uncertainty are separated into [[Regression Inference]], [[Coefficient of Determination R-Squared]], and [[Regression Confidence vs Prediction Intervals]] to preserve one canonical concept per note.
