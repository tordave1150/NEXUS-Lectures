---
title: "CRPS"
aliases:
  - Continuous Ranked Probability Score
  - Distributional Forecast Score
topic_number: 48
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

# CRPS

> [!abstract] Summary
> CRPS ประเมิน full univariate predictive distributionโดยเปรียบ forecast CDFกับ step functionของ observation; ค่ายิ่งต่ำยิ่งดีและมีหน่วยเดียวกับ target.

## Why this concept matters

CRPSรวม calibrationและsharpnessใน proper scoreเดียวและสามารถมองเป็นการ aggregate quantile lossesทั่วทุก probabilities.

## Core Idea

- ใช้กับ entire distribution ไม่ใช่ point forecast.
- Lower CRPS = better distributional forecast.
- สำหรับ deterministic point-mass forecast CRPSลดรูปเป็น absolute error.
- CRPSไม่ไวต่อ tailเฉพาะระดับเท่า NLLในบางสถานการณ์; metric choiceขึ้นกับ objective.

## Mathematical Formulation / Technical Detail

Definition:

$$
CRPS(F,y)=
\int_{-\infty}^{\infty}
\left(F(z)-\mathbf 1\{y\le z\}\right)^2dz.
$$

อีกมุมหนึ่ง CRPSเชื่อมกับ integral/averageของ quantile scoresทั่ว $p\in(0,1)$.

## Worked / Practical Example

ถ้า Model Aให้ distributionกว้างมากจน actualมักอยู่ในช่วงแต่ไม่ sharp และ Model Bแคบเกินจน missบ่อย CRPSลงโทษทั้งสองด้าน; modelที่ calibratedและsharpจะได้ scoreต่ำกว่า.

## Assumptions and Interpretation

- ต้อง evaluateบน genuine future observations.
- CRPS valuesเปรียบข้าม seriesต่าง scaleโดยตรงไม่เหมาะถ้าไม่ scale/skill-score.

## When to use

- compare probabilistic forecasting models.
- distributional neural/classical forecasts.

## When not to use / Limitations

- multivariate dependenceต้องใช้ multivariate scoring rulesอื่น; univariate CRPSไม่เห็น joint dependenceทั้งหมด.

## Common Mistakes

- พูดว่า CRPSยิ่งมากยิ่งดี.
- ใช้ CRPSแทน tail-specific business lossโดยไม่ตรวจ.
- เปรียบ raw CRPSข้าม target units.

## Quick Review

- **Concept:** CRPS ประเมิน full univariate predictive distributionโดยเปรียบ forecast CDFกับ step functionของ observation; ค่ายิ่งต่ำยิ่งดีและมีหน่วยเดียวกับ target.
- **สิ่งที่ต้องจำ:** ใช้กับ entire distribution ไม่ใช่ point forecast.
- **การใช้งาน:** compare probabilistic forecasting models.
- **ข้อควรระวัง:** พูดว่า CRPSยิ่งมากยิ่งดี.

## Related Notes

- [[Probabilistic Forecasting]]
- [[Quantile Forecast and Quantile Score]]
- [[Prediction Intervals]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[02-probabilistic-forecast]] | Continuous Ranked Probability Score section; also Topic 13 probabilistic lecture | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `02-probabilistic-forecast.pdf` — Continuous Ranked Probability Score section; also Topic 13 probabilistic lecture

## External References

- [Gneiting, T. & Raftery, A.E. (2007), Strictly Proper Scoring Rules, Prediction, and Estimation, JASA 102(477), 359–378.](https://doi.org/10.1198/016214506000001437)
- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
