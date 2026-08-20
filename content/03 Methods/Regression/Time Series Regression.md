---
title: "Time Series Regression"
aliases:
  - TS Regression
  - Regression Forecasting
topic_number: 17
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

# Time Series Regression

> [!abstract] Summary
> Time Series Regression ใช้ predictor variables เพื่ออธิบายหรือ forecast time-series target โดย regression equation เชื่อม $y_t$ กับ $x_{j,t}$.

## Why this concept matters

เมื่อ business drivers เช่น income, price, unemployment, promotion หรือ weather มีข้อมูลที่เป็นประโยชน์ regression สามารถใช้ information ที่ pure univariate model ไม่ได้ใช้.

## Core Idea

- Simple regression มี predictor เดียว; multiple regression มีหลาย predictors.
- Coefficient ตีความ ceteris paribus: เปลี่ยน predictor หนึ่งหน่วยโดยคง predictor อื่น.
- Forecasting ต้องมี future values/forecasts/scenarios ของ predictors.
- OLS regression บน time-series data ยังต้องตรวจ residual autocorrelation.

## Mathematical Formulation / Technical Detail

Multiple linear regression:

$$
y_t=\beta_0+\beta_1x_{1,t}+\cdots+\beta_kx_{k,t}+\varepsilon_t.
$$

OLS estimate เลือก $\beta$ ให้

$$
\sum_t (y_t-\hat y_t)^2
$$

ต่ำที่สุด.

## Worked / Practical Example

Lecture ใช้ New Car Sales กับ disposable income, unemployment rate, prime rate และ consumer sentiment. ถ้า coefficient ของ UMICS = 1122.43 การตีความคือ เมื่อ predictors อื่นคงที่ UMICS เพิ่ม 1 หน่วยสัมพันธ์กับ NCS เพิ่มเฉลี่ยประมาณ 1122 คัน — ไม่ใช่ causal effect โดยอัตโนมัติ.

## Assumptions and Interpretation

- Linearity in parameters และ conditional mean specification ต้องสมเหตุสมผล.
- สำหรับ classical inference มักสมมติ errors mean zero, constant variance และไม่ autocorrelated; normalityช่วย exact small-sample inference.
- Predictors อาจ endogenous; OLS association ไม่เท่ากับ causal effect.

## When to use

- forecasting with known/forecastable drivers.
- scenario analysis / what-if.

## When not to use / Limitations

- ถ้า predictor future valuesไม่ทราบและ forecast ยาก อาจทำให้ ex-ante forecast uncertainty สูง.
- ถ้า residual autocorrelationแรงควรพิจารณา Dynamic Regression.

## Common Mistakes

- ตีความ coefficient เป็น causalityโดยไม่ design ที่รองรับ.
- ใช้ actual future predictors เพื่ออ้าง ex-ante performance.
- ไม่ตรวจ multicollinearityและ residual dependence.

## Quick Review

- **Concept:** Time Series Regression ใช้ predictor variables เพื่ออธิบายหรือ forecast time-series target โดย regression equation เชื่อม $y_t$ กับ $x_{j,t}$.
- **สิ่งที่ต้องจำ:** Simple regression มี predictor เดียว; multiple regression มีหลาย predictors.
- **การใช้งาน:** forecasting with known/forecastable drivers.
- **ข้อควรระวัง:** ตีความ coefficient เป็น causalityโดยไม่ design ที่รองรับ.

## Related Notes

- [[Ex-ante vs Ex-post Forecasting]]
- [[Regression Assumptions and Diagnostics]]
- [[Dynamic Regression ARIMAX]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[06-TSRegression_260620_180251]] | Introduction / time-series linear regression section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `06-TSRegression_260620_180251.pdf` — Introduction / time-series linear regression section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
