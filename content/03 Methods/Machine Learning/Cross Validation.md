---
title: "Cross Validation"
aliases:
  - K-Fold Cross Validation
  - CV
topic_number: 75
domain:
  - Data Science
  - Machine Learning
  - Model Evaluation
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - cross-validation
  - evaluation
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Cross Validation

> [!abstract] Summary
> Cross-validation (CV) ประเมิน model/hyperparameters โดย fit/validate หลาย splits ของ training data แล้ว aggregate performance เพื่อลด dependence ต่อ single holdout split.

## Why this concept matters

ใช้เมื่ออยาก estimate generalization และ tune hyperparameters โดยยังเก็บ final test set ไว้ untouched.

## Core Idea

- K-fold: แบ่ง training dataเป็น K folds; train K−1, validate 1 สลับกัน.
- Classification มักใช้ stratified folds เพื่อรักษา class proportions.
- Grouped observations ต้องใช้ group-aware CV; time series ใช้ forward/rolling CV แทน ordinary random K-fold.
- ทุก preprocessing step ที่เรียน parameters ต้องอยู่ใน pipeline ภายในแต่ละ fold.

## Mathematical Formulation / Technical Detail

\[
\widehat{Score}_{CV}=\frac1K\sum_{k=1}^{K}Score_k.
\]

CV estimate มี uncertainty; report distribution/SD เมื่อ decision sensitive.

## Worked / Practical Example

GridSearchCV สำหรับ k-NN: แต่ละ candidate k ถูก evaluate บน folds เดียวกัน; เลือก k จาก mean validation score จากนั้น refit บน training dataทั้งหมด และประเมิน final test หนึ่งครั้ง.

## When to use

- hyperparameter tuning.
- model comparison เมื่อ data จำกัด.

## Limitations / Assumptions

- CV แพงกว่า single split.
- ถ้า folds ไม่เคารพ dependence structure estimate จะ optimistic.
- Nested CV อาจจำเป็นเมื่อต้อง estimate performance ของ tuning procedure เอง.

## Common Mistakes

- preprocess full dataset ก่อน CV.
- ใช้ ordinary KFold กับ time series.
- เอา test set เข้า grid search.

## Cross-check / Corrections

- Lecture's 60/20/20 diagram is not CV by itself; CV is repeated fold-based resampling on training data.

## Quick Review

- **Concept:** Cross-validation (CV) ประเมิน model/hyperparameters โดย fit/validate หลาย splits ของ training data แล้ว aggregate performance เพื่อลด dependence ต่อ single holdout split.
- **จำให้ได้:** K-fold: แบ่ง training dataเป็น K folds; train K−1, validate 1 สลับกัน.
- **ใช้งาน:** hyperparameter tuning.
- **ระวัง:** preprocess full dataset ก่อน CV.

## Related Notes

- [[Train Validation Test Split]]
- [[Time Series Cross Validation]]
- [[Bias Variance Tradeoff]]
- [[K-Nearest Neighbors]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 7 - Model Training and Evaluation]] | Slides 3–5 | motivation for resampling |
| [[DADS6003 Week 9 - K-Nearest Neighbors]] | Slide 8 | tuning k with cross-validation |

## External References

- scikit-learn cross_validate: https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.cross_validate.html
- scikit-learn Model Selection: https://scikit-learn.org/stable/model_selection.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
