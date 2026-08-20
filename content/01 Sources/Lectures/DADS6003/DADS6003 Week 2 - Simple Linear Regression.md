---
title: "DADS6003 Week 2 - Simple Linear Regression"
source_type: lecture
course: DADS6003
document: "DADS6003_week2_regression_260117_105205.pdf"
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

# Week 2: Single Variable Linear Regression

## Document Metadata

- **Course:** DADS6003
- **Lecturer:** Ekarat Rattagan
- **File:** `DADS6003_week2_regression_260117_105205.pdf`
- **Slides:** 1–16
- **Type:** Lecture PDF with handwritten annotations
- **Drive:** https://drive.google.com/file/d/1FGFZrZmHcfeQS0Zfw9iPexxBwXczarxy/view
- **Reliability:** Moderate as lecture material; important formulas, definitions and worked examples cross-checked against official scikit-learn documentation and Stanford CS229 material.

## Topics / Slide Map

| Topic | Location |
|---|---|
| Notation, model representation, MSE | Slides 2–4 |
| Normal equation and pseudoinverse | Slides 5–7 |
| Batch Gradient Descent | Slides 8–13 |
| Iterative vs analytical approaches | Slides 14–15 |

## Canonical Notes

- [[Simple Linear Regression]]
- [[Ordinary Least Squares and Normal Equation]]
- [[Gradient Descent]]

## Reliability / Cross-check Notes

- ถ้านิยาม MSE เป็น J=(1/N)Σ(h−y)^2 gradient มี factor 2; สูตร update ที่ไม่มี factor 2 สอดคล้องกับ J=(1/2N)Σ(h−y)^2 หรือมอง factor 2 ว่าถูก absorb เข้า learning rate.
- ความซับซ้อน O(n^3) ของการ invert X'X ควรตีความ n เป็นจำนวน features ของเมทริกซ์ที่ invert; modern least-squares solvers มักใช้ QR/SVD/pseudoinverse แทน explicit inverse.

> [!warning] Use lecture as a learning source, not as unquestioned ground truth
> สูตร, numerical example, terminology และ rule of thumb ที่มีผลต่อการใช้งานจริงจะถูกเก็บใน canonical note หลัง cross-check แล้ว หาก lecture ขัดกับ standard reference canonical note จะเก็บทั้ง original claim และ correction อย่างชัดเจน.

## Source Traceability

Canonical notesที่ link มายัง source นี้ควรอ้างรูปแบบ:
`[Source: DADS6003_week2_regression_260117_105205.pdf, slide <n>]`
