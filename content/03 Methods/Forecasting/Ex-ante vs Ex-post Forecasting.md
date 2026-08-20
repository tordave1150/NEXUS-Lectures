---
title: "Ex-ante vs Ex-post Forecasting"
aliases:
  - Ex-ante Forecast
  - Ex-post Forecast
topic_number: 18
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

# Ex-ante vs Ex-post Forecasting

> [!abstract] Summary
> Ex-ante forecast ใช้เฉพาะ predictor information ที่จะมีจริง ณ เวลาพยากรณ์ ส่วน ex-post forecast เสียบ actual future predictor values ภายหลังเพื่อแยกความผิดพลาดจาก predictor forecast กับ regression model.

## Why this concept matters

ความแตกต่างนี้สำคัญมากเมื่อ forecasting target ด้วย external drivers เพราะ overall error มาจากทั้ง model relationship และการทำนาย predictors.

## Core Idea

- Ex-ante = operationally honest forecast ณ origin.
- Ex-post = diagnostic/counterfactual forecast เมื่อรู้ predictors จริงแล้ว.
- ช่องว่าง ex-ante vs ex-post ช่วย diagnose predictor forecast uncertainty.
- Ex-post ไม่ใช่ผล performance ที่ deploy ได้จริงหาก future predictorsไม่รู้ล่วงหน้า.

## Mathematical Formulation / Technical Detail

Regression forecast:

$$
\hat y_{T+h|T}
=
\hat\beta_0+\sum_j\hat\beta_j\hat x_{j,T+h|T}
$$

คือ ex-ante.

Ex-post diagnostic ใช้:

$$
\tilde y_{T+h}
=
\hat\beta_0+\sum_j\hat\beta_j x_{j,T+h}
$$

โดย $x_{j,T+h}$ คือค่าจริงที่รู้ภายหลัง.

## Worked / Practical Example

ถ้า ex-ante MAPE = 60% แต่ ex-post MAPE = 8% แสดงว่าความเสียหายหลักน่าจะมาจาก predictor forecasts; ถ้าทั้งคู่ราว 60% แสดงว่า regression specification เองน่าจะมีปัญหามาก.

## Assumptions and Interpretation

- Comparisons ต้องใช้ regression coefficients ที่ estimate ก่อน future period.
- Ex-post ใช้เพื่อ diagnosis ไม่ควรถูกนำเสนอเป็น real-time forecast accuracy.

## When to use

- วิเคราะห์ source of forecast error.
- scenario planning เมื่อบาง predictors เป็น decisions ที่กำหนดล่วงหน้า.

## When not to use / Limitations

- ถ้า predictor ถูกกำหนดแน่นอนล่วงหน้า เช่น promotion plan คำว่า forecasted predictor อาจไม่เหมาะ; มันคือ known future input.

## Common Mistakes

- ใช้ future actual predictors แล้วเรียกผลว่า ex-ante.
- ลืม uncertainty ของ predictor forecasts ใน prediction intervals.
- เปรียบเทียบคนละ model fit ระหว่าง ex-ante และ ex-postจนแยกสาเหตุไม่ได้.

## Quick Review

- **Concept:** Ex-ante forecast ใช้เฉพาะ predictor information ที่จะมีจริง ณ เวลาพยากรณ์ ส่วน ex-post forecast เสียบ actual future predictor values ภายหลังเพื่อแยกความผิดพลาดจาก predictor forecast กับ regression model.
- **สิ่งที่ต้องจำ:** Ex-ante = operationally honest forecast ณ origin.
- **การใช้งาน:** วิเคราะห์ source of forecast error.
- **ข้อควรระวัง:** ใช้ future actual predictors แล้วเรียกผลว่า ex-ante.

## Related Notes

- [[Time Series Regression]]
- [[Dynamic Regression ARIMAX]]
- [[Prediction Intervals]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[06-TSRegression_260620_180251]] | Ex-ante vs ex-post forecasts section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `06-TSRegression_260620_180251.pdf` — Ex-ante vs ex-post forecasts section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
