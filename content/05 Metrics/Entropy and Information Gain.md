---
title: "Entropy and Information Gain"
aliases:
  - Entropy
  - Information Gain
topic_number: 80
domain:
  - Data Science
  - Machine Learning
  - Information Theory
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - entropy
  - information-gain
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Entropy and Information Gain

> [!abstract] Summary
> Entropy วัด class impurity/uncertainty ใน node; Information Gain วัด entropy ที่ลดลงหลัง split และเป็น criterion สำคัญใน ID3/entropy-based trees.

## Why this concept matters

ช่วยเข้าใจว่าทำไม split ที่ทำ child nodes บริสุทธิ์ขึ้นจึงดี และเชื่อม decision trees กับ information theory.

## Core Idea

- Entropy = 0 เมื่อ node มี class เดียว.
- Binary entropy สูงสุดที่ class proportions 0.5/0.5.
- Information Gain = parent entropy − weighted child entropy.

## Mathematical Formulation / Technical Detail

\[
H(Q)=-\sum_{k=1}^{K}p_k\log_2p_k.
\]

\[
IG(Q,A)=H(Q)-\sum_v\frac{|Q_v|}{|Q|}H(Q_v).
\]

## Worked / Practical Example

Play-tennis parent entropy ≈0.94; Outlook split ให้ IG ≈0.248 มากกว่า Humidity ≈0.151 ใน lecture example จึงถูกเลือกเป็น root ภายใต้ ID3 criterion.

## When to use

- decision-tree split selection.
- information-theoretic intuition.

## Limitations / Assumptions

- Information gain มี bias ต่อ attributes ที่มีหลาย possible values; C4.5 ใช้ gain ratio เพื่อ mitigate.
- Log base เปลี่ยน scale ไม่เปลี่ยน ranking หากใช้ consistent base.

## Common Mistakes

- คิดว่า entropy เป็น classification error probability โดยตรง.
- เปรียบ IG จากคนละ dataset scale โดยไม่ context.

## Cross-check / Corrections

- ไม่พบ correction สำคัญ; เพิ่มเฉพาะ context และ implementation caveats.

## Quick Review

- **Concept:** Entropy วัด class impurity/uncertainty ใน node; Information Gain วัด entropy ที่ลดลงหลัง split และเป็น criterion สำคัญใน ID3/entropy-based trees.
- **จำให้ได้:** Entropy = 0 เมื่อ node มี class เดียว.
- **ใช้งาน:** decision-tree split selection.
- **ระวัง:** คิดว่า entropy เป็น classification error probability โดยตรง.

## Related Notes

- [[Decision Trees]]
- [[Gini Impurity]]
- [[Decision Tree Pruning]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 9-2 - Decision Trees]] | Slides 4–16 | entropy, information gain, ID3 examples |

## External References

- scikit-learn Decision Trees: https://scikit-learn.org/stable/modules/tree.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
