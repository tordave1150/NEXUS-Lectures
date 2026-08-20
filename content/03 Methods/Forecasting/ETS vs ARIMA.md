---
title: "ETS vs ARIMA"
aliases:
  - Exponential Smoothing vs ARIMA
  - ETS versus ARIMA
topic_number: 16
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[05-ARIMA_SARIMA]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# ETS vs ARIMA

> [!abstract] Summary
> ETS และ ARIMA เป็น classical forecasting families ที่เสริมกัน: ETS model level/trend/seasonality ผ่าน state components ขณะที่ ARIMA เน้น autocorrelation ของ differenced series.

## Why this concept matters

ไม่มี family ใดครองทุก dataset; การเข้าใจ representation ต่างกันช่วยเลือก candidate models และอธิบายเหตุผลของ forecast.

## Core Idea

- ETS เหมาะกับ structural components เช่น level, trend, seasonality.
- ARIMA เหมาะกับ stochastic dependence และ differencing.
- บาง ETS models มี ARIMA-equivalent point forecasts แต่ families โดยรวมไม่เท่ากัน.
- เลือกด้วย out-of-sample accuracy, residual diagnostics และ operational constraints มากกว่าชื่อ family.

## Mathematical Formulation / Technical Detail

ตัวอย่าง conceptual contrast:

ETS(A,N,N):
$$
\ell_t=\alpha y_t+(1-\alpha)\ell_{t-1}
$$

ARIMA(0,1,1):
$$
(1-B)y_t=(1+\theta B)\varepsilon_t.
$$

ภายใต้ parameter mapping บางกรณี SES และ ARIMA(0,1,1) ให้ point forecasts ที่เกี่ยวข้องกัน แต่ prediction distributions และ allowed structures ต้องดู specification.

## Worked / Practical Example

ถ้า monthly sales มี stable local level และ seasonality ETS อาจตีความง่าย; ถ้า differenced data มีชัดเจน AR/MA dynamics ARIMA อาจเหมาะกว่า. ควร fit ทั้งคู่เป็น candidate แล้ว evaluate บน CV.

## Assumptions and Interpretation

- ใช้ข้อมูลและ forecast horizon เดียวกันในการเปรียบเทียบ.
- AIC จาก ETS และ ARIMAอาจใช้ภายใน likelihood framework แต่ out-of-sample accuracy ยังเป็นหลักฐานตรงต่อ forecasting goal.

## When to use

- สร้าง strong classical benchmark set.
- เมื่อไม่แน่ใจว่า structural smoothing หรือ autocorrelation representation เหมาะกว่า.

## When not to use / Limitations

- อย่าประกาศว่า ARIMA 'ดีกว่า' ETS หรือกลับกันโดยทั่วไป.
- external predictors ต้องใช้ regression extensions.

## Common Mistakes

- เปรียบเทียบ training RMSE อย่างเดียว.
- เลือก model เพราะ formula ดูซับซ้อนกว่า.
- คิดว่า ETS จับ autocorrelationไม่ได้เลยหรือ ARIMA จับ trendไม่ได้เลย — ทั้งคู่สร้าง forecasts ของ pattern ได้แต่ representation ต่างกัน.

## Quick Review

- **Concept:** ETS และ ARIMA เป็น classical forecasting families ที่เสริมกัน: ETS model level/trend/seasonality ผ่าน state components ขณะที่ ARIMA เน้น autocorrelation ของ differenced series.
- **สิ่งที่ต้องจำ:** ETS เหมาะกับ structural components เช่น level, trend, seasonality.
- **การใช้งาน:** สร้าง strong classical benchmark set.
- **ข้อควรระวัง:** เปรียบเทียบ training RMSE อย่างเดียว.

## Related Notes

- [[Exponential Smoothing and ETS]]
- [[ETS Models and Model Selection]]
- [[ARIMA]]
- [[Time Series Cross Validation]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[05-ARIMA_SARIMA]] | Applications / ETS vs ARIMA section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `05-ARIMA_SARIMA.pdf` — Applications / ETS vs ARIMA section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
