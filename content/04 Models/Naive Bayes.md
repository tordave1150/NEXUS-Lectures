---
title: "Naive Bayes"
aliases:
  - Naive Bayes Classifier
  - Gaussian Naive Bayes
  - Categorical Naive Bayes
topic_number: 73
domain:
  - Data Science
  - Machine Learning
  - Statistics
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - classification
  - naive-bayes
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Naive Bayes

> [!abstract] Summary
> Naive Bayes เป็น probabilistic classifier ที่ใช้ Bayes theorem พร้อมสมมติว่า features conditionally independent เมื่อกำหนด class; assumption แรงแต่ model เร็วและเป็น baseline ที่ดีในหลายงาน.

## Why this concept matters

เป็นตัวอย่างชัดเจนของการแลก modeling assumption กับ computational simplicity และช่วยเชื่อม probability theory กับ classification.

## Core Idea

- Classification rule: maximize prior × product of class-conditional feature likelihoods.
- GaussianNB ใช้ Gaussian likelihood ต่อ continuous feature conditional on class.
- Categorical/Multinomial variants ใช้ likelihood ที่เหมาะกับ feature type.
- Laplace/Lidstone smoothing ป้องกัน zero conditional probabilities.

## Mathematical Formulation / Technical Detail

\[
\hat y=\arg\max_y P(y)\prod_{j=1}^{d}P(x_j\mid y).
\]

Gaussian feature:
\[
P(x_j\mid y)=\frac{1}{\sqrt{2\pi\sigma_{jy}^2}}
\exp\left[-\frac{(x_j-\mu_{jy})^2}{2\sigma_{jy}^2}\right].
\]

Categorical Laplace smoothing:
\[
\hat P(x_j=t\mid y=c)=\frac{N_{tjc}+\alpha}{N_c+\alpha K_j}.
\]

## Worked / Practical Example

Lecture example (Drew, No, Brown, Short):
- Male likelihood×prior = \(1/108\approx0.00926\)
- Female likelihood×prior = \(0.012\)

Normalize:
\[
P(M|x)\approx 0.435,\quad P(F|x)\approx0.565.
\]

ดังนั้นจากตัวเลขที่ lecture ให้ class ควรเป็น **Female**, ไม่ใช่ Male.

## When to use

- text/categorical baselines, spam, document classification.
- small data หรือ need fast probabilistic baseline.

## Limitations / Assumptions

- Conditional independence มักไม่จริงและ probability calibration อาจไม่ดี.
- GaussianNB assumption ต้องตรวจ distributional fit แบบ pragmatic.
- Products ของ probabilities อาจ underflow จึงใช้ log probabilities.

## Common Mistakes

- คูณ probabilities โดยไม่ใช้ log ใน high dimensions.
- ใช้ GaussianNB กับ categorical codes อย่างไม่มี distribution rationale.
- เชื่อ worked answer แม้ arithmetic ไม่สอดคล้อง.

## Cross-check / Corrections

- Slides 9–11 มี decimal error 0.0092 → 0.092 และ final class ผิด; canonical derivation แก้เป็น Female ≈56.5%.

## Quick Review

- **Concept:** Naive Bayes เป็น probabilistic classifier ที่ใช้ Bayes theorem พร้อมสมมติว่า features conditionally independent เมื่อกำหนด class; assumption แรงแต่ model เร็วและเป็น baseline ที่ดีในหลายงาน.
- **จำให้ได้:** Classification rule: maximize prior × product of class-conditional feature likelihoods.
- **ใช้งาน:** text/categorical baselines, spam, document classification.
- **ระวัง:** คูณ probabilities โดยไม่ใช้ log ใน high dimensions.

## Related Notes

- [[Bayes Theorem]]
- [[Logistic Regression]]
- [[Classification Metrics]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 4 - Naive Bayes]] | Slides 2–14 | Bayes derivation, Naive assumption, worked example, Gaussian/Laplace |

## External References

- scikit-learn Naive Bayes: https://scikit-learn.org/stable/modules/naive_bayes.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
