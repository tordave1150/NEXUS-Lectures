---
title: "Transfer Function Model TFM"
aliases:
  - Transfer Function Model
  - TFM
  - Lagged Predictor Dynamic Regression
topic_number: 25
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

# Transfer Function Model TFM

> [!abstract] Summary
> Transfer Function Model ขยาย dynamic regression ให้ predictor มี distributed lag effect: $x_t,x_{t-1},...$ สามารถส่งผลต่อ targetทันที ล่าช้า หรือค่อย ๆ decay.

## Why this concept matters

ธุรกิจจำนวนมากมี delayed response เช่น advertising, maintenance, lead time และ promotion; contemporaneous regressionเพียงตัวเดียวอาจ miss dynamics.

## Core Idea

- Lag coefficientsเรียก impulse-response/transfer-function weightsใน simple finite distributed lag form.
- Error processยังสามารถเป็น ARIMA.
- Lag lengthควร guided by business logic และตรวจด้วย AICc/CV.
- Models ที่เปรียบเทียบ lag lengthsต้องใช้ common fitting sampleเพื่อ fairness.

## Mathematical Formulation / Technical Detail

Finite distributed lag:

$$
y_t=\beta_0+\omega_0x_t+\omega_1x_{t-1}+\cdots+\omega_kx_{t-k}+\eta_t,
$$

โดย $\eta_t$ follows ARIMA.

Backshift:

$$
y_t=\beta_0+\omega(B)x_t+\eta_t.
$$

## Worked / Practical Example

Advertising $x_t$ อาจเพิ่ม salesทันที $\omega_0>0$ และยังมี carryoverที่ $t-1,t-2$. ถ้า coefficientหลัง lag 3 เล็กมาก การใช้ lag 5อาจเพิ่ม varianceโดยไม่เพิ่ม signal.

## Assumptions and Interpretation

- Lagged predictorsต้องพร้อม ณ forecast origin; future x valuesอาจต้อง forecast/plan.
- Highly correlated adjacent lagsทำให้ individual coefficientsไม่เสถียร; cumulative effectอาจมีความหมายกว่า.

## When to use

- marketing response.
- supply-chain delayed effects.
- policy/intervention dynamics.

## When not to use / Limitations

- lag structureยาวมากอาจต้อง regularization/parametric transfer function.
- causal interpretationต้องมี identification ไม่ใช่แค่ lag.

## Common Mistakes

- สร้าง lag จำนวนมากแล้วเลือกจาก p-valueทีละตัว.
- เปรียบ AIC modelsคนละ training rows.
- ใช้ future lag/rolling featureที่ยังไม่ทราบจริง.

## Quick Review

- **Concept:** Transfer Function Model ขยาย dynamic regression ให้ predictor มี distributed lag effect: $x_t,x_{t-1},...$ สามารถส่งผลต่อ targetทันที ล่าช้า หรือค่อย ๆ decay.
- **สิ่งที่ต้องจำ:** Lag coefficientsเรียก impulse-response/transfer-function weightsใน simple finite distributed lag form.
- **การใช้งาน:** marketing response.
- **ข้อควรระวัง:** สร้าง lag จำนวนมากแล้วเลือกจาก p-valueทีละตัว.

## Related Notes

- [[Dynamic Regression ARIMAX]]
- [[Lagged Variables and Lag Plots]]
- [[Regularized Regression]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[08-DynamicRegression_260627_151638]] | Transfer function models / lagged predictors section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `08-DynamicRegression_260627_151638.pdf` — Transfer function models / lagged predictors section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
