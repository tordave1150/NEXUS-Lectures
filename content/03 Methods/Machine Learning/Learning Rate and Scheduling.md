---
title: "Learning Rate and Scheduling"
aliases:
  - Learning Rate Schedule
  - LR Schedule
topic_number: 70
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
  - learning-rate
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Learning Rate and Scheduling

> [!abstract] Summary
> Learning rate กำหนดขนาด parameter update; scheduling ปรับ learning rate ตามเวลา/validation เพื่อให้ช่วงแรกเรียนเร็วและช่วงท้าย refine solution ได้เสถียรขึ้น.

## Why this concept matters

optimizer เดียวกันให้ผลต่างมากจาก learning rate; จึงเป็น hyperparameter สำคัญที่ต้อง monitor และ tune.

## Core Idea

- Constant learning rate ง่ายแต่เสี่ยง oscillation หรือ slow convergence.
- Decay schedules เช่น inverse-time, exponential, cosine เป็น choices ไม่ใช่ universal rule.
- Adaptive optimizers ปรับ effective step ต่อ parameter แต่ยังมี global/base learning rate.

## Mathematical Formulation / Technical Detail

ตัวอย่าง inverse-time schedule:

\[
\eta_t=\frac{\eta_0}{1+\lambda t}.
\]

อีกแบบ exponential:
\[
\eta_t=\eta_0\gamma^t.
\]

ค่าที่เหมาะขึ้นกับ objective geometry, batch size และ optimizer.

## Worked / Practical Example

ถ้า training loss oscillate และ validation ไม่ดี อาจลด learning rate; ถ้าลดเร็วเกิน model อาจหยุดก่อนถึง useful region. Learning-rate curves จึงควรอ่านคู่กับ train/validation loss.

## When to use

- gradient-based models.
- SGD/mini-batch/neural networks.

## Limitations / Assumptions

- Schedule ไม่แก้ model misspecification/data leakage.
- Learning rate interactions กับ normalization, batch size, optimizer.

## Common Mistakes

- ถือสูตร inverse-time จาก lecture เป็นมาตรฐานเดียว.
- tune learning rate บน test set.

## Cross-check / Corrections

- Lecture schedule เป็นหนึ่งตัวอย่าง; canonical note ระบุ alternatives และไม่ให้สถานะเป็น default universal schedule.

## Quick Review

- **Concept:** Learning rate กำหนดขนาด parameter update; scheduling ปรับ learning rate ตามเวลา/validation เพื่อให้ช่วงแรกเรียนเร็วและช่วงท้าย refine solution ได้เสถียรขึ้น.
- **จำให้ได้:** Constant learning rate ง่ายแต่เสี่ยง oscillation หรือ slow convergence.
- **ใช้งาน:** gradient-based models.
- **ระวัง:** ถือสูตร inverse-time จาก lecture เป็นมาตรฐานเดียว.

## Related Notes

- [[Gradient Descent]]
- [[Stochastic and Mini-batch Gradient Descent]]
- [[Backpropagation]]
- [[Cross Validation]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 3 - Multiple Linear Regression]] | Slide 8 | inverse-time decay example |

## External References

- scikit-learn SGD: https://scikit-learn.org/stable/modules/sgd.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
