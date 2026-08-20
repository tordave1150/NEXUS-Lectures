---
title: "Gradient Descent"
aliases:
  - Batch Gradient Descent
  - GD
topic_number: 68
domain:
  - Data Science
  - Machine Learning
  - Optimization
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - optimization
  - gradient-descent
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Gradient Descent

> [!abstract] Summary
> Gradient Descent (GD) ปรับ parameters ไปทิศตรงข้าม gradient ของ objective; Batch GD ใช้ training observations ทั้งหมดในการคำนวณ gradient ต่อ update.

## Why this concept matters

เป็น optimization primitive ของ linear/logistic regression และ neural networks และช่วยแยก 'model/loss' ออกจาก 'optimizer'.

## Core Idea

- Update: \(\theta_{t+1}=\theta_t-\eta\nabla J(\theta_t)\).
- Learning rate \(\eta\) ใหญ่เกินอาจ diverge/oscillate; เล็กเกินเรียนช้า.
- Feature scaling ช่วย conditioning และทำให้ gradient directions สมดุลขึ้น.
- Stopping criterion อาจอิง max iterations, gradient norm หรือ objective improvement.

## Mathematical Formulation / Technical Detail

สำหรับ MSE ถ้านิยาม

\[
J(\theta)=\frac{1}{2n}\sum_i(h_\theta(x_i)-y_i)^2,
\]

จะได้
\[
\nabla_\theta J=\frac1n X^\top(X\theta-y).
\]

ถ้านิยาม \(J=\frac1n\sum e_i^2\), gradient จะมี factor \(2\). ทั้งสอง convention ให้ optimum เดียวกันแต่ learning-rate scale ต่างกัน.

## Worked / Practical Example

Linear regression ที่มี predictors scale 1 และ 1,000,000 ทำให้ contour elongated; standardization ทำให้ GD ใช้ step size เดียวได้มีประสิทธิภาพขึ้น.

## When to use

- objective differentiable/มี gradient และ dataset พอ fit batch.
- ใช้ทำความเข้าใจ optimizer ก่อน SGD/Adam.

## Limitations / Assumptions

- Non-convex objective อาจมี saddle/local minima.
- Gradient computation full batch แพงเมื่อ n ใหญ่.
- Plateau/ill-conditioning ทำให้ convergence ช้า.

## Common Mistakes

- ลืม factor convention ของ MSE gradient.
- ใช้ learning rate เดียวโดยไม่ monitor convergence.
- ไม่ scale features ใน distance/gradient-sensitive models.

## Cross-check / Corrections

- Lecture ใช้ MSE \(1/N\) แต่ gradient formula ไม่มี factor 2; canonical note ใช้ \(1/(2N)\) convention เพื่อให้สูตรสอดคล้อง หรือระบุว่า factor 2 absorb เข้า learning rate ได้.

## Quick Review

- **Concept:** Gradient Descent (GD) ปรับ parameters ไปทิศตรงข้าม gradient ของ objective; Batch GD ใช้ training observations ทั้งหมดในการคำนวณ gradient ต่อ update.
- **จำให้ได้:** Update: \(\theta_{t+1}=\theta_t-\eta\nabla J(\theta_t)\).
- **ใช้งาน:** objective differentiable/มี gradient และ dataset พอ fit batch.
- **ระวัง:** ลืม factor convention ของ MSE gradient.

## Related Notes

- [[Feature Scaling]]
- [[Stochastic and Mini-batch Gradient Descent]]
- [[Learning Rate and Scheduling]]
- [[Backpropagation]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 2 - Simple Linear Regression]] | Slides 8–14 | batch GD intuition and updates |
| [[DADS6003 Week 3 - Multiple Linear Regression]] | Slides 4–5 | multi-feature batch GD |

## External References

- Stanford CS229 syllabus/notes: https://cs229.stanford.edu/syllabus-summer2019.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
