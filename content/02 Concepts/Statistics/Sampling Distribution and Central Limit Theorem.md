---
title: "Sampling Distribution and Central Limit Theorem"
topic_number: 133
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - sampling
  - clt
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Sampling Distribution and Central Limit Theorem

> [!abstract] Summary
> Sampling distribution คือ distribution ของ statistic ภายใต้การสุ่มตัวอย่างซ้ำ; CLT อธิบายว่า standardized sample mean มีแนวโน้มเข้าใกล้ normal ภายใต้เงื่อนไขที่เหมาะสมเมื่อ sample size เพิ่ม.

## Why this concept matters

เป็นกลไกที่เชื่อม sample statistic กับ standard error, confidence interval และ hypothesis test.

## Core Idea

อย่าสับสน **distribution of raw data** กับ **sampling distribution of a statistic**. Statistic เช่น $\bar X$ เปลี่ยนค่าจาก sample หนึ่งไปอีก sample หนึ่ง จึงมี distribution ของตัวเอง.

## Mathematical Formulation / Technical Detail

ถ้า $X_i$ iid มี $E[X_i]=\mu$ และ $Var(X_i)=\sigma^2<\infty$:

$E[\bar X]=\mu$, $Var(\bar X)=\sigma^2/n$.

CLT: $\frac{\bar X-\mu}{\sigma/\sqrt n}\Rightarrow N(0,1)$ เมื่อ $n$ โต ภายใต้ regularity conditions.

## Worked / Practical Example

แม้ raw data เบ้ การแจกแจงของ sample mean มักสมมาตร/ใกล้ normal มากขึ้นเมื่อ $n$ เพิ่ม แต่ rate ขึ้นกับความเบ้, heavy tails และ dependence.

## Assumptions / When to use

Classical iid CLT ต้องการ independent/identically distributed และ finite variance ในรูปพื้นฐาน; dependent-data CLTs มีเงื่อนไขต่างออกไป.

## Common Mistakes

- พูดว่า CLT ทำให้ “ข้อมูล” เป็น normal
- ใช้ $n=30$ เป็นกฎตายตัว
- ลืม dependence หรือ infinite-variance/heavy-tail cases

## Cross-check / Corrections

Canonical note keeps the lecture intuition but avoids a universal sample-size cutoff: CLT quality is distribution- and design-dependent.

## Quick Review

- **Concept:** Sampling distribution คือ distribution ของ statistic ภายใต้การสุ่มตัวอย่างซ้ำ; CLT อธิบายว่า standardized sample mean มีแนวโน้มเข้าใกล้ normal ภายใต้เงื่อนไขที่เหมาะสมเมื่อ sample size เพิ่ม.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Normal Distribution and Standardization]]
- [[Statistical Inference and Estimation]]
- [[Confidence Intervals]]
- [[Hypothesis Testing Fundamentals]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[1Probability_mod]] | Sampling distributions / CLT sections | sampling distribution and asymptotic normality |
| [[2ConfidenceInterval_mod]] | Distribution of statistics / CLT review | CI foundation |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
