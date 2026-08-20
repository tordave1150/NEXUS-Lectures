---
title: "Prediction Intervals"
aliases:
  - Forecast Interval
  - Prediction Interval
  - PI
topic_number: 49
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[02-probabilistic-forecast]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Prediction Intervals

> [!abstract] Summary
> Prediction Interval แสดงช่วงของ future observationตาม nominal coverage เช่น 80% หรือ 95%; ต่างจาก confidence intervalของ parameterและต้องรวม future process noise.

## Why this concept matters

Point forecastอย่างเดียวไม่บอก uncertainty; intervalช่วย capacity, inventoryและrisk decisions.

## Core Idea

- Coverageสูงขึ้น → intervalกว้างขึ้น.
- หลาย modelsมี forecast uncertaintyเพิ่มตาม horizon.
- Residual standard deviation $\hat\sigma$ ไม่เท่ากับ h-step forecast standard deviation $\hat\sigma_h$.
- Central PIใช้ lower/upper predictive quantiles.

## Mathematical Formulation / Technical Detail

ภายใต้ normal forecast distribution:

$$
\hat y_{T+h|T}\pm z_{1-\alpha/2}\hat\sigma_h.
$$

95% ใช้ประมาณ $z=1.96$, 80% ใช้ประมาณ 1.28.

## Worked / Practical Example

ถ้า point forecast=100 และ $\hat\sigma_h=20$, normal 95% PI≈[60.8,139.2]. สำหรับ horizonไกลขึ้นถ้า $\sigma_h$เพิ่ม ช่วงควรกว้างขึ้น.

## Assumptions and Interpretation

- Nominal 95%ไม่รับประกัน 95% coverageใน sampleสั้น; calibrationต้องประเมินหลาย forecasts.
- Ex-ante regression intervalsอาจไม่รวม uncertaintyของ predictor forecastsหาก softwareถือ predictors known.

## When to use

- communicate uncertainty.
- planning thresholds.
- evaluate interval calibration.

## When not to use / Limitations

- normal symmetric intervalไม่เหมาะกับ skewed/nonnegative targetบางกรณี;ใช้ distribution/quantilesที่เหมาะ.

## Common Mistakes

- สับสน confidence intervalของ meanกับ prediction interval.
- ใช้ residual sdแทน forecast sdทุก horizon.
- คิดว่า wider intervalดีกว่าเพราะ coverageสูงโดยไม่คำนึง sharpness.

## Quick Review

- **Concept:** Prediction Interval แสดงช่วงของ future observationตาม nominal coverage เช่น 80% หรือ 95%; ต่างจาก confidence intervalของ parameterและต้องรวม future process noise.
- **สิ่งที่ต้องจำ:** Coverageสูงขึ้น → intervalกว้างขึ้น.
- **การใช้งาน:** communicate uncertainty.
- **ข้อควรระวัง:** สับสน confidence intervalของ meanกับ prediction interval.

## Related Notes

- [[Probabilistic Forecasting]]
- [[CRPS]]
- [[Ex-ante vs Ex-post Forecasting]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[02-probabilistic-forecast]] | Prediction interval / forecast standard deviation section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `02-probabilistic-forecast.pdf` — Prediction interval / forecast standard deviation section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
