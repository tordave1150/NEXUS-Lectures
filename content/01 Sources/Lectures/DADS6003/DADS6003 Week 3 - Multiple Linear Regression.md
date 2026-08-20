---
title: "DADS6003 Week 3 - Multiple Linear Regression"
source_type: lecture
course: DADS6003
document: "DADS6003_week3_MLR_260301_155054.pdf"
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

# Week 3: Multiple Linear Regression

## Document Metadata

- **Course:** DADS6003
- **Lecturer:** Ekarat Rattagan
- **File:** `DADS6003_week3_MLR_260301_155054.pdf`
- **Slides:** 1–11
- **Type:** Lecture PDF with handwritten annotations
- **Drive:** https://drive.google.com/file/d/1ZnfHSOKelcKI9XBtxLjtvktO0vRNeqMW/view
- **Reliability:** Moderate as lecture material; important formulas, definitions and worked examples cross-checked against official scikit-learn documentation and Stanford CS229 material.

## Topics / Slide Map

| Topic | Location |
|---|---|
| Multiple linear regression and matrix form | Slides 2–5 |
| Feature scaling | Slides 6 |
| SGD and mini-batch gradient descent | Slides 7–9 |
| Polynomial regression | Slides 10 |

## Canonical Notes

- [[Multiple Linear Regression]]
- [[Feature Scaling]]
- [[Stochastic and Mini-batch Gradient Descent]]
- [[Learning Rate and Scheduling]]
- [[Polynomial Regression]]

## Reliability / Cross-check Notes

- Z-score scaling ไม่ได้ map ค่าให้อยู่ในช่วงตายตัว แต่ทำให้ training feature มี mean≈0 และ variance≈1; ค่าสุดโต่งยังเกิน ±3 ได้.
- Learning-rate decay formula เป็นหนึ่งในหลาย schedules ไม่ใช่กฎมาตรฐานเดียว.

> [!warning] Use lecture as a learning source, not as unquestioned ground truth
> สูตร, numerical example, terminology และ rule of thumb ที่มีผลต่อการใช้งานจริงจะถูกเก็บใน canonical note หลัง cross-check แล้ว หาก lecture ขัดกับ standard reference canonical note จะเก็บทั้ง original claim และ correction อย่างชัดเจน.

## Source Traceability

Canonical notesที่ link มายัง source นี้ควรอ้างรูปแบบ:
`[Source: DADS6003_week3_MLR_260301_155054.pdf, slide <n>]`
