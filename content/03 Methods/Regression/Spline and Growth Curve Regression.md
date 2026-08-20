---
title: "Spline and Growth Curve Regression"
aliases:
  - Spline Regression
  - Regression Splines
  - Growth Curves
topic_number: 33
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

# Spline and Growth Curve Regression

> [!abstract] Summary
> Spline regression ใช้ piecewise polynomial basisที่ต่อกันอย่าง smooth เพื่อ capture local curvature; growth curves เช่น logistic/Gompertzใส่ shape constraintsที่เหมาะกับ saturation.

## Why this concept matters

Splineยืดหยุ่นกว่า global polynomialและมัก extrapolateภายใน rangeได้มีเสถียรภาพกว่า ขณะที่ growth curveมี business interpretationเมื่อ processมี ceiling.

## Core Idea

- Knots แบ่ง predictor rangeเป็นช่วง.
- Cubic splineใช้ polynomial degree 3และ impose continuity/smoothnessที่ knots.
- Natural cubic splineบังคับ tailsเป็น linearเพื่อลด wild extrapolation.
- Growth curveเหมาะกับ adoption/capacity saturationมากกว่า arbitrary polynomial.

## Mathematical Formulation / Technical Detail

Truncated-power cubic spline schematic:

$$
y=\beta_0+\beta_1x+\beta_2x^2+\beta_3x^3+
\sum_j\gamma_j(x-\kappa_j)_+^3+\varepsilon.
$$

Logistic growth:

$$
y(t)=\frac{K}{1+\exp[-r(t-t_0)]}.
$$

## Worked / Practical Example

ยอด adoption ที่เริ่มช้า → โตเร็ว → อิ่มตัวอาจ fit logistic growth. Advertising responseที่มี curvatureหลายช่วงอาจใช้ spline knotsแทน degree-5 polynomial.

## Assumptions and Interpretation

- Knot/df selectionเป็น model complexity decision.
- Extrapolationของ splinesนอก boundaryยังต้องระวัง.

## When to use

- smooth nonlinear relationships.
- saturation/growth processes.

## When not to use / Limitations

- data sparseมากรอบ knots.
- ใช้ flexible splineเพื่อ causal interpretationโดยไม่ control confounding.

## Common Mistakes

- ใส่ knotsจำนวนมากจน overfit.
- คิดว่า splineคือ piecewise linesที่ไม่ต่อกัน.
- ใช้ logistic growthทั้งที่ไม่มี plausible carrying capacity.

## Quick Review

- **Concept:** Spline regression ใช้ piecewise polynomial basisที่ต่อกันอย่าง smooth เพื่อ capture local curvature; growth curves เช่น logistic/Gompertzใส่ shape constraintsที่เหมาะกับ saturation.
- **สิ่งที่ต้องจำ:** Knots แบ่ง predictor rangeเป็นช่วง.
- **การใช้งาน:** smooth nonlinear relationships.
- **ข้อควรระวัง:** ใส่ knotsจำนวนมากจน overfit.

## Related Notes

- [[Nonlinear Regression]]
- [[Polynomial Regression]]
- [[Regularized Regression]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[10-NonlinearRegression_260711_160649 (1)]] | Spline regression / exponential & growth curve appendix | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `10-NonlinearRegression_260711_160649 (1).pdf` — Spline regression / exponential & growth curve appendix

## External References

- [scikit-learn User Guide — Linear Models (Ridge, Lasso, Elastic Net, Logistic Regression).](https://scikit-learn.org/stable/modules/linear_model.html)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
