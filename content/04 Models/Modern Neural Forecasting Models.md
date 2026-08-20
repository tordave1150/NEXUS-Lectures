---
title: "Modern Neural Forecasting Models"
aliases:
  - DeepAR
  - Temporal Fusion Transformer
  - TFT
  - N-HiTS
topic_number: 43
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

# Modern Neural Forecasting Models

> [!abstract] Summary
> Modern neural forecastingมีหลาย family: DeepARใช้ autoregressive RNNเพื่อ probabilistic global forecasting, TFTผสม recurrent processingกับ attention/gatingเพื่อ multi-horizon covariates, N-HiTSใช้ MLP-based hierarchical interpolationสำหรับ long-horizon forecasting.

## Why this concept matters

ไม่มี architectureเดียวดีที่สุดทุกกรณี; data scale, covariates, horizon, probabilistic objective และ computeเป็นตัวกำหนด.

## Core Idea

- Global modelsเรียนจากหลาย related time seriesร่วมกัน.
- DeepAR outputเป็น predictive distributionและ autoregressive sampling.
- TFTรองรับ static, known-future และ observed covariatesพร้อม interpretability components.
- N-HiTSใช้ hierarchical/multi-rate decompositionโดยไม่ใช่ Transformer.
- Classical baselinesยังจำเป็น.

## Mathematical Formulation / Technical Detail

แนวคิด global probabilistic model:

$$
p(y_{T+1:T+H}\mid y_{1:T},x)
=
\prod_{h=1}^{H}
p(y_{T+h}\mid y_{1:T+h-1},x).
$$

Architectureกำหนดวิธี parameterize conditional distributions/functions.

## Worked / Practical Example

Retail chainที่มีหลายพัน SKU-seriesอาจใช้ global modelเพื่อ share statistical strength. Known future promotionและcalendarสามารถเป็น covariates; output quantiles/distributionsนำไป inventory decisions.

## Assumptions and Interpretation

- Train/validation splitต้อง temporalและมักควรแบ่งระดับ seriesอย่างระวัง.
- Neural benchmark claimsจาก papersไม่รับประกัน performanceบน datasetใหม่.

## When to use

- large panels of related series.
- multi-horizon + rich covariates.
- probabilistic forecasting at scale.

## When not to use / Limitations

- single short series.
- compute/latency constraints.
- ไม่มี baselineหรือ monitoring.

## Common Mistakes

- เรียก N-HiTSว่า Transformer.
- เลือก architectureจาก leaderboardโดยไม่ reproduce.
- ใช้ future covariateที่จริงไม่ known ณ forecast time.

## Quick Review

- **Concept:** Modern neural forecastingมีหลาย family: DeepARใช้ autoregressive RNNเพื่อ probabilistic global forecasting, TFTผสม recurrent processingกับ attention/gatingเพื่อ multi-horizon covariates, N-HiTSใช้ MLP-based hierarchical interpolationสำหรับ long-horizon forecasting.
- **สิ่งที่ต้องจำ:** Global modelsเรียนจากหลาย related time seriesร่วมกัน.
- **การใช้งาน:** large panels of related series.
- **ข้อควรระวัง:** เรียก N-HiTSว่า Transformer.

## Related Notes

- [[NNAR]]
- [[Probabilistic Forecasting]]
- [[ML Time-Series Feature Engineering]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[12-NN_260718_091137]] | Modern neural network architectures section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `12-NN_260718_091137.pdf` — Modern neural network architectures section

## External References

- [Salinas, D., Flunkert, V., Gasthaus, J. & Januschowski, T. (2020), DeepAR: Probabilistic forecasting with autoregressive recurrent networks, International Journal of Forecasting 36(3), 1181–1191.](https://doi.org/10.1016/j.ijforecast.2019.07.001)
- [Lim, B., Arik, S.O., Loeff, N. & Pfister, T. (2021), Temporal Fusion Transformers for Interpretable Multi-horizon Time Series Forecasting.](https://arxiv.org/abs/1912.09363)
- [Challu, C. et al. (2023), N-HiTS: Neural Hierarchical Interpolation for Time Series Forecasting.](https://arxiv.org/abs/2201.12886)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
