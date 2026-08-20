---
title: "Regression Assumptions and Diagnostics"
aliases:
  - Regression Diagnostics
  - OLS Assumptions
topic_number: 19
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[06-TSRegression_260620_180251]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Regression Assumptions and Diagnostics

> [!abstract] Summary
> Regression diagnostics ตรวจว่า functional form, residual behavior, variance และ predictor relationships สอดคล้องกับ assumptions มากพอสำหรับ prediction/inference หรือไม่.

## Why this concept matters

Good fit ไม่เพียงดู $R^2$; residual plots และ out-of-sample performance อาจเปิดเผย nonlinearity, heteroskedasticity, autocorrelation และ influential observations.

## Core Idea

- Linearity หมายถึง conditional mean ถูกระบุเป็น linear in parameters—not necessarily raw straight line if transformations/polynomials included.
- Errors ควร mean zero conditional on predictors.
- Homoskedasticity สำคัญต่อ standard errors แบบ classical.
- Time-series regression ต้องตรวจ autocorrelation.
- Multicollinearityทำให้ coefficientsไม่เสถียรแต่ไม่ได้สร้าง bias โดยตัวมันเองเมื่อ assumptions อื่นถูก.
- Outliers/high leverage สามารถเปลี่ยน fit อย่างมาก.

## Mathematical Formulation / Technical Detail

Residual:

$$
e_t=y_t-\hat y_t.
$$

Variance inflation factor (แนวคิด):

$$
VIF_j=\frac{1}{1-R_j^2},
$$

โดย $R_j^2$ มาจาก regression ของ predictor $j$ บน predictors อื่น.

## Worked / Practical Example

ถ้า residual vs fitted เป็นรูปโค้ง แสดง linear specification อาจขาด nonlinear term; ถ้า residual spread โตตาม fitted อาจมี heteroskedasticity; ถ้า residual ACF สูงควรพิจารณา ARIMA errors.

## Assumptions and Interpretation

- Diagnostics เป็น evidence ไม่ใช่ checkbox.
- Inference robust methods เช่น heteroskedasticity-consistent SE แก้ standard errors แต่ไม่ได้แก้ misspecified conditional mean.

## When to use

- ก่อนตีความ coefficients.
- ก่อนใช้ regression forecast.
- หลังเปลี่ยน features/model.

## When not to use / Limitations

- อย่า reject model เพียงเพราะ residualsไม่ perfectly normal เมื่อ objective เป็น point forecastingและ sample ใหญ่.
- อย่าใช้ $R^2$ เป็น forecast metric.

## Common Mistakes

- คิดว่า high $R^2$ = good forecast.
- ทดสอบ assumptions จำนวนมากแล้วตีความ p-value แบบกลไก.
- ลืม temporal diagnostics.

## Quick Review

- **Concept:** Regression diagnostics ตรวจว่า functional form, residual behavior, variance และ predictor relationships สอดคล้องกับ assumptions มากพอสำหรับ prediction/inference หรือไม่.
- **สิ่งที่ต้องจำ:** Linearity หมายถึง conditional mean ถูกระบุเป็น linear in parameters—not necessarily raw straight line if transformations/polynomials included.
- **การใช้งาน:** ก่อนตีความ coefficients.
- **ข้อควรระวัง:** คิดว่า high $R^2$ = good forecast.

## Related Notes

- [[Time Series Regression]]
- [[Dynamic Regression ARIMAX]]
- [[Nonlinear Regression]]
- [[Regularized Regression]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[06-TSRegression_260620_180251]] | Regression assumptions / diagnostic tests section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `06-TSRegression_260620_180251.pdf` — Regression assumptions / diagnostic tests section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น


## Statistics Course Enrichment — 2026-08-15

- Added inferential/statistical-model context from [[8Correlation-Regression1_2_68_260502_155920]]: Error assumptions, residual analysis and model suitability.
- Detailed coefficient tests, $R^2$, and mean-response vs new-observation uncertainty are separated into [[Regression Inference]], [[Coefficient of Determination R-Squared]], and [[Regression Confidence vs Prediction Intervals]] to preserve one canonical concept per note.
