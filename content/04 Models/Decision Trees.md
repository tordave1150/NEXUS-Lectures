---
title: "Decision Trees"
aliases:
  - Decision Tree
  - CART
  - ID3
  - C4.5
topic_number: 79
domain:
  - Data Science
  - Machine Learning
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - decision-tree
  - cart
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Decision Trees

> [!abstract] Summary
> Decision Tree recursively split feature space ด้วย if–then rules เพื่อลด impurity/error; ใช้ได้ทั้ง classification และ regression และมี interpretability สูงแต่ variance สูงเมื่อ tree ลึก.

## Why this concept matters

เป็นพื้นฐานของ Random Forest และ Boosting tree models.

## Core Idea

- แต่ละ internal node เลือก feature/threshold หรือ category split.
- Leaf เก็บ class distribution/mean/other target statistic.
- ID3 เน้น information gain; C4.5 ขยาย continuous attributes/pruning; CART ใช้ binary splits และรองรับ regression.
- Tree ไม่ต้อง standardize features สำหรับ axis-aligned split criteria.

## Mathematical Formulation / Technical Detail

Candidate split \(\theta\) แบ่ง node data \(Q\) เป็น \(Q_L,Q_R\). เลือก split ที่ minimize weighted impurity:

\[
G(Q,\theta)=\frac{n_L}{n}H(Q_L)+\frac{n_R}{n}H(Q_R).
\]

\(H\) อาจเป็น Gini/entropy สำหรับ classification หรือ squared error สำหรับ regression.

## Worked / Practical Example

Play-tennis example: compare Outlook/Humidity/Wind/Temperature; feature ที่ลด impurity มากสุดเป็น root แล้ว recurse บน subsets.

## When to use

- nonlinear interactions และ interpretable rules.
- mixed-scale numerical features.
- base learner สำหรับ ensembles.

## Limitations / Assumptions

- Unpruned deep trees overfit/unstable.
- Axis-aligned splits ไม่ smooth และ extrapolate regression ไม่ดี.
- High-cardinality features/imbalance ต้องระวัง.

## Common Mistakes

- คิดว่า Decision Trees ต้อง feature scaling.
- เรียก Bagging/Boosting ว่า pruning.
- สับสน algorithm family CART กับ criterion option ของ library.

## Cross-check / Corrections

- Canonical note แยก traditional CART criteria ออกจาก CART-style library implementations ที่อาจ support entropy/log-loss.

## Quick Review

- **Concept:** Decision Tree recursively split feature space ด้วย if–then rules เพื่อลด impurity/error; ใช้ได้ทั้ง classification และ regression และมี interpretability สูงแต่ variance สูงเมื่อ tree ลึก.
- **จำให้ได้:** แต่ละ internal node เลือก feature/threshold หรือ category split.
- **ใช้งาน:** nonlinear interactions และ interpretable rules.
- **ระวัง:** คิดว่า Decision Trees ต้อง feature scaling.

## Related Notes

- [[Entropy and Information Gain]]
- [[Gini Impurity]]
- [[Decision Tree Pruning]]
- [[Bagging and Random Forest]]
- [[Boosting and AdaBoost]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 9-2 - Decision Trees]] | Slides 2–24 | tree rules, ID3, CART, impurity, ensembles |

## External References

- scikit-learn Decision Trees: https://scikit-learn.org/stable/modules/tree.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
