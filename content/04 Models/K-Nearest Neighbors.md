---
title: "K-Nearest Neighbors"
aliases:
  - KNN
  - k-NN
topic_number: 77
domain:
  - Data Science
  - Machine Learning
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - knn
  - classification
  - regression
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# K-Nearest Neighbors

> [!abstract] Summary
> k-NN เป็น instance-based non-parametric method: prediction ของ query ขึ้นกับ labels/targets ของ training points ที่อยู่ใกล้ที่สุดภายใต้ distance metric.

## Why this concept matters

เป็น baseline ที่เข้าใจง่ายและแสดงชัดว่าทำไม scaling, distance metric และ dimensionality สำคัญ.

## Core Idea

- Classification: majority/weighted vote ของ k neighbors.
- Regression: average/weighted average ของ neighbor targets.
- ไม่มี parametric training ขั้นหนัก แต่ prediction ต้องค้นหา neighbors.
- k เป็น hyperparameter: เล็ก → boundary flexible/high variance; ใหญ่ → smoother/high bias.

## Mathematical Formulation / Technical Detail

Euclidean distance:

\[
d(x,z)=\sqrt{\sum_{j=1}^{p}(x_j-z_j)^2}.
\]

Distance-weighted classification อาจใช้
\[
w_i \propto \frac{1}{d(x,x_i)+\epsilon}.
\]

## Worked / Practical Example

จาก sample S5=(2,5), คำนวณ distance ถึง S1–S4 แล้วเลือก k=3. Regression output = mean targets ของ neighbors; classification output = majority class. หาก features คนละ scale ต้อง standardize ก่อน.

## When to use

- small/medium data, nonlinear local patterns.
- baseline ที่ไม่มี strong parametric assumption.

## Limitations / Assumptions

- Prediction cost/memory สูงเมื่อ n ใหญ่.
- Curse of dimensionality ทำ distance less informative.
- Sensitive ต่อ scaling/noise/irrelevant features.

## Common Mistakes

- z-score = range [-3,3].
- ใช้ odd k แล้วคิดว่า tie impossible ทุก setting.
- ใช้ Euclidean distance กับ categorical features โดยไม่ encode/metric ที่เหมาะ.

## Cross-check / Corrections

- Corrected z-score range claim; odd-k tie avoidance is limited; ZIP compression removed as primary computational remedy.

## Quick Review

- **Concept:** k-NN เป็น instance-based non-parametric method: prediction ของ query ขึ้นกับ labels/targets ของ training points ที่อยู่ใกล้ที่สุดภายใต้ distance metric.
- **จำให้ได้:** Classification: majority/weighted vote ของ k neighbors.
- **ใช้งาน:** small/medium data, nonlinear local patterns.
- **ระวัง:** z-score = range [-3,3].

## Related Notes

- [[Feature Scaling]]
- [[Cross Validation]]
- [[Support Vector Machine]]
- [[KNN and SVM]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 9 - K-Nearest Neighbors]] | Slides 2–12 | algorithm, regression/classification, tuning, issues |

## External References

- scikit-learn Nearest Neighbors: https://scikit-learn.org/stable/modules/neighbors.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
