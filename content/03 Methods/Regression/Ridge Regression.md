---
title: "Ridge Regression"
aliases:
  - Ridge
  - L2 Regularization
topic_number: 35
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[11-RegularizedRegression_260718_091112]]"
  - "[[DADS6003 Week 6 - Regularization]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Ridge Regression

> [!abstract] Summary
> Ridge regression เพิ่ม L2 penalty $\lambda\sum_j\beta_j^2$ ทำให้ coefficientsหดเข้าหาศูนย์แต่โดยทั่วไปไม่เป็นศูนย์พอดี.

## Why this concept matters

Ridgeเหมาะเมื่อ predictorsจำนวนมากและ correlated เพราะกระจาย weightและลด coefficient variance.

## Core Idea

- $\lambda=0$ กลับเป็น OLS.
- $\lambda$ มาก → shrinkageมาก.
- Ridgeไม่ทำ hard feature selectionโดยธรรมชาติ.
- Scaling predictorsสำคัญ.

## Mathematical Formulation / Technical Detail

Ridge objective:

$$
\min_{\beta_0,\beta}
\frac1n\sum_i(y_i-\beta_0-x_i^\top\beta)^2
+\lambda\sum_{j=1}^p\beta_j^2.
$$

Intercept $\beta_0$ โดยทั่วไปไม่ penalized.

## Worked / Practical Example

ถ้า CPI และ PDI strongly correlated, OLSอาจให้ coefficientsใหญ่คนละ sign; Ridgeสามารถ shrinkทั้งคู่และให้ predictionเสถียรกว่า แม้ interpretationราย coefficientยังต้องระวัง.

## Assumptions and Interpretation

- CVเลือก lambdaบน training folds.
- Coefficient pathsช่วยเห็นผลของ shrinkage.

## When to use

- multicollinearity.
- predictorsหลายตัวที่เชื่อว่ามี small distributed effects.

## When not to use / Limitations

- ถ้าต้องการ sparse feature setชัดเจนอาจ Lasso/Elastic Netเหมาะกว่า.

## Common Mistakes

- คิดว่า Ridgeลบ features.
- ไม่ scale variables.
- ตีความ coefficientหลัง shrinkageเหมือน unbiased OLS estimateเพื่อ inference.

## Quick Review

- **Concept:** Ridge regression เพิ่ม L2 penalty $\lambda\sum_j\beta_j^2$ ทำให้ coefficientsหดเข้าหาศูนย์แต่โดยทั่วไปไม่เป็นศูนย์พอดี.
- **สิ่งที่ต้องจำ:** $\lambda=0$ กลับเป็น OLS.
- **การใช้งาน:** multicollinearity.
- **ข้อควรระวัง:** คิดว่า Ridgeลบ features.

## Related Notes

- [[Regularized Regression]]
- [[Lasso Regression]]
- [[Elastic Net]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[11-RegularizedRegression_260718_091112]] | Ridge regression section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `11-RegularizedRegression_260718_091112.pdf` — Ridge regression section

## External References

- [scikit-learn User Guide — Linear Models (Ridge, Lasso, Elastic Net, Logistic Regression).](https://scikit-learn.org/stable/modules/linear_model.html)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น

## DADS6003 Enrichment

DADS6003 แสดง coefficient path ที่ coefficients ค่อย ๆ หดเข้าใกล้ศูนย์เมื่อ regularization strength เพิ่มขึ้น แต่โดยทั่วไป Ridge ไม่ได้ทำ variable selection แบบ exact zero เหมือน Lasso. ใช้ร่วมกับ [[Feature Scaling]] และเลือก $\lambda$ ด้วย [[Cross Validation]].

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 6 - Regularization]] | Slides 10–13, 22–27 | Ridge objective, coefficient shrinkage and comparison |
