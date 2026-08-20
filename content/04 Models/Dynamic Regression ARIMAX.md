---
title: "Dynamic Regression ARIMAX"
aliases:
  - Dynamic Regression
  - ARIMAX
  - Regression with ARIMA Errors
topic_number: 23
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[08-DynamicRegression_260627_151638]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Dynamic Regression ARIMAX

> [!abstract] Summary
> Dynamic regression รวม regression predictors กับ ARIMA error process เพื่อให้ external drivers อธิบาย mean และ ARIMA จับ temporal dependence ที่เหลือใน residuals.

## Why this concept matters

OLS ที่ residuals autocorrelatedอาจให้ standard errors/significance ผิดและ forecast structureไม่ครบ; ARIMA errorsแก้ dependence โดยตรง.

## Core Idea

- Regression error $\eta_t$ อาจ autocorrelated; innovation $\varepsilon_t$ ภายใน ARIMAควร white noise.
- คำว่า ARIMAX ใช้ไม่เหมือนกันทุกแหล่ง; FPP แนะนำคำว่า regression with ARIMA errors/dynamic regression.
- Differencing มี implication ต่อ regression coefficients; software formulationต้องอ่าน.
- Future predictorsยังจำเป็นสำหรับ forecasting.

## Mathematical Formulation / Technical Detail

Model:

$$
y_t=\beta_0+\sum_{j=1}^k\beta_jx_{j,t}+\eta_t
$$

และ

$$
\phi(B)(1-B)^d\eta_t=\theta(B)\varepsilon_t.
$$

มี error สองระดับ: regression error $\eta_t$ และ white-noise innovation $\varepsilon_t$.

## Worked / Practical Example

New Car Sales regression อาจมี residual autocorrelationหลัง OLS. การ fit ARIMA errorsทำให้ standard errorsและ forecast intervalsสะท้อน serial dependence และบาง predictorsที่เคยดู significantอาจไม่ significantอีก.

## Assumptions and Interpretation

- Predictors ควร exogenous/appropriately specifiedสำหรับ interpretation.
- Innovation diagnosticsหลัง fitยังต้องตรวจ.

## When to use

- regression forecast ที่ residuals autocorrelated.
- external drivers + time-series dynamics.

## When not to use / Limitations

- ถ้า predictorsเองต้อง forecast ความไม่แน่นอนของ predictorต้องจัดการ.
- ไม่ใช่ causal modelโดยอัตโนมัติ.

## Common Mistakes

- เรียกทุก ARIMA+X formulationว่าเดียวกันโดยไม่ดู software convention.
- ใช้ OLS p-valuesเมื่อ residuals serially correlated.
- เปรียบ AIC ของ OLS และ ARIMA-error modelsที่ likelihood/dataไม่ comparableแบบกลไก.

## Cross-check / Correction

> [!warning] Verification note
> คำว่า ARIMAX มีหลาย convention; ใน note นี้ใช้ความหมาย regression with ARIMA errors ตาม workflow ของ lecture/FPP และระบุ equation ทุกครั้งเพื่อหลีกเลี่ยงความกำกวม.

## Quick Review

- **Concept:** Dynamic regression รวม regression predictors กับ ARIMA error process เพื่อให้ external drivers อธิบาย mean และ ARIMA จับ temporal dependence ที่เหลือใน residuals.
- **สิ่งที่ต้องจำ:** Regression error $\eta_t$ อาจ autocorrelated; innovation $\varepsilon_t$ ภายใน ARIMAควร white noise.
- **การใช้งาน:** regression forecast ที่ residuals autocorrelated.
- **ข้อควรระวัง:** เรียกทุก ARIMA+X formulationว่าเดียวกันโดยไม่ดู software convention.

## Related Notes

- [[Time Series Regression]]
- [[ARIMA]]
- [[Transfer Function Model TFM]]
- [[Deterministic vs Stochastic Trend]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[08-DynamicRegression_260627_151638]] | Regression with ARIMA errors section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `08-DynamicRegression_260627_151638.pdf` — Regression with ARIMA errors section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
