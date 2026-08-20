---
title: "Bayes Theorem"
aliases:
  - Bayes Rule
topic_number: 72
domain:
  - Statistics
  - Probability
  - Machine Learning
language: th
source_type:
  - lecture
tags:
  - statistics
  - probability
  - bayes
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Bayes Theorem

> [!abstract] Summary
> Bayes Theorem อัปเดต prior belief ด้วย evidence ผ่าน likelihood เพื่อได้ posterior probability และเป็นแกนของ Naive Bayes และ Bayesian inference.

## Why this concept matters

ช่วยแยกคำว่า prior, likelihood, evidence และ posterior ซึ่งมักถูกสับสน และทำให้ probabilistic classifiers เข้าใจได้จาก first principles.

## Core Idea

- Posterior \(P(Y|X)\) ∝ Likelihood \(P(X|Y)\) × Prior \(P(Y)\).
- Evidence \(P(X)\) ทำหน้าที่ normalize posterior ให้รวมเป็น 1.
- Likelihood เป็น function ของ hypothesis/class เมื่อ data ถูกตรึง; ไม่ใช่ posterior probability.

## Mathematical Formulation / Technical Detail

\[
P(Y\mid X)=\frac{P(X\mid Y)P(Y)}{P(X)}.
\]

สำหรับ mutually exclusive classes \(C_k\):
\[
P(X)=\sum_k P(X\mid C_k)P(C_k).
\]

## Worked / Practical Example

ถ้า spam prior = 0.2, phrase likelihood ใน spam = 0.6, ใน ham = 0.1: posterior ต้อง normalize ทั้งสอง class; ไม่ควรดู likelihood 0.6 แล้วสรุป posterior = 60%.

## When to use

- probabilistic classification.
- Bayesian reasoning/inference.

## Limitations / Assumptions

- Posterior ขึ้นกับ prior และ likelihood assumptions.
- Base-rate neglect เกิดเมื่อ ignore prior.

## Common Mistakes

- สับสน P(X|Y) กับ P(Y|X).
- เรียก likelihood ว่า probability ของ parameter หลังเห็น data.

## Cross-check / Corrections

- ไม่พบ correction สำคัญ; เพิ่มเฉพาะ context และ implementation caveats.

## Quick Review

- **Concept:** Bayes Theorem อัปเดต prior belief ด้วย evidence ผ่าน likelihood เพื่อได้ posterior probability และเป็นแกนของ Naive Bayes และ Bayesian inference.
- **จำให้ได้:** Posterior \(P(Y|X)\) ∝ Likelihood \(P(X|Y)\) × Prior \(P(Y)\).
- **ใช้งาน:** probabilistic classification.
- **ระวัง:** สับสน P(X|Y) กับ P(Y|X).

## Related Notes

- [[Naive Bayes]]
- [[Likelihood MLE NLL]]
- [[Probabilistic Forecasting]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 4 - Naive Bayes]] | Slides 3–5 | Bayes rule and evidence |

## External References

- scikit-learn Naive Bayes: https://scikit-learn.org/stable/modules/naive_bayes.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
