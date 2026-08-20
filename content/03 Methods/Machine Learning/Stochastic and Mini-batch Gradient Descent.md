---
title: "Stochastic and Mini-batch Gradient Descent"
aliases:
  - SGD
  - Mini-batch GD
topic_number: 69
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
  - sgd
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Stochastic and Mini-batch Gradient Descent

> [!abstract] Summary
> SGD estimate gradient จากหนึ่ง observation ต่อ update; mini-batch ใช้กลุ่มย่อยและเป็น default practical pattern ใน deep learning เพราะ trade-off ระหว่าง compute efficiency กับ gradient noise.

## Why this concept matters

ช่วย scale training ไปยัง datasets ใหญ่ และ stochastic noise บางครั้งช่วย optimization/generalization.

## Core Idea

- Batch GD: gradient จาก n samples.
- SGD: gradient estimate จาก 1 sample.
- Mini-batch: gradient estimate จาก b samples โดย \(1<b<n\).
- ควร shuffle training examples สำหรับ iid training เมื่อ assumptions อนุญาต และใช้ learning-rate schedule.

## Mathematical Formulation / Technical Detail

\[
\theta_{t+1}=\theta_t-\eta_t g_t,
\qquad E[g_t\mid\theta_t]\approx\nabla J(\theta_t).
\]

Mini-batch:
\[
g_t=\frac1{|B_t|}\sum_{i\in B_t}\nabla_\theta L_i(\theta_t).
\]

## Worked / Practical Example

Batch size 64 ไม่ได้มีความหมายเชิงทฤษฎีตายตัว; เลือกจาก memory, throughput, gradient noise และ validation behavior. ขนาดใหญ่ขึ้นมักให้ gradient เสถียรกว่าแต่ updates ต่อ epoch น้อยลง.

## When to use

- large datasets.
- neural network training.
- online/streaming variants เมื่อ algorithm รองรับ.

## Limitations / Assumptions

- SGD trajectory noisy และ sensitive ต่อ schedule.
- Sequential/time-series data ห้าม shuffle โดยไม่คิด temporal semantics.
- Feature scaling ยังสำคัญ.

## Common Mistakes

- พูดว่า SGD 'converges faster' เสมอโดยไม่ระบุ wall-clock/iterations/tolerance.
- ใช้ validation/test observations ใน mini-batch.

## Cross-check / Corrections

- ไม่พบ correction สำคัญ; เพิ่มเฉพาะ context และ implementation caveats.

## Quick Review

- **Concept:** SGD estimate gradient จากหนึ่ง observation ต่อ update; mini-batch ใช้กลุ่มย่อยและเป็น default practical pattern ใน deep learning เพราะ trade-off ระหว่าง compute efficiency กับ gradient noise.
- **จำให้ได้:** Batch GD: gradient จาก n samples.
- **ใช้งาน:** large datasets.
- **ระวัง:** พูดว่า SGD 'converges faster' เสมอโดยไม่ระบุ wall-clock/iterations/tolerance.

## Related Notes

- [[Gradient Descent]]
- [[Learning Rate and Scheduling]]
- [[Feature Scaling]]
- [[Backpropagation]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 3 - Multiple Linear Regression]] | Slides 7–9 | BGD/SGD/mini-batch comparison |
| [[DADS6003 Week 6 - Regularization]] | Slides 24–26 | SGD-style regularized updates |

## External References

- scikit-learn SGD models: https://scikit-learn.org/stable/modules/sgd.html
- Stanford CS229: https://cs229.stanford.edu/syllabus-summer2019.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
