---
title: "DADS6003 Week 9-2 - Decision Trees"
source_type: lecture
course: DADS6003
document: "DADS6003_week9-2_tree_260516_162056.pdf"
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

# Week 9-2: Decision Trees

## Document Metadata

- **Course:** DADS6003
- **Lecturer:** Ekarat Rattagan
- **File:** `DADS6003_week9-2_tree_260516_162056.pdf`
- **Slides:** 1–25
- **Type:** Lecture PDF with handwritten annotations
- **Drive:** https://drive.google.com/file/d/18RjvqMu70YrQHqOyFc-Kfl9hv0Lqsdyd/view
- **Reliability:** Moderate as lecture material; important formulas, definitions and worked examples cross-checked against official scikit-learn documentation and Stanford CS229 material.

## Topics / Slide Map

| Topic | Location |
|---|---|
| Decision-tree rules and entropy | Slides 2–4 |
| Information gain and ID3 | Slides 5–16 |
| CART, Gini impurity and split criteria | Slides 17–20 |
| Overfitting, pruning, bagging and boosting | Slides 21–24 |

## Canonical Notes

- [[Decision Trees]]
- [[Entropy and Information Gain]]
- [[Gini Impurity]]
- [[Decision Tree Pruning]]
- [[Bagging and Random Forest]]
- [[Boosting and AdaBoost]]
- [[Ensemble Learning]]

## Reliability / Cross-check Notes

- CART เป็น binary-tree family; traditional CART classification ใช้ Gini impurity และ regression ใช้ squared-error style criteria. Libraries อาจมี entropy/log-loss criterion ใน CART-style implementation จึงควรแยก algorithm family ออกจาก criterion implementation.
- Bagging/Boosting ไม่ใช่ pruning methods; เป็น ensemble strategies ที่แก้ generalization ผ่านการรวมหลาย learners.

> [!warning] Use lecture as a learning source, not as unquestioned ground truth
> สูตร, numerical example, terminology และ rule of thumb ที่มีผลต่อการใช้งานจริงจะถูกเก็บใน canonical note หลัง cross-check แล้ว หาก lecture ขัดกับ standard reference canonical note จะเก็บทั้ง original claim และ correction อย่างชัดเจน.

## Source Traceability

Canonical notesที่ link มายัง source นี้ควรอ้างรูปแบบ:
`[Source: DADS6003_week9-2_tree_260516_162056.pdf, slide <n>]`
