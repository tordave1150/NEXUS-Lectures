---
title: "Support Vector Machine"
aliases:
  - SVM
  - Support Vector Classifier
topic_number: 78
domain:
  - Data Science
  - Machine Learning
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - svm
  - classification
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Support Vector Machine

> [!abstract] Summary
> Support Vector Machine หา separating hyperplane ที่ maximize margin; kernel trick ขยายไป nonlinear boundaries โดยคำนวณ similarities ใน implicit feature space.

## Why this concept matters

เป็น strong supervised baseline สำหรับ medium-sized, high-dimensional data และช่วยเข้าใจ margin, regularization และ kernels.

## Core Idea

- Hard-margin ใช้ได้เมื่อ linearly separable; soft-margin ใช้ penalty C ยอม violations.
- Support vectors คือ observations ที่กำหนด boundary/margin.
- Kernel เช่น RBF ทำ nonlinear decision surface.
- Scaling สำคัญมากเพราะ distance/dot-product geometry และ regularization.

## Mathematical Formulation / Technical Detail

Linear soft-margin primal:

\[
\min_{w,b,\xi}\frac12\|w\|^2+C\sum_i\xi_i
\]

subject to
\[
y_i(w^\top x_i+b)\ge 1-\xi_i,\quad \xi_i\ge0.
\]

RBF kernel:
\[
K(x,z)=\exp(-\gamma\|x-z\|^2).
\]

## Worked / Practical Example

C ใหญ่ penalize training errors แรงและอาจ boundary complex ขึ้น; gamma ใหญ่ใน RBF ทำ influence local ขึ้น. ทั้งสองต้อง tune ด้วย CV ภายใน training set.

## When to use

- classification/regression ที่ n ไม่ใหญ่มาก.
- high-dimensional sparse/text problems (linear SVM).

## Limitations / Assumptions

- Kernel SVM scale ไม่ดีเมื่อ n ใหญ่มาก.
- Probability outputs ต้อง calibration เพิ่มในบาง implementations.
- Hyperparameters C/gamma sensitive.

## Common Mistakes

- ไม่ scale features.
- เลือก C/gamma จาก test set.
- ตีความ support vectors ว่า 'important cases' ใน causal sense.

## Cross-check / Corrections

- ไม่พบ correction สำคัญ; เพิ่มเฉพาะ context และ implementation caveats.

## Quick Review

- **Concept:** Support Vector Machine หา separating hyperplane ที่ maximize margin; kernel trick ขยายไป nonlinear boundaries โดยคำนวณ similarities ใน implicit feature space.
- **จำให้ได้:** Hard-margin ใช้ได้เมื่อ linearly separable; soft-margin ใช้ penalty C ยอม violations.
- **ใช้งาน:** classification/regression ที่ n ไม่ใหญ่มาก.
- **ระวัง:** ไม่ scale features.

## Related Notes

- [[K-Nearest Neighbors]]
- [[Feature Scaling]]
- [[Cross Validation]]
- [[Logistic Regression]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[S2-ML_260725_130143]] | SVM section | existing source from previous forecasting/ML lecture set |

## External References

- scikit-learn SVM: https://scikit-learn.org/stable/modules/svm.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
