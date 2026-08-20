---
title: "Quantile Regression"
aliases:
  - Regression Quantiles
  - Conditional Quantile Regression
topic_number: 55
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[S2-ML_260725_130143]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Quantile Regression

> [!abstract] Summary
> Quantile Regression model conditional quantile $Q_Y(\tau|X)$ โดย minimize pinball/check lossแทน squared loss จึงทำนาย medianหรือ high/low conditional quantilesได้โดยตรง.

## Why this concept matters

OLSตอบ conditional mean; quantile regressionตอบ distributional heterogeneityและ asymmetric planning เช่น stockระดับ 95th percentile conditional on price/features.

## Core Idea

- $\tau=0.5$ estimate conditional median.
- High $\tau$ lineไม่จำเป็น parallelกับ median line.
- Robustต่อ vertical outliersมากกว่า OLS median regressionในบาง sense.
- Quantilesหลายระดับ fitแยกอาจเกิด crossing; advanced methods impose monotonicity.

## Mathematical Formulation / Technical Detail

Linear quantile model:

$$
Q_Y(\tau|x)=\beta_0(\tau)+x^\top\beta(\tau).
$$

Check loss:

$$
\rho_\tau(u)=u(\tau-\mathbf1\{u<0\}).
$$

Estimate:

$$
\hat\beta(\tau)=\arg\min_\beta\sum_i\rho_\tau(y_i-x_i^\top\beta).
$$

## Worked / Practical Example

Price=1.80 และ fitted 75th-percentile sales lineให้ 8.25 thousand gallons หมายถึง conditional 75th percentileของ salesประมาณ 8.25ภายใต้ model; inventory service interpretationต้อง match demand processและcost definition.

## Assumptions and Interpretation

- Quantile regressionไม่สมมติ normal residual distributionเพื่อ define conditional quantile.
- Inferenceมี methodsเฉพาะ; OLS SEใช้ตรง ๆไม่ได้.

## When to use

- conditional service levels.
- heteroskedastic response.
- distributional regression.

## When not to use / Limitations

- ถ้าต้อง full distributionอาจใช้หลาย quantilesหรือdistributional model.
- extreme quantilesต้อง dataมาก.

## Common Mistakes

- เรียก p=.75ว่า 75% ของ predictionsจะ exact.
- ตีความ coefficientเหมือน mean effect.
- ใช้ quantile crossingโดยไม่ตรวจ.

## Quick Review

- **Concept:** Quantile Regression model conditional quantile $Q_Y(\tau|X)$ โดย minimize pinball/check lossแทน squared loss จึงทำนาย medianหรือ high/low conditional quantilesได้โดยตรง.
- **สิ่งที่ต้องจำ:** $\tau=0.5$ estimate conditional median.
- **การใช้งาน:** conditional service levels.
- **ข้อควรระวัง:** เรียก p=.75ว่า 75% ของ predictionsจะ exact.

## Related Notes

- [[Quantile Forecast and Quantile Score]]
- [[Probabilistic Forecasting]]
- [[Log Transformation and Elasticity]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[S2-ML_260725_130143]] | Quantile regression section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `S2-ML_260725_130143.pdf` — Quantile regression section

## External References

- [Koenker, R. & Bassett, G. (1978), Regression Quantiles, Econometrica 46(1), 33–50.](https://doi.org/10.2307/1913643)
- [Gneiting, T. & Raftery, A.E. (2007), Strictly Proper Scoring Rules, Prediction, and Estimation, JASA 102(477), 359–378.](https://doi.org/10.1198/016214506000001437)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
