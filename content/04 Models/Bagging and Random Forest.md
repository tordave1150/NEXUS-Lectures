---
title: "Bagging and Random Forest"
aliases:
  - Bagging
  - Bootstrap Aggregating
  - Random Forest
topic_number: 83
domain:
  - Data Science
  - Machine Learning
  - Ensemble Learning
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - ensemble
  - random-forest
  - bagging
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Bagging and Random Forest

> [!abstract] Summary
> Bagging train base learners หลายตัวบน bootstrap samples แล้ว aggregate predictions เพื่อลด variance; Random Forest เพิ่ม random feature subsampling ระหว่าง tree construction เพื่อ decorrelate trees.

## Why this concept matters

Decision trees มี variance สูง; averaging trees ที่ error ไม่ perfectly correlated สามารถ improve generalization ได้มาก.

## Core Idea

- Bootstrap sample: sample n rows with replacement.
- Classification aggregate ด้วย vote/probability average; regressionใช้ mean.
- Random Forest = bagged trees + random subset of candidate features at splits.
- Out-of-bag samples สามารถใช้ estimate performance/feature diagnostics บางชนิด.

## Mathematical Formulation / Technical Detail

ถ้า estimators มี variance \(\sigma^2\) และ pairwise correlation \(\rho\), variance ของ average โดยประมาณ:

\[
Var(\bar f)\approx \rho\sigma^2+\frac{1-\rho}{M}\sigma^2.
\]

เพิ่ม M ลดส่วน second term; random feature selection ช่วยลด \(\rho\).

## Worked / Practical Example

Single tree sensitive ต่อ small data changes. Train 500 randomized trees แล้ว average ทำ boundary เสถียรขึ้นและมักลด test error.

## When to use

- tabular nonlinear prediction.
- high-variance tree baselines.

## Limitations / Assumptions

- Interpretability ต่ำกว่า single tree.
- มาก trees เพิ่ม compute/memory.
- Feature importance แบบ impurity มี biases.

## Common Mistakes

- คิดว่า Random Forest = pruning.
- ใช้ bootstrap + identical highly correlated trees แล้วคาด variance ลดเต็มที่.

## Cross-check / Corrections

- ไม่พบ correction สำคัญ; เพิ่มเฉพาะ context และ implementation caveats.

## Quick Review

- **Concept:** Bagging train base learners หลายตัวบน bootstrap samples แล้ว aggregate predictions เพื่อลด variance; Random Forest เพิ่ม random feature subsampling ระหว่าง tree construction เพื่อ decorrelate trees.
- **จำให้ได้:** Bootstrap sample: sample n rows with replacement.
- **ใช้งาน:** tabular nonlinear prediction.
- **ระวัง:** คิดว่า Random Forest = pruning.

## Related Notes

- [[Decision Trees]]
- [[Ensemble Learning]]
- [[Boosting and AdaBoost]]
- [[Bias Variance Tradeoff]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 9-2 - Decision Trees]] | Slides 21–23 | bagging algorithm and Random Forest intuition |

## External References

- scikit-learn Ensemble Methods: https://scikit-learn.org/stable/modules/ensemble.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
