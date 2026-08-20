---
title: "AR MA ARMA"
aliases:
  - AR Model
  - MA Model
  - ARMA
topic_number: 13
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

# AR MA ARMA

> [!abstract] Summary
> ARMA family model serial dependence ของ stationary series ผ่าน past values (AR) และ past innovations/shocks (MA).

## Why this concept matters

การแยก memory of levels กับ memory of shocks เป็นพื้นฐานก่อนเข้า ARIMA/SARIMA และช่วยอ่าน ACF/PACF.

## Core Idea

- AR(p): current value depends linearly on past $p$ values.
- MA(q): current value depends on current and past $q$ innovations.
- ARMA(p,q) รวมทั้งสองส่วน.
- AR models ต้องมี stationarity conditions; MA models มักกำหนด invertibility เพื่อ representation ที่เป็นเอกลักษณ์.

## Mathematical Formulation / Technical Detail

AR(p):

$$
y_t=c+\phi_1y_{t-1}+\cdots+\phi_py_{t-p}+\varepsilon_t.
$$

MA(q):

$$
y_t=c+\varepsilon_t+\theta_1\varepsilon_{t-1}+\cdots+\theta_q\varepsilon_{t-q}.
$$

ARMA(p,q) รวมสองสมการ:

$$
y_t=c+\sum_{i=1}^p\phi_i y_{t-i}+\varepsilon_t+\sum_{j=1}^q\theta_j\varepsilon_{t-j}.
$$

## Worked / Practical Example

Warehouse backlog AR(2) อาจใช้ backlog 1–2 วันที่ผ่านมา ส่วน MA(1) อาจสะท้อน disruption เมื่อวานที่ยังส่งผลต่อวันนี้. ARMA(2,1) จึงรวม persistence ของ level กับ shock memory.

## Assumptions and Interpretation

- $\varepsilon_t$ ควรเป็น white-noise innovations.
- Sign convention ของ MA coefficients ต่างกันได้ระหว่างตำรา/software; ต้องดูนิยามของ package.

## When to use

- stationary serially correlated series.
- เป็น error model ภายใน dynamic regression.

## When not to use / Limitations

- ถ้ามี stochastic trend ควรพิจารณา differencing/ARIMA.
- อย่าเลือก order จาก ACF/PACF อย่างเดียวโดยไม่ validate.

## Common Mistakes

- สับสน MA(q) model กับ moving-average smoother.
- ตีความ $\varepsilon_{t-1}$ เป็น observed target แทน innovation.
- copy formula ข้าม software โดยไม่ตรวจ sign convention.

## Cross-check / Correction

> [!warning] Verification note
> คำว่า MA ใน ARMA = Moving Average of *innovations*, ไม่ใช่ simple rolling mean ของ observations.

## Quick Review

- **Concept:** ARMA family model serial dependence ของ stationary series ผ่าน past values (AR) และ past innovations/shocks (MA).
- **สิ่งที่ต้องจำ:** AR(p): current value depends linearly on past $p$ values.
- **การใช้งาน:** stationary serially correlated series.
- **ข้อควรระวัง:** สับสน MA(q) model กับ moving-average smoother.

## Related Notes

- [[Autocorrelation and ACF]]
- [[ARIMA]]
- [[Dynamic Regression ARIMAX]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[05-ARIMA_SARIMA]] | Non-seasonal ARIMA foundations: AR, MA, ARMA | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `05-ARIMA_SARIMA.pdf` — Non-seasonal ARIMA foundations: AR, MA, ARMA

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
