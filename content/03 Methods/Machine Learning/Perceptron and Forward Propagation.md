---
title: "Perceptron and Forward Propagation"
aliases:
  - Perceptron
  - Forward Propagation
topic_number: 41
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

# Perceptron and Forward Propagation

> [!abstract] Summary
> Perceptron เป็น linear binary classifierที่รวม weighted inputs + biasแล้วผ่าน threshold; forward propagationคือขั้นตอนคำนวณจาก inputไป outputด้วย parametersปัจจุบัน.

## Why this concept matters

Perceptronช่วยเข้าใจ neuron, decision boundary และเหตุผลที่ hidden layersจำเป็นสำหรับ nonlinear problems.

## Core Idea

- Decision boundary $w^Tx+b=0$ เป็น hyperplane.
- Step activationให้ class 0/1.
- Perceptron learning update weightsเมื่อ misclassified.
- Perceptron convergence theoremต้องการ linearly separable data.

## Mathematical Formulation / Technical Detail

Prediction:

$$
\hat y=\mathbb{1}(w^\top x+b>0).
$$

Simple update:

$$
w\leftarrow w+\eta(y-\hat y)x,
$$

$$
b\leftarrow b+\eta(y-\hat y).
$$

## Worked / Practical Example

OR truth table linearly separable จึงมี weights/biasที่ classify 4 pointsได้ถูกทั้งหมด. XOR ไม่ separableด้วยเส้นตรงเดียวจึง single perceptronทำไม่ได้.

## Assumptions and Interpretation

- Step functionไม่ differentiableจึง modern backpropใช้ differentiable activations.
- Broadcastingของ biasใน matrix implementationเป็น software operationที่เพิ่ม biasทุก row.

## When to use

- teaching linear classifiers.
- understand NN forward computations.

## When not to use / Limitations

- modern complex tasksโดยตรง.
- probability calibration; perceptron scoreไม่ใช่ probability.

## Common Mistakes

- พูดว่า perceptron = logistic regression.
- คิดว่า forward propagationคือ trainingทั้งหมด.
- ใช้ XORเป็นหลักฐานว่า neural networksทำไม่ได้ — hidden layersแก้ได้.

## Quick Review

- **Concept:** Perceptron เป็น linear binary classifierที่รวม weighted inputs + biasแล้วผ่าน threshold; forward propagationคือขั้นตอนคำนวณจาก inputไป outputด้วย parametersปัจจุบัน.
- **สิ่งที่ต้องจำ:** Decision boundary $w^Tx+b=0$ เป็น hyperplane.
- **การใช้งาน:** teaching linear classifiers.
- **ข้อควรระวัง:** พูดว่า perceptron = logistic regression.

## Related Notes

- [[Neural Networks Fundamentals]]
- [[Multilayer Perceptron and XOR]]
- [[Logistic Regression]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[12-NN_260718_091137]] | Perceptron / OR example / forward propagation | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `12-NN_260718_091137.pdf` — Perceptron / OR example / forward propagation

## External References

- [scikit-learn User Guide — Neural network models (supervised).](https://scikit-learn.org/stable/modules/neural_networks_supervised.html)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น

## DADS6003 Enrichment

Forward propagation สามารถเขียน layer-wise เป็น $z^{(l)}=W^{(l)}a^{(l-1)}+b^{(l)}$ และ $a^{(l)}=g(z^{(l)})$. DADS6003 ใช้ binary logic examples เพื่อเชื่อม perceptron ไปสู่ MLP และ backpropagation.

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 10 - Neural Network]] | Slides 4–9 | perceptron/MLP and forward pass |
