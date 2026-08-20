---
title: "Neural Networks Fundamentals"
aliases:
  - Neural Network
  - Artificial Neural Network
  - ANN
topic_number: 39
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

# Neural Networks Fundamentals

> [!abstract] Summary
> Neural Network ประกอบด้วย layersของ neuronsที่คำนวณ weighted sums + biasesแล้วผ่าน nonlinear activation ทำให้เรียน complex nonlinear mappings.

## Why this concept matters

NN เป็น universal function approximatorใน practical senseเมื่อมี architecture/trainingเหมาะสม แต่ความยืดหยุ่นสูงทำให้ต้องควบคุม overfittingและ scaling.

## Core Idea

- Input layerรับ features; hidden layersเรียน representations; output layerขึ้นกับ task.
- Weightsและbiasesคือ trainable parameters.
- Activation function เช่น ReLUสร้าง nonlinearity.
- Forward propagationคำนวณ prediction; backpropagationคำนวณ gradientsเพื่อ update parameters.
- Architecture depth/widthเป็น hyperparameters.

## Mathematical Formulation / Technical Detail

Neuron:

$$
z=w^\top x+b,\qquad a=g(z).
$$

Layer:

$$
a^{(\ell)}=g\left(W^{(\ell)}a^{(\ell-1)}+b^{(\ell)}\right).
$$

## Worked / Practical Example

Network 3 inputs → hidden 3 → hidden 3 → 2 outputs มี connection weights 3×3 + 3×3 + 3×2 = 24 ก่อนนับ biases. จำนวน parametersโตเร็วตาม layer widths.

## Assumptions and Interpretation

- Featuresมักควร scale.
- Trainingเป็น non-convex optimization; initializationและstochastic trainingทำให้ seedมีผล.
- Lossต้องสัมพันธ์กับ task/distribution.

## When to use

- large nonlinear datasets.
- global forecasting across many related series.
- complex interactions.

## When not to use / Limitations

- small dataที่ simple modelเพียงพอ.
- ต้องการ highly transparent coefficients.

## Common Mistakes

- นับ bias parametersผิด.
- ใช้ deep modelโดยไม่มี baseline.
- ไม่แยก hyperparametersจาก learned parameters.

## Quick Review

- **Concept:** Neural Network ประกอบด้วย layersของ neuronsที่คำนวณ weighted sums + biasesแล้วผ่าน nonlinear activation ทำให้เรียน complex nonlinear mappings.
- **สิ่งที่ต้องจำ:** Input layerรับ features; hidden layersเรียน representations; output layerขึ้นกับ task.
- **การใช้งาน:** large nonlinear datasets.
- **ข้อควรระวัง:** นับ bias parametersผิด.

## Related Notes

- [[Perceptron and Forward Propagation]]
- [[Multilayer Perceptron and XOR]]
- [[Modern Neural Forecasting Models]]
- [[NNAR]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[12-NN_260718_091137]] | NN architecture preview / practical considerations | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `12-NN_260718_091137.pdf` — NN architecture preview / practical considerations

## External References

- [scikit-learn User Guide — Neural network models (supervised).](https://scikit-learn.org/stable/modules/neural_networks_supervised.html)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น

## DADS6003 Enrichment — Training View

DADS6003 Week 10 เติมภาพ training loop ให้ canonical note:

1. Forward pass คำนวณ activations และ prediction.
2. Compute task-appropriate loss เช่น binary cross-entropy.
3. [[Backpropagation]] ใช้ chain rule หา gradients ของ weights/biases.
4. Optimizer เช่น [[Stochastic and Mini-batch Gradient Descent]] อัปเดต parameters.

ดู [[Activation Functions and Softmax]] สำหรับ ReLU/sigmoid/softmax และ output-layer choices.

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 10 - Neural Network]] | Slides 4–18 | perceptron/MLP architecture, forward pass, backprop, activations, softmax |
