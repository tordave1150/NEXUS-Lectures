---
title: "Nonlinear Regression"
aliases:
  - Nonlinear Relationships
  - Regression when Linearity Fails
topic_number: 30
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[10-NonlinearRegression_260711_160649 (1)]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Nonlinear Regression

> [!abstract] Summary
> Nonlinear regressionในบริบท lecture หมายถึงการเพิ่ม nonlinear functionsของ predictors เช่น polynomial, log, splineหรือ growth curves เพื่อให้ conditional meanไม่ถูกบังคับเป็น straight line.

## Why this concept matters

Business relationshipsจำนวนมากมี diminishing returns, saturation, threshold หรือ accelerating cost; linear slopeคงที่อาจไม่สมเหตุผล.

## Core Idea

- Linear in parameters modelสามารถมี nonlinear feature $x^2$, $\log x$, spline basisได้.
- Shapeควรเลือกจาก domain logic + validation ไม่ใช่เพียง $R^2$.
- Extrapolationของ flexible nonlinear modelsอันตรายกว่าการ interpolation.
- Marginal effectของ $x$ ขึ้นกับ $x$ เมื่อมี nonlinear term.

## Mathematical Formulation / Technical Detail

Quadratic example:

$$
y=\beta_0+\beta_1x+\beta_2x^2+\varepsilon.
$$

Marginal effect:

$$
\frac{\partial E[y|x]}{\partial x}
=\beta_1+2\beta_2x.
$$

ดังนั้น effectไม่คงที่.

## Worked / Practical Example

Advertising vs salesอาจมี diminishing returns: initial spendช่วยมากแต่ incremental spendภายหลังช่วยน้อย. Quadraticที่ $\beta_2<0$สร้าง concave curve แต่หาก extrapolateไกลอาจกลับลงแบบไม่สมเหตุผล.

## Assumptions and Interpretation

- Model specificationควรคำนึง observed range.
- Nonlinear predictor transformไม่เท่ากับ nonlinear-in-parameters estimationเสมอ.

## When to use

- diminishing returns.
- curvatureใน residual plot.
- economic/operational responseที่ไม่เป็นเส้นตรง.

## When not to use / Limitations

- high-degree polynomial extrapolation.
- small sample + flexible basisเสี่ยง overfit.

## Common Mistakes

- เลือก degreeจาก $R^2$ training.
- ตีความ raw coefficientเดี่ยวโดยไม่ดู marginal effect.
- extrapolateเกิน data rangeโดยไม่ทำ plausibility check.

## Quick Review

- **Concept:** Nonlinear regressionในบริบท lecture หมายถึงการเพิ่ม nonlinear functionsของ predictors เช่น polynomial, log, splineหรือ growth curves เพื่อให้ conditional meanไม่ถูกบังคับเป็น straight line.
- **สิ่งที่ต้องจำ:** Linear in parameters modelสามารถมี nonlinear feature $x^2$, $\log x$, spline basisได้.
- **การใช้งาน:** diminishing returns.
- **ข้อควรระวัง:** เลือก degreeจาก $R^2$ training.

## Related Notes

- [[Polynomial Regression]]
- [[Log Transformation and Elasticity]]
- [[Spline and Growth Curve Regression]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[10-NonlinearRegression_260711_160649 (1)]] | Motivation / when linearity fails section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `10-NonlinearRegression_260711_160649 (1).pdf` — Motivation / when linearity fails section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)
- [scikit-learn User Guide — Linear Models (Ridge, Lasso, Elastic Net, Logistic Regression).](https://scikit-learn.org/stable/modules/linear_model.html)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
