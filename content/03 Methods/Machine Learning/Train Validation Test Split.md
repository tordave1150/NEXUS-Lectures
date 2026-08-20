---
title: "Train Validation Test Split"
aliases:
  - Holdout Split
  - Train Val Test
topic_number: 74
domain:
  - Data Science
  - Machine Learning
  - Model Evaluation
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - evaluation
  - data-splitting
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Train Validation Test Split

> [!abstract] Summary
> Train/validation/test split แยกข้อมูลตามบทบาท: train ใช้ fit parameters, validation ใช้ model/hyperparameter decisions, test ใช้ final unbiased-ish evaluation หลัง decisions จบ.

## Why this concept matters

การแยกบทบาทป้องกันเรา optimize โดยตรงต่อข้อมูลที่ใช้รายงาน final performance.

## Core Idea

- Train: fit model/preprocessing parameters.
- Validation: select features, hyperparameters, thresholds, architectures.
- Test: เปิดเมื่อ design choices จบ; ไม่ใช้ iterative tuning.
- Stratification/group/time-aware splitting ต้องใช้เมื่อ sampling structure ต้องการ.

## Mathematical Formulation / Technical Detail

ไม่มีสัดส่วน universal เช่น 60/20/20 หรือ 80/20. สัดส่วนควรขึ้นกับ \(n\), tuning complexity และ need for precise final estimate.

หลักการสำคัญกว่าเปอร์เซ็นต์:
\[
D_{\text{train}},D_{\text{val}},D_{\text{test}}
\text{ ต้องแยกตาม intended information flow.}
\]

## Worked / Practical Example

มี 10,000 labeled rows อาจใช้ 70/15/15. หาก data น้อย อาจใช้ cross-validation ภายใน training set แล้ว hold out test เล็กหนึ่งชุดแทน.

## When to use

- supervised ML evaluation.
- ก่อน cross-validation/hyperparameter tuning.

## Limitations / Assumptions

- Repeatedly checking test results ทำให้ test กลายเป็น validation set.
- Random split ไม่เหมาะกับ grouped/time-dependent data.

## Common Mistakes

- คิดว่า 80/20 เป็นมาตรฐานตายตัว.
- fit scaler/feature selector ด้วย validation+test.
- เรียก 60/20/20 split ว่า cross-validation.

## Cross-check / Corrections

- Lecture เรียก 60/20/20 ว่า cross-validation; canonical note แก้ว่าเป็น three-way holdout. Cross-validation ต้อง resample/fold training data หลายครั้ง.

## Quick Review

- **Concept:** Train/validation/test split แยกข้อมูลตามบทบาท: train ใช้ fit parameters, validation ใช้ model/hyperparameter decisions, test ใช้ final unbiased-ish evaluation หลัง decisions จบ.
- **จำให้ได้:** Train: fit model/preprocessing parameters.
- **ใช้งาน:** supervised ML evaluation.
- **ระวัง:** คิดว่า 80/20 เป็นมาตรฐานตายตัว.

## Related Notes

- [[Cross Validation]]
- [[Bias Variance Tradeoff]]
- [[Machine Learning Workflow and MLOps]]
- [[Time Series Cross Validation]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 7 - Model Training and Evaluation]] | Slides 3–5 | holdout and three-way split |

## External References

- scikit-learn train_test_split: https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html
- scikit-learn Model Selection: https://scikit-learn.org/stable/model_selection.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
