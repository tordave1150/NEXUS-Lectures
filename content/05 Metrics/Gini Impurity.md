---
title: "Gini Impurity"
aliases:
  - Gini Index
topic_number: 81
domain:
  - Data Science
  - Machine Learning
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - gini
  - decision-tree
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Gini Impurity

> [!abstract] Summary
> Gini Impurity วัดความไม่บริสุทธิ์ของ class distribution ใน node และเป็น split criterion ที่พบบ่อยใน CART-style classification trees.

## Why this concept matters

คำนวณง่ายและมักให้ splits ใกล้ entropy แต่ไม่เหมือนกันทุกกรณี.

## Core Idea

- Formula \(1-\sum_kp_k^2\).
- ค่า 0 = pure node.
- เลือก split ที่ weighted child Gini ต่ำสุดหรือ impurity reduction สูงสุด.

## Mathematical Formulation / Technical Detail

\[
Gini(Q)=1-\sum_{k=1}^{K}p_k^2.
\]

Split impurity:
\[
G_{split}=\frac{n_L}{n}Gini(Q_L)+\frac{n_R}{n}Gini(Q_R).
\]

## Worked / Practical Example

Binary 50/50: Gini=0.5; 100/0: Gini=0. Lecture เปรียบ Gini ของ Outlook/Temperature/Humidity/Wind และเลือก Outlook เพราะ weighted Gini ต่ำสุด.

## When to use

- classification trees.
- เปรียบ candidate splits.

## Limitations / Assumptions

- Gini ไม่ใช่ coefficient แบบ Gini inequality index แม้ชื่อเหมือน.
- criterion choice มักมีผลน้อยกว่า depth/min samples/data quality แต่ต้อง validate.

## Common Mistakes

- เลือก Gini สูงสุดแทนต่ำสุดสำหรับ weighted impurity.
- สับสน node Gini กับ information gain.

## Cross-check / Corrections

- ไม่พบ correction สำคัญ; เพิ่มเฉพาะ context และ implementation caveats.

## Quick Review

- **Concept:** Gini Impurity วัดความไม่บริสุทธิ์ของ class distribution ใน node และเป็น split criterion ที่พบบ่อยใน CART-style classification trees.
- **จำให้ได้:** Formula \(1-\sum_kp_k^2\).
- **ใช้งาน:** classification trees.
- **ระวัง:** เลือก Gini สูงสุดแทนต่ำสุดสำหรับ weighted impurity.

## Related Notes

- [[Decision Trees]]
- [[Entropy and Information Gain]]
- [[Decision Tree Pruning]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 9-2 - Decision Trees]] | Slides 18–20 | Gini formula and worked split comparison |

## External References

- scikit-learn Decision Trees: https://scikit-learn.org/stable/modules/tree.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
