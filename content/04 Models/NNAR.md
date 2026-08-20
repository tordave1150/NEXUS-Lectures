---
title: "NNAR"
aliases:
  - Neural Network Autoregression
  - NNETAR
topic_number: 40
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[12-NN_260718_091137]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# NNAR

> [!abstract] Summary
> NNAR ใช้ lagged target valuesเป็น inputsของ feed-forward neural network เพื่อเรียน nonlinear autoregressive relationship; seasonal NNARเพิ่ม seasonal lags.

## Why this concept matters

เป็น bridgeระหว่าง classical autoregressionกับ neural networkและเหมาะเมื่อ lag-response relationshipไม่เป็นเส้นตรง.

## Core Idea

- NNAR(p,k): p lag inputs, k hidden nodesใน common one-hidden-layer notation.
- Seasonal formเพิ่ม lags $y_{t-m},y_{t-2m},...$.
- Overlapping regular/seasonal lagsควรนับ input uniqueเพียงครั้งเดียว.
- Multi-step forecastsมัก recursiveหรือ simulation-basedขึ้นกับ implementation.

## Mathematical Formulation / Technical Detail

Nonseasonal schematic:

$$
\hat y_t=f(y_{t-1},\ldots,y_{t-p};W).
$$

Seasonal:

$$
\hat y_t=f(y_{t-1},\ldots,y_{t-p},
y_{t-m},y_{t-2m},\ldots;W).
$$

## Worked / Practical Example

NNAR(4,3) ใช้ lags 1–4 เข้า hidden layer 3 nodes. Seasonal monthly NNARอาจเพิ่ม lag 12,24. ถ้า pครอบ lag12อยู่แล้วอย่านับ duplicateเป็น inputเพิ่ม.

## Assumptions and Interpretation

- Lag featuresต้องสร้างจาก available history.
- NN forecasts sensitiveต่อ scaling/initialization; ensemblesหลาย fitsช่วยลด varianceในบาง implementations.

## When to use

- nonlinear autoregressive patterns.
- classical NN benchmarkสำหรับ time series.

## When not to use / Limitations

- short noisy seriesอาจ overfit.
- external covariatesต้องใช้ architecture/implementationที่รองรับ.

## Common Mistakes

- คิดว่า NNAR automaticallyเข้าใจ calendarโดยไม่มี seasonal lag/features.
- ใช้ test setเลือก p,k.
- ไม่ set seedเมื่อ reproducibilityสำคัญ.

## Quick Review

- **Concept:** NNAR ใช้ lagged target valuesเป็น inputsของ feed-forward neural network เพื่อเรียน nonlinear autoregressive relationship; seasonal NNARเพิ่ม seasonal lags.
- **สิ่งที่ต้องจำ:** NNAR(p,k): p lag inputs, k hidden nodesใน common one-hidden-layer notation.
- **การใช้งาน:** nonlinear autoregressive patterns.
- **ข้อควรระวัง:** คิดว่า NNAR automaticallyเข้าใจ calendarโดยไม่มี seasonal lag/features.

## Related Notes

- [[Neural Networks Fundamentals]]
- [[AR MA ARMA]]
- [[ML Time-Series Feature Engineering]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[12-NN_260718_091137]] | Neural Network Autoregression section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `12-NN_260718_091137.pdf` — Neural Network Autoregression section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
