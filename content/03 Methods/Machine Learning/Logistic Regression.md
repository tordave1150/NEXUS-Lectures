---
title: "Logistic Regression"
aliases:
  - Logit Regression
  - Binary Logistic Regression
topic_number: 56
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[S2-ML_260725_130143]]"
  - "[[DADS6003 Week 5 - Logistic Regression]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Logistic Regression

> [!abstract] Summary
> Logistic Regression model log-oddsของ binary outcomeเป็น linear functionของ featuresและแปลงกลับเป็น probabilityผ่าน logistic function.

## Why this concept matters

เหมาะกับ probability predictionที่ต้อง interpret coefficients/odds ratios และใช้เป็น strong classification baseline.

## Core Idea

- $p=P(Y=1|x)$ อยู่ใน [0,1].
- Coefficient $\beta_j$ เพิ่ม log-oddsต่อหนึ่งหน่วย x; $e^{\beta_j}$ คือ odds ratio conditional on other variables.
- Decision thresholdแยกจาก probability model.
- Regularized logistic regressionเป็น defaultในหลาย ML libraries.

## Mathematical Formulation / Technical Detail

Logit model:

$$
\log\frac{p}{1-p}=\beta_0+x^\top\beta.
$$

$$
p=\frac{1}{1+\exp[-(\beta_0+x^\top\beta)]}.
$$

Odds ratio for one-unit increase:

$$
OR=e^{\beta_j}.
$$

## Worked / Practical Example

ถ้า holiday dummy coefficient $\beta=\log(3.45)$ oddsของ late deliveryระหว่าง holidayเป็นประมาณ 3.45 เท่าของ baselineเมื่อ featuresอื่นคงที่. Odds ratio 3.45 ไม่ได้แปล probabilityเพิ่ม 3.45 เท่า.

## Assumptions and Interpretation

- Observations conditional independence/likelihood specificationต้องเหมาะ; clustered/time dataอาจต้อง extensions.
- Probability calibrationควรตรวจแยกจาก discrimination.

## When to use

- binary classification.
- interpretable probability model.
- baselineก่อน SVM/boosting.

## When not to use / Limitations

- strong nonlinear boundaryโดยไม่มี features/kernel.
- rare eventsอาจต้อง class weights/sampling/calibrationอย่างระวัง.

## Common Mistakes

- สับสน odds ratioกับ risk ratio.
- ใช้ 0.5 thresholdทุก business cost.
- ตีความ coefficientเป็น causalโดยอัตโนมัติ.

## Quick Review

- **Concept:** Logistic Regression model log-oddsของ binary outcomeเป็น linear functionของ featuresและแปลงกลับเป็น probabilityผ่าน logistic function.
- **สิ่งที่ต้องจำ:** $p=P(Y=1|x)$ อยู่ใน [0,1].
- **การใช้งาน:** binary classification.
- **ข้อควรระวัง:** สับสน odds ratioกับ risk ratio.

## Related Notes

- [[Classification Metrics]]
- [[KNN and SVM]]
- [[Likelihood MLE NLL]]
- [[Regularized Regression]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[S2-ML_260725_130143]] | Logistic regression / odds ratio section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `S2-ML_260725_130143.pdf` — Logistic regression / odds ratio section

## External References

- [scikit-learn User Guide — Linear Models (Ridge, Lasso, Elastic Net, Logistic Regression).](https://scikit-learn.org/stable/modules/linear_model.html)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น

## DADS6003 Enrichment — Sigmoid, NLL and Decision Threshold

จาก lecture DADS6003 Week 5 เราเชื่อม Logistic Regression กับ Maximum Likelihood ได้ชัดขึ้น: สำหรับ binary target, Bernoulli negative log-likelihood หรือ binary cross-entropy คือ objective มาตรฐาน

$$
J(\beta)=-\frac1n\sum_{i=1}^{n}\left[y_i\log p_i+(1-y_i)\log(1-p_i)\right],
\qquad p_i=\sigma(x_i^\top\beta).
$$

Gradient มีรูป

$$
\nabla_\beta J=\frac1nX^\top(p-y).
$$

> [!warning] Threshold is a decision rule
> ค่า `0.5` เป็น default ที่พบบ่อย แต่ไม่ใช่ threshold ที่ดีที่สุดเสมอ ต้องเลือกจาก business cost, class prevalence และ metric ที่สนใจ เช่น precision/recall หรือ expected cost.

### Additional Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 5 - Logistic Regression]] | Slides 2–15 | sigmoid, decision boundary, Bernoulli NLL, gradient, odds/logit |
