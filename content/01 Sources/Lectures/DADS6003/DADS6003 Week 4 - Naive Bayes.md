---
title: "DADS6003 Week 4 - Naive Bayes"
source_type: lecture
course: DADS6003
document: "DADS6003_week7_nb_260516_152015.pdf"
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

# Week 4: Naive Bayes Classification

## Document Metadata

- **Course:** DADS6003
- **Lecturer:** Ekarat Rattagan
- **File:** `DADS6003_week7_nb_260516_152015.pdf`
- **Slides:** 1–15
- **Type:** Lecture PDF with handwritten annotations
- **Drive:** https://drive.google.com/file/d/1OAm-sMM4yL7QQZ072pH0h_85OcI5PuFC/view
- **Reliability:** Moderate as lecture material; important formulas, definitions and worked examples cross-checked against official scikit-learn documentation and Stanford CS229 material.

## Topics / Slide Map

| Topic | Location |
|---|---|
| Bayes rule and conditional probability | Slides 2–5 |
| Conditional-independence assumption | Slides 6–8 |
| Worked Naive Bayes classification | Slides 9–11 |
| Gaussian likelihood and Laplace smoothing | Slides 12–14 |

## Canonical Notes

- [[Bayes Theorem]]
- [[Naive Bayes]]

## Reliability / Cross-check Notes

- Worked example มี arithmetic/decimal error: Male score = 1/108≈0.00926 ไม่ใช่ 0.092. Female score = 0.012 ดังนั้น normalized posterior ประมาณ Male 43.5%, Female 56.5%; class ที่ได้จากตัวเลขในสไลด์ควรเป็น Female.
- Laplace smoothing ต้อง apply ต่อ conditional categorical counts ภายใน class/feature ตามจำนวน categories ของ feature; ไม่ใช่เพียงบวกหนึ่งกับ global class frequency ในทุกบริบท.

> [!warning] Use lecture as a learning source, not as unquestioned ground truth
> สูตร, numerical example, terminology และ rule of thumb ที่มีผลต่อการใช้งานจริงจะถูกเก็บใน canonical note หลัง cross-check แล้ว หาก lecture ขัดกับ standard reference canonical note จะเก็บทั้ง original claim และ correction อย่างชัดเจน.

## Source Traceability

Canonical notesที่ link มายัง source นี้ควรอ้างรูปแบบ:
`[Source: DADS6003_week7_nb_260516_152015.pdf, slide <n>]`
