---
title: "Bias Variance Tradeoff"
aliases:
  - Underfitting and Overfitting
  - Bias-Variance
topic_number: 76
domain:
  - Data Science
  - Machine Learning
  - Statistics
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - bias-variance
  - overfitting
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Bias Variance Tradeoff

> [!abstract] Summary
> Bias–variance tradeoff อธิบายว่าความผิดพลาดเกิดได้จาก model ที่ rigid เกิน (high bias/underfit) หรือ sensitive ต่อ training sample เกิน (high variance/overfit); complexity และ regularization เปลี่ยนสมดุลนี้.

## Why this concept matters

เป็นกรอบวินิจฉัยว่าควรเพิ่ม capacity, regularize, เพิ่ม data หรือปรับ features แทนการ tune แบบสุ่ม.

## Core Idea

- High bias: train และ validation error สูง/ใกล้กันในหลายกรณี.
- High variance: train error ต่ำแต่ validation gap สูง.
- เพิ่ม regularization มักเพิ่ม bias และลด variance.
- เพิ่ม training data มักช่วย high-variance problems มากกว่า high-bias problems แต่ผลไม่ใช่ law แบบ absolute.

## Mathematical Formulation / Technical Detail

สำหรับ squared loss แบบ idealized:

\[
E[(Y-\hat f(X))^2]
=
\sigma^2 + Bias[\hat f(X)]^2 + Var[\hat f(X)].
\]

decomposition นี้ขึ้นกับ assumptions และ estimator; ใช้เป็น mental model มากกว่าสูตร diagnostic ทุก problem.

## Worked / Practical Example

Polynomial degree 1 อาจ underfit curved data; degree 20 อาจ memorize noise. Validation curve ช่วยหา region ที่ trade-off เหมาะกว่า.

## When to use

- เลือก model complexity/regularization.
- วิเคราะห์ train-vs-validation behavior.

## Limitations / Assumptions

- Bias/variance ไม่ได้สังเกตโดยตรงจากชุดข้อมูลเดียวอย่างสมบูรณ์.
- Deep learning behavior อาจไม่ตรง textbook U-shape อย่างง่ายเสมอ.

## Common Mistakes

- บอกว่า 'เพิ่ม data ลด variance แต่ไม่กระทบ bias' เป็นกฎตายตัว.
- สรุป overfit จาก training loss ต่ำอย่างเดียว.

## Cross-check / Corrections

- Lecture heuristic เรื่อง training data และ bias/variance ถูกเก็บเป็น guideline ไม่ใช่ universal theorem.

## Quick Review

- **Concept:** Bias–variance tradeoff อธิบายว่าความผิดพลาดเกิดได้จาก model ที่ rigid เกิน (high bias/underfit) หรือ sensitive ต่อ training sample เกิน (high variance/overfit); complexity และ regularization เปลี่ยนสมดุลนี้.
- **จำให้ได้:** High bias: train และ validation error สูง/ใกล้กันในหลายกรณี.
- **ใช้งาน:** เลือก model complexity/regularization.
- **ระวัง:** บอกว่า 'เพิ่ม data ลด variance แต่ไม่กระทบ bias' เป็นกฎตายตัว.

## Related Notes

- [[Regularized Regression]]
- [[Cross Validation]]
- [[Train Validation Test Split]]
- [[Polynomial Regression]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 6 - Regularization]] | Slides 3–9 | overfit/underfit intuition |
| [[DADS6003 Week 7 - Model Training and Evaluation]] | Slides 6–9 | bias/variance diagnosis |

## External References

- Stanford CS229 bias-variance notes index: https://cs229.stanford.edu/notes2021fall/
- scikit-learn Learning Curves: https://scikit-learn.org/stable/modules/learning_curve.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
