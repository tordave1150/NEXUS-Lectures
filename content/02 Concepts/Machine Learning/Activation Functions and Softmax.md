---
title: "Activation Functions and Softmax"
aliases:
  - Activation Function
  - Softmax
  - ReLU
  - Sigmoid
topic_number: 86
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
  - activation
  - softmax
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Activation Functions and Softmax

> [!abstract] Summary
> Activation functions เพิ่ม nonlinearity ให้ neural networks; output activation ต้องสัมพันธ์กับ target/loss. Softmax แปลง multiclass logits เป็น probability vector ที่รวมกันเป็น 1.

## Why this concept matters

ถ้าไม่มี nonlinear activations หลาย linear layers collapse เป็น linear transformation เดียว; activation จึงเป็นเหตุผลหลักที่ MLP model nonlinear boundaries ได้.

## Core Idea

- Sigmoid: output (0,1), เหมาะ binary probability output.
- ReLU: \(\max(0,z)\), common hidden activation.
- Softmax: normalize K logits เป็น categorical probabilities.
- Loss และ output activation ควรจับคู่ เช่น softmax + cross-entropy.

## Mathematical Formulation / Technical Detail

Sigmoid:
\[
\sigma(z)=\frac1{1+e^{-z}}.
\]

ReLU:
\[
ReLU(z)=\max(0,z).
\]

Softmax:
\[
p_k=\frac{e^{z_k}}{\sum_j e^{z_j}}.
\]

เพื่อ numerical stability คำนวณจาก \(z_k-\max_j z_j\).

## Worked / Practical Example

Three-class logits [2,1,0] ผ่าน softmax ให้ probabilities positive และ sum=1. การบวก constant เดียวกันทุก logits ไม่เปลี่ยน softmax probabilities.

## When to use

- hidden/output design ของ neural networks.
- multiclass classification probability output.

## Limitations / Assumptions

- Sigmoid/tanh saturation ทำ gradient เล็ก.
- ReLU units อาจ inactive.
- Softmax probability อาจ overconfident และ calibration ต้องตรวจ.

## Common Mistakes

- ใช้ softmax ทีละ class แยกกันแทน joint normalization.
- คิดว่า ReLU output เป็น probability.
- ใช้ activation โดยไม่สัมพันธ์กับ loss/target domain.

## Cross-check / Corrections

- ไม่พบ correction สำคัญ; เพิ่มเฉพาะ context และ implementation caveats.

## Quick Review

- **Concept:** Activation functions เพิ่ม nonlinearity ให้ neural networks; output activation ต้องสัมพันธ์กับ target/loss. Softmax แปลง multiclass logits เป็น probability vector ที่รวมกันเป็น 1.
- **จำให้ได้:** Sigmoid: output (0,1), เหมาะ binary probability output.
- **ใช้งาน:** hidden/output design ของ neural networks.
- **ระวัง:** ใช้ softmax ทีละ class แยกกันแทน joint normalization.

## Related Notes

- [[Backpropagation]]
- [[Neural Networks Fundamentals]]
- [[Multilayer Perceptron and XOR]]
- [[Logistic Regression]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 10 - Neural Network]] | Slides 17–18 | activation and softmax overview |

## External References

- scikit-learn Neural Networks: https://scikit-learn.org/stable/modules/neural_networks_supervised.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
