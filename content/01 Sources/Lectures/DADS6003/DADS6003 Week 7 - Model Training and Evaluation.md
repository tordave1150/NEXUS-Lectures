---
title: "DADS6003 Week 7 - Model Training and Evaluation"
source_type: lecture
course: DADS6003
document: "DADS6003_week7_model_evaluation_260301_153251.pdf"
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

# Week 7: Model Training and Evaluation

## Document Metadata

- **Course:** DADS6003
- **Lecturer:** Ekarat Rattagan
- **File:** `DADS6003_week7_model_evaluation_260301_153251.pdf`
- **Slides:** 1–18
- **Type:** Lecture PDF with handwritten annotations
- **Drive:** https://drive.google.com/file/d/1Na43U4A166NFHA3cDI3pWQJJm-F3Sy1S/view
- **Reliability:** Moderate as lecture material; important formulas, definitions and worked examples cross-checked against official scikit-learn documentation and Stanford CS229 material.

## Topics / Slide Map

| Topic | Location |
|---|---|
| Holdout and train/validation/test | Slides 2–5 |
| Bias–variance diagnosis | Slides 6–9 |
| Confusion matrix and classification metrics | Slides 10–15 |
| ROC/AUC and precision–recall curve | Slides 16–18 |

## Canonical Notes

- [[Train Validation Test Split]]
- [[Cross Validation]]
- [[Bias Variance Tradeoff]]
- [[Classification Metrics]]

## Reliability / Cross-check Notes

- การแบ่ง 60/20/20 เพียงครั้งเดียวเป็น three-way holdout split ไม่ใช่ cross-validation. Cross-validation ต้องมี repeated folds/splits บน training data.
- Holdout ไม่ได้ทำให้ model overfit โดยตัวมันเอง; ปัญหาคือ estimate มี variance สูงกว่าการ resample และการ tune ซ้ำบน test set ทำให้เกิด selection bias.
- เพิ่ม training data มักช่วยลด variance/estimation error แต่ผลต่อ bias ไม่ใช่ศูนย์ในทุก setting; ข้อความใน lecture เป็น simplified diagnostic heuristic.

> [!warning] Use lecture as a learning source, not as unquestioned ground truth
> สูตร, numerical example, terminology และ rule of thumb ที่มีผลต่อการใช้งานจริงจะถูกเก็บใน canonical note หลัง cross-check แล้ว หาก lecture ขัดกับ standard reference canonical note จะเก็บทั้ง original claim และ correction อย่างชัดเจน.

## Source Traceability

Canonical notesที่ link มายัง source นี้ควรอ้างรูปแบบ:
`[Source: DADS6003_week7_model_evaluation_260301_153251.pdf, slide <n>]`
