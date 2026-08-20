---
title: "Supervised Learning"
aliases:
  - Supervised ML
topic_number: 61
domain:
  - Data Science
  - Machine Learning
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - supervised-learning
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Supervised Learning

> [!abstract] Summary
> Supervised Learning เรียน mapping จาก feature \(X\) ไปยัง target \(Y\) โดยใช้ labeled examples; target แบบ continuous ให้ regression และ target แบบ discrete classes ให้ classification.

## Why this concept matters

เป็นกรอบของ Linear/Logistic Regression, k-NN, SVM, Decision Trees และ Neural Networks จำนวนมาก และกำหนดวิธี split data, tune model และวัด out-of-sample performance.

## Core Idea

- Dataset มี pairs \((x_i,y_i)\).
- Regression: \(y\in\mathbb R\) หรือ continuous target; Classification: \(y\) เป็น class label.
- Loss function ต้องสัมพันธ์กับ task เช่น squared loss, log loss, hinge loss.
- Validation/test data ต้องไม่ไหลเข้า preprocessing หรือ training.

## Mathematical Formulation / Technical Detail

\[
D=\{(x_i,y_i)\}_{i=1}^{n},\qquad
\hat f=\arg\min_{f\in\mathcal F}\frac1n\sum_i L(y_i,f(x_i)).
\]

สำหรับ probabilistic classification อาจเรียน \(P(Y=k\mid X=x)\) แล้วแปลง probability เป็น decision ตาม threshold/cost.

## Worked / Practical Example

Churn: \(x\)=tenure, usage, complaints; \(y\)=churn/no churn. Model อาจทำนาย churn probability แล้ว business เลือก threshold ตาม cost ของ retention campaign.

## When to use

- เมื่อมี labeled historical outcomes.
- Regression, classification, ranking และ probability estimation ที่มี target ชัดเจน.

## Limitations / Assumptions

- Label noise และ selection bias ทำให้ model เรียนสิ่งผิด.
- Distribution shift ทำให้ test performance ในอดีตไม่รับประกัน production performance.
- Correlation จาก supervised model ไม่เท่ากับ causality.

## Common Mistakes

- fit preprocessing บน full dataset.
- ใช้ test set tune hyperparameter.
- เลือก metric ไม่สัมพันธ์กับ objective.

## Cross-check / Corrections

- ไม่พบ correction สำคัญ; เพิ่มเฉพาะ context และ implementation caveats.

## Quick Review

- **Concept:** Supervised Learning เรียน mapping จาก feature \(X\) ไปยัง target \(Y\) โดยใช้ labeled examples; target แบบ continuous ให้ regression และ target แบบ discrete classes ให้ classification.
- **จำให้ได้:** Dataset มี pairs \((x_i,y_i)\).
- **ใช้งาน:** เมื่อมี labeled historical outcomes.
- **ระวัง:** fit preprocessing บน full dataset.

## Related Notes

- [[Machine Learning Fundamentals]]
- [[Train Validation Test Split]]
- [[Cross Validation]]
- [[Bias Variance Tradeoff]]
- [[Classification Metrics]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 1 - Introduction]] | Slides 8–9 | supervised-learning definition |

## External References

- scikit-learn Model Selection: https://scikit-learn.org/stable/model_selection.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
