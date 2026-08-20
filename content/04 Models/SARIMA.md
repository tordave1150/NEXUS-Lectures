---
title: "SARIMA"
aliases:
  - Seasonal ARIMA
  - SARIMA Model
topic_number: 15
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

# SARIMA

> [!abstract] Summary
> SARIMA ขยาย ARIMA ด้วย seasonal AR, seasonal differencing และ seasonal MA terms เพื่อ model autocorrelation ที่ seasonal lags.

## Why this concept matters

Series ที่มีทั้ง short-term dependence และ repeating seasonal dependenceต้องแยก non-seasonal กับ seasonal dynamics.

## Core Idea

- เขียนเป็น ARIMA$(p,d,q)(P,D,Q)_m$.
- $m$ คือ seasonal period เช่น 12 สำหรับ monthly annual seasonality.
- Seasonal differencing คือ $y_t-y_{t-m}$.
- Seasonal AR/MA terms ทำงานที่ lags $m,2m,\ldots$.

## Mathematical Formulation / Technical Detail

General form:

$$
\Phi(B^m)\phi(B)(1-B)^d(1-B^m)^D y_t
=
c+\Theta(B^m)\theta(B)\varepsilon_t.
$$

Seasonal difference:

$$
(1-B^m)y_t=y_t-y_{t-m}.
$$

## Worked / Practical Example

Monthly sales ที่มี annual seasonalityอาจเริ่มด้วย $m=12$. ถ้า seasonal pattern ใน level ทำให้ seasonal ACF persistence สูง การ seasonal difference $D=1$ จะเปรียบเดือนเดียวกันข้ามปี ก่อน model remaining ARMA structure.

## Assumptions and Interpretation

- เลือก $D$ เท่าที่จำเป็น; seasonal overdifferencing ก็เป็นปัญหา.
- SARIMA เหมาะกับ integer seasonal periods ที่ไม่ยาวเกินไป.

## When to use

- monthly/quarterly series ที่ seasonal autocorrelation ชัด.
- ใช้เมื่อต้องการ stochastic seasonal dynamics.

## When not to use / Limitations

- complex multiple seasonality ยาวมากอาจเหมาะกับ DHR/MSTL/TBATS มากกว่า.
- ไม่ควรใส่ seasonal orders โดยอัตโนมัติเพียงเพราะ data เป็นรายเดือน.

## Common Mistakes

- สับสน $d$ กับ $D$.
- คิดว่า seasonal dummy กับ seasonal differencingเหมือนกัน.
- ไม่ตรวจ residual seasonal ACF หลัง fit.

## Quick Review

- **Concept:** SARIMA ขยาย ARIMA ด้วย seasonal AR, seasonal differencing และ seasonal MA terms เพื่อ model autocorrelation ที่ seasonal lags.
- **สิ่งที่ต้องจำ:** เขียนเป็น ARIMA$(p,d,q)(P,D,Q)_m$.
- **การใช้งาน:** monthly/quarterly series ที่ seasonal autocorrelation ชัด.
- **ข้อควรระวัง:** สับสน $d$ กับ $D$.

## Related Notes

- [[ARIMA]]
- [[Complex Seasonality]]
- [[Dynamic Harmonic Regression]]
- [[Exponential Smoothing and ETS|ETS]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[05-ARIMA_SARIMA]] | Seasonal ARIMA section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `05-ARIMA_SARIMA.pdf` — Seasonal ARIMA section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
