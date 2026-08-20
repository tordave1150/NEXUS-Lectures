---
title: "Likelihood MLE NLL"
aliases:
  - Likelihood
  - Maximum Likelihood Estimation
  - MLE
  - Negative Log Likelihood
  - NLL
topic_number: 45
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

# Likelihood MLE NLL

> [!abstract] Summary
> Likelihood มอง probability modelเป็นฟังก์ชันของ parametersเมื่อข้อมูลถูกสังเกตแล้ว; MLEเลือก parametersที่ maximize likelihood และ softwareมัก minimize Negative Log Likelihood (NLL).

## Why this concept matters

MLEเป็นแกนกลางของ probabilistic models, ARIMA/ETS distributions, logistic regression และ neural distributional forecasting.

## Core Idea

- Likelihoodไม่ใช่ probability distributionของ parameterเว้นแต่มี Bayesian prior/framework.
- Log-likelihoodเปลี่ยน productเป็น sumและ numerical stableกว่า.
- Min NLLเท่ากับ max likelihoodเพราะ log monotonic.
- Time-series likelihoodมักเป็น productของ conditional densities ไม่ใช่ iid productง่าย ๆ.

## Mathematical Formulation / Technical Detail

IID likelihood:

$$
L(\theta)=\prod_{i=1}^{n}f(y_i\mid\theta).
$$

Log-likelihood:

$$
\ell(\theta)=\sum_{i=1}^{n}\log f(y_i\mid\theta).
$$

MLE:

$$
\hat\theta=\arg\max_\theta \ell(\theta)
=\arg\min_\theta[-\ell(\theta)].
$$

## Worked / Practical Example

Bernoulli sample likelihoodคือ $\prod p^{y_i}(1-p)^{1-y_i}$ และ MLEของ $p$ คือ sample mean. Gaussian regressionภายใต้ constant varianceทำให้ maximizing likelihoodเชื่อมกับ minimizing SSE.

## Assumptions and Interpretation

- Model density/supportต้องเหมาะกับ target เช่น count vs continuous.
- Non-convex likelihoodอาจมี local optima; existence/identifiabilityต้องตรวจใน complex models.

## When to use

- fit probabilistic models.
- compare likelihood-based IC.
- train distributional neural networks.

## When not to use / Limitations

- NLL valuesข้าม datasets/parameterizationsไม่ควรเปรียบแบบไร้บริบท.
- MLEไม่ robustต่อ misspecified distributionเสมอ.

## Common Mistakes

- เรียก likelihoodว่า probabilityที่ parameterเป็นจริง.
- คูณ tiny probabilitiesตรง ๆจน underflowแทน log-likelihood.
- สมมติ independenceของ time-series observationsโดยไม่ conditionalize.

## Quick Review

- **Concept:** Likelihood มอง probability modelเป็นฟังก์ชันของ parametersเมื่อข้อมูลถูกสังเกตแล้ว; MLEเลือก parametersที่ maximize likelihood และ softwareมัก minimize Negative Log Likelihood (NLL).
- **สิ่งที่ต้องจำ:** Likelihoodไม่ใช่ probability distributionของ parameterเว้นแต่มี Bayesian prior/framework.
- **การใช้งาน:** fit probabilistic models.
- **ข้อควรระวัง:** เรียก likelihoodว่า probabilityที่ parameterเป็นจริง.

## Related Notes

- [[AIC AICc BIC]]
- [[Probabilistic Forecasting]]
- [[Logistic Regression]]
- [[CRPS]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[13-probabilistic-forecast_260725_090945]] | Likelihood / MLE / NLL section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `13-probabilistic-forecast_260725_090945.pdf` — Likelihood / MLE / NLL section

## External References

- [Gneiting, T. & Raftery, A.E. (2007), Strictly Proper Scoring Rules, Prediction, and Estimation, JASA 102(477), 359–378.](https://doi.org/10.1198/016214506000001437)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
