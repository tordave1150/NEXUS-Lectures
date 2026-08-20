---
title: "Feature Scaling"
aliases:
  - Standardization
  - Normalization
  - Z-score Scaling
  - Min-Max Scaling
topic_number: 71
domain:
  - Data Science
  - Machine Learning
  - Preprocessing
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - preprocessing
  - scaling
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Feature Scaling

> [!abstract] Summary
> Feature Scaling ทำ predictors ให้อยู่ใน comparable numerical scales; สำคัญมากกับ distance-based, gradient-based และ regularized methods.

## Why this concept matters

ถ้า feature หน่วยต่างกันมาก distance, penalty และ optimization geometry อาจถูกครอบงำด้วย feature ที่ตัวเลขใหญ่ แม้ไม่ได้สำคัญเชิง predictive มากกว่า.

## Core Idea

- Standardization: subtract training mean และ divide training SD.
- Min-max scaling: map training range ไปช่วงที่กำหนด เช่น [0,1].
- fit scaler **เฉพาะ training data** แล้ว transform validation/test ด้วย parameters เดิม.
- Decision trees โดยทั่วไปไม่ต้อง scaling สำหรับ axis-aligned splits แต่ pipelines อื่นอาจต้อง.

## Mathematical Formulation / Technical Detail

\[
z=\frac{x-\mu_{\text{train}}}{\sigma_{\text{train}}}.
\]

Standardization ทำให้ training feature มี mean ใกล้ 0 และ variance ใกล้ 1 แต่ **ไม่ bound range**.

Min-max:
\[
x'=\frac{x-x_{\min,\text{train}}}{x_{\max,\text{train}}-x_{\min,\text{train}}}.
\]

## Worked / Practical Example

Population = 120,000,000 และ Age = 60 ใน Euclidean k-NN: หากไม่ scale population จะ dominate distance. หลัง standardization contribution ขึ้นกับ standardized deviation แทน raw units.

## When to use

- k-NN, SVM, regularized regression, neural networks, gradient descent.
- features มี measurement scales ต่างกัน.

## Limitations / Assumptions

- Outliers กระทบ mean/SD และ min/max; อาจใช้ robust scaling.
- Scaling ไม่แก้ skewness/nonlinearity โดยอัตโนมัติ.

## Common Mistakes

- คิดว่า z-score maps ทุกค่าเข้า [-3,3].
- fit scaler ก่อน train/test split.
- standardize dummy variables โดยอัตโนมัติโดยไม่คิด model/interpretation.

## Cross-check / Corrections

- Lecture KNN slide ระบุ z-score maps to (-3,3); canonical correction: z-score has no fixed bounds and produces mean≈0, variance≈1 on fitted data.

## Quick Review

- **Concept:** Feature Scaling ทำ predictors ให้อยู่ใน comparable numerical scales; สำคัญมากกับ distance-based, gradient-based และ regularized methods.
- **จำให้ได้:** Standardization: subtract training mean และ divide training SD.
- **ใช้งาน:** k-NN, SVM, regularized regression, neural networks, gradient descent.
- **ระวัง:** คิดว่า z-score maps ทุกค่าเข้า [-3,3].

## Related Notes

- [[K-Nearest Neighbors]]
- [[Regularized Regression]]
- [[Gradient Descent]]
- [[Stochastic and Mini-batch Gradient Descent]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 3 - Multiple Linear Regression]] | Slide 6 | feature-scaling motivation |
| [[DADS6003 Week 9 - K-Nearest Neighbors]] | Slide 10 | distance-scale sensitivity |

## External References

- scikit-learn StandardScaler: https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
