---
title: "Ensemble Learning"
aliases:
  - Bagging
  - Boosting
  - Random Forest
  - Gradient Boosting
  - Stacking
topic_number: 59
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[S2-ML_260725_130143]]"
  - "[[DADS6003 Week 9-2 - Decision Trees]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Ensemble Learning

> [!abstract] Summary
> Ensemble Learning รวมหลาย modelsเพื่อให้ predictionแข็งแรงกว่า individual learner; Baggingฝึก modelsแบบ parallelบน resamplesเพื่อลด variance ส่วน Boostingสร้าง learnersต่อเนื่องเพื่อแก้ residual/errors.

## Why this concept matters

Treesมี varianceสูงจึงได้ประโยชน์จาก bagging/Random Forest; boostingสามารถสร้าง powerful nonlinear predictorsแต่ต้อง tuneอย่างระวัง.

## Core Idea

- Bagging average/voteหลาย base learners.
- Random Forestเพิ่ม random feature subsetsเพื่อลด correlationระหว่าง trees.
- Boosting fit sequential learnersเพื่อปรับ errors/gradients.
- Gradient Boosting/XGBoost-like methodsใช้ additive treesกับ loss gradients.
- Stackingเรียน meta-modelจาก out-of-fold predictions.

## Mathematical Formulation / Technical Detail

Regression ensemble average:

$$
\hat y(x)=\frac1B\sum_{b=1}^{B}\hat f_b(x).
$$

Boosting additive model:

$$
F_M(x)=F_0(x)+\sum_{m=1}^{M}\nu f_m(x),
$$

โดย $\nu$ คือ learning rate.

## Worked / Practical Example

Forecasting with engineered lags: Random Forestอาจ capture nonlinear interactionsโดยไม่ต้องกำหนด polynomialเอง; gradient boostingอาจแม่นขึ้นแต่ต้อง tune depth, learning rate, roundsด้วย rolling CV.

## Assumptions and Interpretation

- สำหรับ time series ต้องสร้าง out-of-fold/validation predictionsแบบ chronological.
- Ensemble diversityสำคัญ; modelsเหมือนกันมากให้ benefitน้อย.

## When to use

- tabular nonlinear prediction.
- feature-rich time-series ML.
- classification/regression benchmarks.

## When not to use / Limitations

- small data + aggressive boostingเสี่ยง overfit.
- stackingที่ meta-modelเห็น in-sample base predictionsเกิด leakage.

## Common Mistakes

- ใช้ random CVกับ time-series features.
- คิดว่า boosting=bagging.
- สร้าง stacking featuresจาก training predictionsที่ไม่ได้ out-of-fold.

## Quick Review

- **Concept:** Ensemble Learning รวมหลาย modelsเพื่อให้ predictionแข็งแรงกว่า individual learner; Baggingฝึก modelsแบบ parallelบน resamplesเพื่อลด variance ส่วน Boostingสร้าง learnersต่อเนื่องเพื่อแก้ residual/errors.
- **สิ่งที่ต้องจำ:** Bagging average/voteหลาย base learners.
- **การใช้งาน:** tabular nonlinear prediction.
- **ข้อควรระวัง:** ใช้ random CVกับ time-series features.

## Related Notes

- [[ML Time-Series Feature Engineering]]
- [[KNN and SVM]]
- [[Classification Metrics]]
- [[Regularized Regression]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[S2-ML_260725_130143]] | Ensemble: Bagging & Boosting section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `S2-ML_260725_130143.pdf` — Ensemble: Bagging & Boosting section

## External References

- [scikit-learn User Guide — Ensemble methods.](https://scikit-learn.org/stable/modules/ensemble.html)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น

## DADS6003 Enrichment — Tree Ensembles

DADS6003 เชื่อม Decision Tree กับสอง ensemble families:

- **Bagging**: train learners บน bootstrap samples แบบขนาน แล้ว aggregate เพื่อช่วยลด variance; [[Bagging and Random Forest]] เพิ่ม random feature selection ใน Random Forest.
- **Boosting**: train learners แบบลำดับ โดย learner ถัดไปมุ่งแก้ข้อผิดพลาดของ ensemble; ดู [[Boosting and AdaBoost]].

> [!note]
> Bagging/Boosting เป็น ensemble strategies ไม่ใช่ pruning algorithms แม้ทั้งหมดใช้เพื่อลดปัญหาการ generalize ของต้นไม้ได้ในคนละวิธี.

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 9-2 - Decision Trees]] | Slides 21–24 | overfitting, bagging, random forest and boosting |
