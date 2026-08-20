---
title: "Bernoulli and Binomial Distribution"
topic_number: 131
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - probability
  - binomial
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Bernoulli and Binomial Distribution

> [!abstract] Summary
> Bernoulli model ใช้กับ trial ที่มีสอง outcome; Binomial model นับจำนวน successes จาก $n$ independent Bernoulli trials ที่มี success probability คงที่ $p$.

## Why this concept matters

เป็นฐานของ proportion inference, classification likelihood และ count-of-success problems.

## Core Idea

Bernoulli: $X\in\{0,1\}$.
Binomial: $X=\sum_{i=1}^{n}X_i$, เมื่อ $X_i$ iid Bernoulli($p$).

## Mathematical Formulation / Technical Detail

$P(X=x)=\binom{n}{x}p^x(1-p)^{n-x}$, $x=0,\dots,n$.

$E[X]=np$, $Var(X)=np(1-p)$.

Sample proportion $\hat p=X/n$ มี $E[\hat p]=p$ และ $Var(\hat p)=p(1-p)/n$.

## Worked / Practical Example

ถ้าโยน fair coin 10 ครั้ง จำนวนหัว $X\sim Binomial(10,0.5)$; $P(X=5)=\binom{10}{5}0.5^{10}$.

## Assumptions / When to use

ต้องมีจำนวน trial คงที่, two-outcome coding, independence และ constant $p$ สำหรับ textbook binomial model.

## Common Mistakes

- ใช้ binomial เมื่อ $p$ เปลี่ยนตาม trial
- sampling without replacement จาก finite population แล้วถือ independent โดยไม่ตรวจเงื่อนไข
- ใช้ normal approximation โดยไม่ดู expected successes/failures

## Cross-check / Corrections

Lecture ใช้ข้อความว่า normal approximation ดีเมื่อ $n\to\infty$ และ $p\to0.5$; canonical note ไม่ถือ $p$ ต้องเข้าใกล้ 0.5 เป็นเงื่อนไขจำเป็น แต่ความแม่นขึ้นกับ $np$ และ $n(1-p)$ ว่าเพียงพอสำหรับ approximation หรือไม่.

## Quick Review

- **Concept:** Bernoulli model ใช้กับ trial ที่มีสอง outcome; Binomial model นับจำนวน successes จาก $n$ independent Bernoulli trials ที่มี success probability คงที่ $p$.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Random Variables PMF PDF CDF]]
- [[Normal Distribution and Standardization]]
- [[Confidence Interval for a Population Proportion]]
- [[One-Sample Mean and Proportion Tests]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[1Probability_mod]] | Bernoulli/binomial and normal-approximation sections | model and sampling behavior |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
