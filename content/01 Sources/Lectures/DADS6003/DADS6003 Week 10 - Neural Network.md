---
title: "DADS6003 Week 10 - Neural Network"
source_type: lecture
course: DADS6003
document: "DADS6003_week10_nn_260424_200018.pdf"
author: "Ekarat Rattagan"
language:
  - en
  - th-annotations
reliability: "Moderate → High after cross-check"
status: reviewed
created: 2026-08-08
updated: 2026-08-08
tags:
  - source
  - lecture
  - dads6003
---

# Week 10: Neural Network

## Document Metadata

- **Course:** DADS6003
- **Lecturer:** Ekarat Rattagan
- **File:** `DADS6003_week10_nn_260424_200018.pdf`
- **Slides:** 1–21
- **Type:** Lecture PDF with handwritten annotations
- **Drive:** https://drive.google.com/file/d/1xTZqmvNKcpp5MOXbr6zeUZTLTgTLgTBV/view
- **Reliability:** Moderate as lecture material; important formulas, definitions and worked examples cross-checked against official scikit-learn documentation and Stanford CS229 material.

## Topics / Slide Map

| Topic | Location |
|---|---|
| Motivation, perceptron and MLP | Slides 2–7 |
| Forward pass and binary cross-entropy | Slides 8–9 |
| Backpropagation derivation | Slides 10–16 |
| Activation functions, softmax and history | Slides 17–20 |

## Canonical Notes

- [[Neural Networks Fundamentals]]
- [[Perceptron and Forward Propagation]]
- [[Multilayer Perceptron and XOR]]
- [[Backpropagation]]
- [[Activation Functions and Softmax]]

## Reliability / Cross-check Notes

- Hidden-layer backpropagation ใน network ทั่วไปต้องรวม contributions จาก downstream units: delta_j^l = f'(z_j^l) Σ_i w_ij^l delta_i^(l+1). สูตรที่ไม่มี summation ใช้ได้เฉพาะ topology พิเศษ/ตัวอย่างที่มี downstream path เดียว.
- Neural network ไม่ได้แก้ 'many features' โดยอัตโนมัติ; capacity สูงเพิ่มทั้ง expressive power และความต้องการ data/regularization/compute.

> [!warning] Use lecture as a learning source, not as unquestioned ground truth
> สูตร, numerical example, terminology และ rule of thumb ที่มีผลต่อการใช้งานจริงจะถูกเก็บใน canonical note หลัง cross-check แล้ว หาก lecture ขัดกับ standard reference canonical note จะเก็บทั้ง original claim และ correction อย่างชัดเจน.

## Source Traceability

Canonical notesที่ link มายัง source นี้ควรอ้างรูปแบบ:
`[Source: DADS6003_week10_nn_260424_200018.pdf, slide <n>]`
