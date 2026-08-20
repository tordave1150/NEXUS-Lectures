---
title: "Polynomial Regression"
aliases:
  - Quadratic Regression
  - Polynomial Models
topic_number: 31
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[10-NonlinearRegression_260711_160649 (1)]]"
  - "[[DADS6003 Week 3 - Multiple Linear Regression]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Polynomial Regression

> [!abstract] Summary
> Polynomial regression เพิ่ม powers ของ predictor เช่น $x^2,x^3$ เพื่อ model curvature โดยยังเป็น linear regression ใน coefficients.

## Why this concept matters

เป็นวิธีง่ายและตีความได้สำหรับ smooth curvature แต่ degreeสูงทำให้ unstable และ extrapolation อันตราย.

## Core Idea

- Degree $K$ เป็น complexity/hyperparameter.
- Quadraticสามารถแสดง U-shape หรือ inverted-U.
- ทุก lower-order termควรถูกรักษาตาม hierarchy principleเมื่อใส่ higher-order term.
- Scaling/centering x ช่วย numerical stabilityและ interpretation.

## Mathematical Formulation / Technical Detail

Degree-$K$ polynomial:

$$
y=\beta_0+\beta_1x+\beta_2x^2+\cdots+\beta_Kx^K+\varepsilon.
$$

Quadratic turning point เมื่อ $\beta_2\ne0$:

$$
x^*=-\frac{\beta_1}{2\beta_2}.
$$

## Worked / Practical Example

Lecture advertising example fit quadratic sales = intercept + positive $x$ + negative $x^2$, จึงแสดง diminishing marginal returnsและมีจุดสูงสุด. ภายนอก observed range เส้นอาจกลับลงอย่างไม่สมเหตุผลจึงไม่ควร extrapolateไกล.

## Assumptions and Interpretation

- OLS assumptions apply to residuals conditional on polynomial features.
- Powersของ x มัก highly correlated; orthogonal polynomialsหรือ centeringช่วยได้.

## When to use

- curvature within observed range.
- baseline nonlinear modelที่ยังตีความง่าย.

## When not to use / Limitations

- high-degree polynomialเมื่อ dataน้อย.
- long-range extrapolation.

## Common Mistakes

- เลือก degreeสูงเพราะ $R^2$ เพิ่มเสมอ.
- ตัด $x$ ออกแต่เก็บ $x^2$ โดยไม่มีเหตุผล.
- ตีความ $\beta_1$ เป็น marginal effectคงที่.

## Quick Review

- **Concept:** Polynomial regression เพิ่ม powers ของ predictor เช่น $x^2,x^3$ เพื่อ model curvature โดยยังเป็น linear regression ใน coefficients.
- **สิ่งที่ต้องจำ:** Degree $K$ เป็น complexity/hyperparameter.
- **การใช้งาน:** curvature within observed range.
- **ข้อควรระวัง:** เลือก degreeสูงเพราะ $R^2$ เพิ่มเสมอ.

## Related Notes

- [[Nonlinear Regression]]
- [[Spline and Growth Curve Regression]]
- [[Regularized Regression]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[10-NonlinearRegression_260711_160649 (1)]] | Quadratic / polynomial regression section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `10-NonlinearRegression_260711_160649 (1).pdf` — Quadratic / polynomial regression section

## External References

- [scikit-learn User Guide — Linear Models (Ridge, Lasso, Elastic Net, Logistic Regression).](https://scikit-learn.org/stable/modules/linear_model.html)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น

## DADS6003 Enrichment — Polynomial Features

Polynomial regression ยังเป็น **linear model in coefficients** แม้ relation ระหว่าง raw feature กับ response จะโค้งได้ ตัวอย่าง degree 2 สำหรับสอง features สามารถสร้าง terms เช่น $x_1$, $x_2$, $x_1x_2$, $x_1^2$, $x_2^2$ พร้อม intercept. Degree เป็น hyperparameter จึงควรเลือกด้วย validation/CV ไม่ใช่ training fit เพียงอย่างเดียว.

### Additional Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 3 - Multiple Linear Regression]] | Slide 10 | polynomial feature expansion and degree complexity |
