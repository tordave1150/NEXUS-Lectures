---
title: "Multilayer Perceptron and XOR"
aliases:
  - MLP
  - XOR Neural Network
  - Hidden Layers
topic_number: 42
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[12-NN_260718_091137]]"
  - "[[DADS6003 Week 10 - Neural Network]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Multilayer Perceptron and XOR

> [!abstract] Summary
> Multilayer Perceptron (MLP) stacking nonlinear hidden layersสามารถสร้าง nonlinear decision boundariesที่ single perceptronทำไม่ได้ เช่น XOR.

## Why this concept matters

XOR เป็นตัวอย่างคลาสสิกที่แสดงบทบาทของ representation learning: hidden unitsสร้าง intermediate featuresก่อน output layerรวมผล.

## Core Idea

- Hidden layer neuronsแบ่ง input spaceเป็น regions.
- Nonlinear activationจำเป็น; stacking purely linear layersยังเทียบเท่า linear transformเดียว.
- Backpropagationใช้ chain ruleส่ง gradientย้อนจาก loss.
- Depth/widthเพิ่ม capacityแต่เพิ่ม overfitting/optimization cost.

## Mathematical Formulation / Technical Detail

Two-layer schematic:

$$
h=g(W_1x+b_1)
$$

$$
\hat y=g_o(W_2h+b_2).
$$

Training minimizes loss $L(y,\hat y)$ via gradients:

$$
W\leftarrow W-\eta\nabla_W L.
$$

## Worked / Practical Example

XOR outputs 1เมื่อ inputsต่างกัน: (0,1),(1,0). ไม่มีเส้นเดียวแยก positive/negativeได้ แต่ hidden unitsสามารถสร้าง regionsแล้ว outputรวมเป็น XOR boundary.

## Assumptions and Interpretation

- Activation/loss choiceขึ้นกับ regression/binary/multiclass.
- Deep network performanceต้องดู validation ไม่ใช่ training accuracy.

## When to use

- nonlinear classification/regression.
- foundation for deeper architectures.

## When not to use / Limitations

- tiny datasetที่ linear modelเพียงพอ.
- เมื่อ interpretabilityและcalibrationสำคัญโดยไม่มี validation.

## Common Mistakes

- ใช้ hidden layersแต่ activationเป็น identityทุกชั้น.
- ไม่ regularize/early stop.
- ตีความ individual hidden neuronเป็น semantic featureเสมอ.

## Quick Review

- **Concept:** Multilayer Perceptron (MLP) stacking nonlinear hidden layersสามารถสร้าง nonlinear decision boundariesที่ single perceptronทำไม่ได้ เช่น XOR.
- **สิ่งที่ต้องจำ:** Hidden layer neuronsแบ่ง input spaceเป็น regions.
- **การใช้งาน:** nonlinear classification/regression.
- **ข้อควรระวัง:** ใช้ hidden layersแต่ activationเป็น identityทุกชั้น.

## Related Notes

- [[Perceptron and Forward Propagation]]
- [[Neural Networks Fundamentals]]
- [[Modern Neural Forecasting Models]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[12-NN_260718_091137]] | Hidden layers and XOR classification section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `12-NN_260718_091137.pdf` — Hidden layers and XOR classification section

## External References

- [scikit-learn User Guide — Neural network models (supervised).](https://scikit-learn.org/stable/modules/neural_networks_supervised.html)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น

## DADS6003 Enrichment — General Backprop Caveat

สำหรับ hidden unit ทั่วไป delta ต้องรวมผลจาก **ทุก downstream unit**:

$$
\delta_j^{(l)}=g'(z_j^{(l)})\sum_i w_{ij}^{(l)}\delta_i^{(l+1)}.
$$

ดังนั้นสูตรที่ดูเหมือนไม่มี summation ใน worked example ของ lecture ใช้ได้กับ topology/example เฉพาะ ไม่ควรนำไปใช้เป็น general hidden-layer recursion โดยตรง.

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 10 - Neural Network]] | Slides 10–16 | chain-rule derivation and backprop example |
