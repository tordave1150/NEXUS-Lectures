---
title: "Probabilistic Forecasting"
aliases:
  - Distributional Forecast
  - Forecast Uncertainty
  - Probabilistic Forecast
topic_number: 44
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[13-probabilistic-forecast_260725_090945]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Probabilistic Forecasting

> [!abstract] Summary
> Probabilistic Forecasting ทำนาย uncertainty ของ future outcome ไม่ใช่แค่ค่าจุด โดยอาจรายงาน quantiles, prediction intervals, event probabilities, samples หรือ full predictive distribution.

## Why this concept matters

Decision problemsจำนวนมาก nonlinearใน uncertain demand/cost จึงต้องรู้ distribution ไม่ใช่ meanอย่างเดียว เช่น service level, shortage risk และ tail risk.

## Core Idea

- Point forecastสรุป locationหนึ่งค่า; distribution forecastอธิบาย rangeและprobability.
- Quantile $q_p$ satisfies $P(Y\le q_p)=p$ สำหรับ continuous distributions.
- Prediction intervalคือช่วงที่มี nominal coverage.
- Event probabilityตอบคำถามเช่น $P(Demand>Capacity)$.
- Proper scoring rulesช่วย evaluate distribution forecasts.

## Mathematical Formulation / Technical Detail

Predictive CDF:

$$
F_{T+h|T}(y)=P(Y_{T+h}\le y\mid\mathcal F_T).
$$

$p$-quantile:

$$
q_p=F^{-1}(p).
$$

Central $(1-\alpha)$ interval:

$$
[q_{\alpha/2},q_{1-\alpha/2}].
$$

## Worked / Practical Example

Inventory Type-1 service level 97% ต้อง stockใกล้ 97th percentileของ demand distribution ไม่ใช่ mean. ถ้า objectiveมี $\min(Q,D)$ expected profitไม่สามารถหาได้จาก $E[D]$เพียงอย่างเดียว.

## Assumptions and Interpretation

- Calibration: eventsควรเกิดตาม probabilityที่ประกาศในระยะยาว.
- Sharpness: distributionควรแคบเท่าที่ calibrationยังดี.
- Model evaluationควรใช้ proper score เช่น CRPS/NLL/quantile scoreตาม forecast representation.

## When to use

- inventory/capacity/risk decisions.
- ต้องการ prediction intervals.
- forecast competitionsและuncertainty-aware planning.

## When not to use / Limitations

- ถ้า downstream decision linearจริง point meanอาจเพียงพอ แต่ distributionยังมี valueด้าน communication/risk.

## Common Mistakes

- รายงาน 95% intervalแล้วเรียกว่า 95% ของ realized observationsจะอยู่ทุก sampleเล็ก.
- ใช้ interval widthอย่างเดียวโดยไม่ดู coverage.
- evaluate quantileด้วย RMSEอย่างเดียว.

## Quick Review

- **Concept:** Probabilistic Forecasting ทำนาย uncertainty ของ future outcome ไม่ใช่แค่ค่าจุด โดยอาจรายงาน quantiles, prediction intervals, event probabilities, samples หรือ full predictive distribution.
- **สิ่งที่ต้องจำ:** Point forecastสรุป locationหนึ่งค่า; distribution forecastอธิบาย rangeและprobability.
- **การใช้งาน:** inventory/capacity/risk decisions.
- **ข้อควรระวัง:** รายงาน 95% intervalแล้วเรียกว่า 95% ของ realized observationsจะอยู่ทุก sampleเล็ก.

## Related Notes

- [[Prediction Intervals]]
- [[Quantile Forecast and Quantile Score]]
- [[CRPS]]
- [[VaR and CVaR]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[13-probabilistic-forecast_260725_090945]] | Representing forecast uncertainty / motivation | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `13-probabilistic-forecast_260725_090945.pdf` — Representing forecast uncertainty / motivation

## External References

- [Gneiting, T. & Raftery, A.E. (2007), Strictly Proper Scoring Rules, Prediction, and Estimation, JASA 102(477), 359–378.](https://doi.org/10.1198/016214506000001437)
- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
