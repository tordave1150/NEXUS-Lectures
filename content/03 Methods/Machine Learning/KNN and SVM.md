---
title: "KNN and SVM"
aliases:
  - KNN vs SVM
  - K-Nearest Neighbors and Support Vector Machine
topic_number: 57
type: comparison
status: legacy-bridge
domain:
  - Data Science
  - Machine Learning
language: th
sources:
  - "[[S2-ML_260725_130143]]"
  - "[[DADS6003 Week 9 - K-Nearest Neighbors]]"
tags:
  - data-science
  - comparison
created: 2026-08-08
updated: 2026-08-08
---

# KNN and SVM

> [!abstract] Canonical split
> Note เดิมนี้ถูกเก็บไว้เพื่อ backward compatibility ของ Topic 57 แต่เพื่อหลัก **One Concept = One Canonical Note** เนื้อหาเต็มถูกแยกเป็น [[K-Nearest Neighbors]] และ [[Support Vector Machine]].

## Comparison

| Dimension | K-Nearest Neighbors | Support Vector Machine |
|---|---|---|
| Learning style | instance-based / lazy | margin-based optimization |
| Main hyperparameters | $k$, distance, weights | $C$, kernel, $\gamma$ |
| Scaling sensitivity | สูง | สูง โดยเฉพาะ RBF/poly kernels |
| Prediction cost | สูงขึ้นตาม stored data/index | depends on support vectors |
| Nonlinearity | local geometry | kernels or nonlinear features |
| Probability output | vote/proportion; calibration may be needed | decision score by default; probability needs calibration/model option |

## Navigate

- [[K-Nearest Neighbors]] — Topic 77
- [[Support Vector Machine]] — Topic 78
- [[Feature Scaling]]
- [[Cross Validation]]
- [[Classification Metrics]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[S2-ML_260725_130143]] | selected ML topics | original combined KNN/SVM coverage |
| [[DADS6003 Week 9 - K-Nearest Neighbors]] | Slides 2–12 | expanded KNN coverage |

## Quick Review

- KNN = local instance-based learner; main choices are $k$, distance and weighting.
- SVM = maximum-margin learner; main choices include $C$, kernel and kernel parameters.
- ทั้งสอง sensitive ต่อ feature scale และควร tune ภายใน validation/CV pipeline.
- Detailed canonical notes: [[K-Nearest Neighbors]] และ [[Support Vector Machine]].

## Related Notes

- [[K-Nearest Neighbors]]
- [[Support Vector Machine]]
- [[Feature Scaling]]
- [[Cross Validation]]
- [[Classification Metrics]]
