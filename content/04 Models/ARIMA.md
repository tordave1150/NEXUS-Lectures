---
title: "ARIMA"
aliases:
  - ARIMA Model
  - Autoregressive Integrated Moving Average
topic_number: 14
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

# ARIMA

> [!abstract] Summary
> ARIMA(p,d,q) ทำ stationary differenced series แล้ว model autocorrelation ด้วย AR(p) และ MA(q). ตัว I = Integrated หมายถึงการย้อนรวม differencing เพื่อ forecast original scale.

## Why this concept matters

ARIMA เป็น classical approach สำคัญสำหรับ series ที่ autocorrelation เป็นแกนหลัก โดยไม่ต้องกำหนด trend/season components แบบ ETS.

## Core Idea

- $p$ = AR order, $d$ = differencing order, $q$ = MA order.
- ARIMA(0,1,0) คือ random walk; ถ้ามี constant ใน differenced equationอาจเป็น random walk with drift.
- Differencing มากเกินไปเพิ่ม noise และอาจสร้าง artificial negative autocorrelation.
- Automatic ARIMA มักค้น orders ด้วย AICc พร้อม unit-root/differencing heuristics.

## Mathematical Formulation / Technical Detail

Backshift form:

$$
\phi(B)(1-B)^d y_t=c+\theta(B)\varepsilon_t.
$$

เมื่อ $d=1$:

$$
y'_t=(1-B)y_t=y_t-y_{t-1}.
$$

ARIMA(0,1,0):

$$
y_t=y_{t-1}+\varepsilon_t.
$$

## Worked / Practical Example

ถ้า throughput เติบโตและ first difference ดู stationary อาจใช้ $d=1$. จากนั้น AR/MA terms model persistence ของ changes และ shocks. Forecast หลาย steps ใช้ past observations/residuals และแทน future innovations ด้วย expected value 0.

## Assumptions and Interpretation

- หลัง differencing ส่วน ARMA ควร stationary/invertible ตามเงื่อนไข model.
- Residual innovations หลัง fit ควรใกล้ white noise.

## When to use

- univariate series ที่ trend แก้ได้ด้วย differencingและมี autocorrelation.
- baseline classical model สำหรับหลาย business series.

## When not to use / Limitations

- ไม่ capture causal/exogenous drivers เว้นแต่ขยายเป็น dynamic regression.
- seasonal structure ต้องใช้ SARIMAหรือ alternatives.

## Common Mistakes

- คิดว่า $d$ ยิ่งมากยิ่งดี.
- เลือก p,d,q จาก training fit อย่างเดียว.
- ตีความ ARIMA coefficients บน original level โดยไม่คำนึง differencing.

## Quick Review

- **Concept:** ARIMA(p,d,q) ทำ stationary differenced series แล้ว model autocorrelation ด้วย AR(p) และ MA(q). ตัว I = Integrated หมายถึงการย้อนรวม differencing เพื่อ forecast original scale.
- **สิ่งที่ต้องจำ:** $p$ = AR order, $d$ = differencing order, $q$ = MA order.
- **การใช้งาน:** univariate series ที่ trend แก้ได้ด้วย differencingและมี autocorrelation.
- **ข้อควรระวัง:** คิดว่า $d$ ยิ่งมากยิ่งดี.

## Related Notes

- [[AR MA ARMA]]
- [[SARIMA]]
- [[ETS vs ARIMA]]
- [[Dynamic Regression ARIMAX]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[05-ARIMA_SARIMA]] | Non-seasonal ARIMA section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `05-ARIMA_SARIMA.pdf` — Non-seasonal ARIMA section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
