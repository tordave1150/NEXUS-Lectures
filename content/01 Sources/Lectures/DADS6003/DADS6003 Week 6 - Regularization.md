---
title: "DADS6003 Week 6 - Regularization"
source_type: lecture
course: DADS6003
document: "DADS6003_week6_regularization_v2_260208_114444.pdf"
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

# Week 6: Regularization

## Document Metadata

- **Course:** DADS6003
- **Lecturer:** Ekarat Rattagan
- **File:** `DADS6003_week6_regularization_v2_260208_114444.pdf`
- **Slides:** 1–27
- **Type:** Lecture PDF with handwritten annotations
- **Drive:** https://drive.google.com/file/d/1ysMmodRv665Q8RxCP6maQ4B7rbF38plH/view
- **Reliability:** Moderate as lecture material; important formulas, definitions and worked examples cross-checked against official scikit-learn documentation and Stanford CS229 material.

## Topics / Slide Map

| Topic | Location |
|---|---|
| Overfitting and regularization intuition | Slides 3–10 |
| Ridge regression and coefficient paths | Slides 11–13 |
| Lasso regression and sparsity | Slides 14–19 |
| Elastic Net | Slides 20–23 |
| SGD-style updates and references | Slides 24–27 |

## Canonical Notes

- [[Regularized Regression]]
- [[Ridge Regression]]
- [[Lasso Regression]]
- [[Elastic Net]]
- [[Bias Variance Tradeoff]]

## Reliability / Cross-check Notes

- ข้อความเชิง recommendation เช่น 'Ridge is a good default' เป็น heuristic ไม่ใช่ universal rule; ควรเลือก penalty และ strength ด้วย cross-validation.
- Lasso objective ไม่ differentiable ที่ coefficient=0; practical solvers มักใช้ coordinate descent/proximal methods หรือ subgradient-like methods มากกว่าการอาศัย plain SGD อย่างเดียว.

> [!warning] Use lecture as a learning source, not as unquestioned ground truth
> สูตร, numerical example, terminology และ rule of thumb ที่มีผลต่อการใช้งานจริงจะถูกเก็บใน canonical note หลัง cross-check แล้ว หาก lecture ขัดกับ standard reference canonical note จะเก็บทั้ง original claim และ correction อย่างชัดเจน.

## Source Traceability

Canonical notesที่ link มายัง source นี้ควรอ้างรูปแบบ:
`[Source: DADS6003_week6_regularization_v2_260208_114444.pdf, slide <n>]`
