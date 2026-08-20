---
title: "Quantile Forecast and Quantile Score"
aliases:
  - Quantile Forecast
  - Pinball Loss
  - Quantile Score
topic_number: 47
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

# Quantile Forecast and Quantile Score

> [!abstract] Summary
> Quantile forecast $q_p$ ระบุระดับที่ future outcomeมี probability $p$ ที่จะต่ำกว่าหรือเท่ากับมัน; quantile score/pinball lossเป็น proper objectiveสำหรับประเมิน quantileนั้น.

## Why this concept matters

Quantilesเชื่อม forecastingกับ service levelsและ asymmetric costs; high quantileลงโทษ under-forecastมากกว่า over-forecast.

## Core Idea

- Medianคือ $p=0.5$ quantile.
- Quantile scoreยิ่งต่ำยิ่งดี.
- Lecture/FPPใช้ versionคูณ 2 ซึ่งทำให้ที่ p=0.5 เท่ากับ absolute error.
- Conventional pinball lossบาง libraryไม่คูณ 2; rankingไม่เปลี่ยนแต่ scaleเปลี่ยน.

## Mathematical Formulation / Technical Detail

FPP convention:

$$
Q_{p,t}=
\begin{cases}
2(1-p)(f_{p,t}-y_t),&y_t<f_{p,t}\\
2p(y_t-f_{p,t}),&y_t\ge f_{p,t}.
\end{cases}
$$

Expected quantile lossถูก minimizeเมื่อ $f_p$ เป็น true $p$-quantile.

## Worked / Practical Example

ที่ $p=0.8$ under-forecast ($y>f_p$) ถูก weight $2(0.8)=1.6$ ขณะที่ over-forecastถูก weight $2(0.2)=0.4$. จึงเหมาะเมื่อ shortage costสูงกว่า excess.

## Assumptions and Interpretation

- Quantile coverageควรตรวจร่วมกับ score.
- Service-level mappingต้องตรง definition เช่น Type-1 service levelกับ demand quantile.

## When to use

- inventory/service-level planning.
- probabilistic model evaluation.
- quantile regression training.

## When not to use / Limitations

- ไม่ใช้ quantile score p=0.95เพื่อประเมิน median objective.
- single quantileไม่บอก full distribution.

## Common Mistakes

- คิดว่า scoreยิ่งมากยิ่งดี.
- ไม่ระบุ conventionคูณ 2.
- ใช้ actual future informationสร้าง quantileแล้วประเมินตนเอง.

## Quick Review

- **Concept:** Quantile forecast $q_p$ ระบุระดับที่ future outcomeมี probability $p$ ที่จะต่ำกว่าหรือเท่ากับมัน; quantile score/pinball lossเป็น proper objectiveสำหรับประเมิน quantileนั้น.
- **สิ่งที่ต้องจำ:** Medianคือ $p=0.5$ quantile.
- **การใช้งาน:** inventory/service-level planning.
- **ข้อควรระวัง:** คิดว่า scoreยิ่งมากยิ่งดี.

## Related Notes

- [[Probabilistic Forecasting]]
- [[CRPS]]
- [[Quantile Regression]]
- [[VaR and CVaR]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[02-probabilistic-forecast]] | Evaluating probabilistic forecasts / quantile score | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `02-probabilistic-forecast.pdf` — Evaluating probabilistic forecasts / quantile score

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)
- [Gneiting, T. & Raftery, A.E. (2007), Strictly Proper Scoring Rules, Prediction, and Estimation, JASA 102(477), 359–378.](https://doi.org/10.1198/016214506000001437)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
