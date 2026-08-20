---
title: "Backpropagation"
aliases:
  - Backprop
  - Reverse-mode Differentiation in Neural Networks
topic_number: 85
domain:
  - Data Science
  - Machine Learning
  - Neural Networks
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - neural-network
  - backpropagation
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Backpropagation

> [!abstract] Summary
> Backpropagation คำนวณ gradients ของ neural-network loss ต่อ weights อย่างมีประสิทธิภาพด้วย chain rule จาก output layer ย้อนสู่ hidden layers; optimizer เช่น SGD/Adam นำ gradients เหล่านี้ไป update weights.

## Why this concept matters

เป็นแกนของ neural network training และแยกชัดว่า backprop = gradient computation ส่วน gradient descent = parameter update rule.

## Core Idea

- Forward pass คำนวณ activations และ loss.
- Backward pass propagate error derivatives ย้อนผ่าน layers.
- Gradient ของ weight = upstream delta × input activation.
- Hidden delta ต้อง **sum contributions จาก downstream units** ใน network ทั่วไป.

## Mathematical Formulation / Technical Detail

ให้
\[
z^{(l+1)}=W^{(l)}a^{(l)}+b^{(l)},\quad a^{(l+1)}=f(z^{(l+1)}).
\]

Output delta สำหรับ sigmoid+BCE:
\[
\delta^{(L)}=a^{(L)}-y.
\]

Hidden layer:
\[
\delta^{(l)}=(W^{(l)})^\top\delta^{(l+1)}\odot f'(z^{(l)}).
\]

Gradient:
\[
\frac{\partial J}{\partial W^{(l)}}=\delta^{(l+1)}(a^{(l)})^\top.
\]

## Worked / Practical Example

ใน 2-hidden-unit → 1-output example, downstream node มีหนึ่งตัวจึง sum ดูเหมือนหายไป. เมื่อ layer ถัดไปมีหลาย nodes ต้องรวม weighted deltas จากทุก downstream connection.

## When to use

- training MLP/deep networks.
- เข้าใจ autodiff และ gradient flow.

## Limitations / Assumptions

- Vanishing/exploding gradients ขึ้นกับ depth/activation/initialization.
- Backprop ไม่ guarantee global optimum.
- Numerical stability สำคัญสำหรับ softmax/log-loss.

## Common Mistakes

- คิดว่า backprop กับ gradient descent เป็นคำเดียวกัน.
- ลืม summation downstream paths.
- คำนวณ derivatives จาก rounded probabilities.

## Cross-check / Corrections

- Lecture hidden-delta notation ไม่มี summation ใน general statement; canonical formula เพิ่ม matrix/summation form ที่ถูกต้องสำหรับ multiple downstream nodes.

## Quick Review

- **Concept:** Backpropagation คำนวณ gradients ของ neural-network loss ต่อ weights อย่างมีประสิทธิภาพด้วย chain rule จาก output layer ย้อนสู่ hidden layers; optimizer เช่น SGD/Adam นำ gradients เหล่านี้ไป update weights.
- **จำให้ได้:** Forward pass คำนวณ activations และ loss.
- **ใช้งาน:** training MLP/deep networks.
- **ระวัง:** คิดว่า backprop กับ gradient descent เป็นคำเดียวกัน.

## Related Notes

- [[Neural Networks Fundamentals]]
- [[Perceptron and Forward Propagation]]
- [[Activation Functions and Softmax]]
- [[Gradient Descent]]
- [[Stochastic and Mini-batch Gradient Descent]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 10 - Neural Network]] | Slides 8–16 | forward pass, BCE and backprop derivation |

## External References

- scikit-learn Neural Networks: https://scikit-learn.org/stable/modules/neural_networks_supervised.html
- Stanford CS229 Deep Learning notes index: https://cs229.stanford.edu/summer2023/

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
