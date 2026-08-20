---
title: "Boosting and AdaBoost"
aliases:
  - Boosting
  - AdaBoost
topic_number: 84
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
  - boosting
  - adaboost
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Boosting and AdaBoost

> [!abstract] Summary
> Boosting สร้าง weak learners แบบ sequential โดยแต่ละ stage เน้นแก้ error ของ ensemble ปัจจุบัน; AdaBoost ปรับ sample weights ให้ observations ที่ classify ผิดมีอิทธิพลมากขึ้น.

## Why this concept matters

ต่างจาก bagging ที่ parallel/variance reduction เป็นหลัก; boosting สามารถลด bias และสร้าง strong predictor จาก weak learners.

## Core Idea

- Sequential learners; later learners depend on previous errors.
- AdaBoost classifier reweights difficult observations.
- Modern boosting families เช่น Gradient Boosting/XGBoost ใช้แนวคิด stage-wise optimization แต่ algorithm ต่างจาก AdaBoost.

## Mathematical Formulation / Technical Detail

Binary AdaBoost learner weight:

\[
\alpha_m=\frac12\log\frac{1-\epsilon_m}{\epsilon_m},
\]

แล้ว update sample weightsประมาณ
\[
w_i\leftarrow w_i\exp(-\alpha_m y_i h_m(x_i)).
\]

## Worked / Practical Example

Decision stump ที่เก่งกว่าสุ่มเล็กน้อยหลายตัวสามารถรวมเป็น nonlinear classifier ที่แข็งแรง โดยแต่ละรอบ focus observations ที่ ensemble ก่อนหน้าทำผิด.

## When to use

- tabular classification/regression.
- เมื่อ shallow trees เป็น weak learners.

## Limitations / Assumptions

- Sensitive ต่อ noisy labels/outliers ในบาง boosting variants.
- ต้อง tune learning rate, depth, estimators.
- Boosting ไม่เท่ากับ Random Forest.

## Common Mistakes

- อธิบาย Boosting ว่า 'ต้นถัดไปแก้ต้นก่อน' แบบ literal ทุก algorithm; จริงคือ optimize ensemble residual/error ตาม formulation.
- ใช้ test set เลือก number of estimators.

## Cross-check / Corrections

- ไม่พบ correction สำคัญ; เพิ่มเฉพาะ context และ implementation caveats.

## Quick Review

- **Concept:** Boosting สร้าง weak learners แบบ sequential โดยแต่ละ stage เน้นแก้ error ของ ensemble ปัจจุบัน; AdaBoost ปรับ sample weights ให้ observations ที่ classify ผิดมีอิทธิพลมากขึ้น.
- **จำให้ได้:** Sequential learners; later learners depend on previous errors.
- **ใช้งาน:** tabular classification/regression.
- **ระวัง:** อธิบาย Boosting ว่า 'ต้นถัดไปแก้ต้นก่อน' แบบ literal ทุก algorithm; จริงคือ optimize ensemble residual/error ตาม formulation.

## Related Notes

- [[Ensemble Learning]]
- [[Bagging and Random Forest]]
- [[Decision Trees]]
- [[Bias Variance Tradeoff]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 9-2 - Decision Trees]] | Slides 21 and 24 | boosting/AdaBoost overview |

## External References

- scikit-learn Ensemble Methods: https://scikit-learn.org/stable/modules/ensemble.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
