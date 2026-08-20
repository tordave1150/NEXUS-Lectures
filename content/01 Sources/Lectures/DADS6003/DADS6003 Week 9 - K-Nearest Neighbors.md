---
title: "DADS6003 Week 9 - K-Nearest Neighbors"
source_type: lecture
course: DADS6003
document: "DADS6003_week09_knn_260516_155501.pdf"
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

# Week 9: K-Nearest Neighbors (k-NN)

## Document Metadata

- **Course:** DADS6003
- **Lecturer:** Ekarat Rattagan
- **File:** `DADS6003_week09_knn_260516_155501.pdf`
- **Slides:** 1–13
- **Type:** Lecture PDF with handwritten annotations
- **Drive:** https://drive.google.com/file/d/1FDxU-e6Tu3ShoDxRYfxUWCcwDrewte0N/view
- **Reliability:** Moderate as lecture material; important formulas, definitions and worked examples cross-checked against official scikit-learn documentation and Stanford CS229 material.

## Topics / Slide Map

| Topic | Location |
|---|---|
| Instance-based learning and k-NN algorithm | Slides 2–5 |
| Categorical distance example | Slides 6–7 |
| Hyperparameter k and decision boundaries | Slides 8–9 |
| Scaling, noise, computation and dimensionality | Slides 10–12 |

## Canonical Notes

- [[K-Nearest Neighbors]]
- [[Feature Scaling]]
- [[Cross Validation]]

## Reliability / Cross-check Notes

- Z-score standardization ไม่ map values เข้า (-3,3); ทำให้ mean≈0, SD≈1 แต่ support ยัง unbounded.
- การเลือก odd k ลดโอกาส tie ใน binary classification บางกรณีเท่านั้น ไม่รับประกันว่าไม่มี tie ใน multiclass/weighted settings.
- การบีบอัด ZIP ไม่ใช่ algorithmic remedy มาตรฐานสำหรับ k-NN memory/computation; ใช้ dimensionality reduction, approximate neighbors, indexing structures หรือ prototype selection ตามบริบท.

> [!warning] Use lecture as a learning source, not as unquestioned ground truth
> สูตร, numerical example, terminology และ rule of thumb ที่มีผลต่อการใช้งานจริงจะถูกเก็บใน canonical note หลัง cross-check แล้ว หาก lecture ขัดกับ standard reference canonical note จะเก็บทั้ง original claim และ correction อย่างชัดเจน.

## Source Traceability

Canonical notesที่ link มายัง source นี้ควรอ้างรูปแบบ:
`[Source: DADS6003_week09_knn_260516_155501.pdf, slide <n>]`
