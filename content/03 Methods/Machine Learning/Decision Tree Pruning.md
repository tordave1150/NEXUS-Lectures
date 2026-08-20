---
title: "Decision Tree Pruning"
aliases:
  - Tree Pruning
  - Post-pruning
  - Pre-pruning
topic_number: 82
domain:
  - Data Science
  - Machine Learning
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - decision-tree
  - pruning
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Decision Tree Pruning

> [!abstract] Summary
> Tree pruning ลด complexity ของ decision tree เพื่อ improve generalization; ทำได้ก่อน growth จบผ่าน constraints หรือหลัง grow ผ่าน cost-complexity/subtree pruning.

## Why this concept matters

Tree ลึกสามารถ fit noise ได้ง่าย จึงต้อง control complexity เหมือน regularization ใน model families อื่น.

## Core Idea

- Pre-pruning: max_depth, min_samples_leaf, max_leaf_nodes ฯลฯ.
- Post-pruning: grow tree แล้วเลือก smaller subtree.
- Cost-complexity pruning trade off empirical impurity กับจำนวน leaves.

## Mathematical Formulation / Technical Detail

\[
R_\alpha(T)=R(T)+\alpha|T_{\text{leaves}}|.
\]

\(\alpha\) ใหญ่ขึ้น penalize tree size มากขึ้น จึงได้ subtree เล็กลง.

## Worked / Practical Example

แทนที่จะปล่อย depth unlimited แล้วเลือกด้วย training accuracy ให้ tune `ccp_alpha` หรือ depth constraints ด้วย CV. Smaller tree อาจ validation ดีขึ้นแม้ training accuracy ลด.

## When to use

- single decision tree ที่ overfit.
- ต้องการ interpretable compact rule set.

## Limitations / Assumptions

- Pruning criterion ต้อง tune บน validation/CV.
- Ensemble trees มักใช้ different complexity controls; ไม่เหมือน pruning single tree.

## Common Mistakes

- เรียก bagging/boosting ว่า pruning.
- prune จาก test-set performance.

## Cross-check / Corrections

- Bagging/Boosting ถูกย้ายออกจาก 'pruning solution' ไปเป็น separate ensemble notes.

## Quick Review

- **Concept:** Tree pruning ลด complexity ของ decision tree เพื่อ improve generalization; ทำได้ก่อน growth จบผ่าน constraints หรือหลัง grow ผ่าน cost-complexity/subtree pruning.
- **จำให้ได้:** Pre-pruning: max_depth, min_samples_leaf, max_leaf_nodes ฯลฯ.
- **ใช้งาน:** single decision tree ที่ overfit.
- **ระวัง:** เรียก bagging/boosting ว่า pruning.

## Related Notes

- [[Decision Trees]]
- [[Bias Variance Tradeoff]]
- [[Cross Validation]]
- [[Bagging and Random Forest]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 9-2 - Decision Trees]] | Slides 21–22 | overfitting and post-pruning intuition |

## External References

- scikit-learn Cost Complexity Pruning: https://scikit-learn.org/stable/modules/tree.html#minimal-cost-complexity-pruning

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
