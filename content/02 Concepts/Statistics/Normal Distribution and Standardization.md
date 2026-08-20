---
title: "Normal Distribution and Standardization"
topic_number: 132
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - probability
  - normal-distribution
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Normal Distribution and Standardization

> [!abstract] Summary
> Normal distribution เป็น continuous symmetric distribution ที่กำหนดด้วย mean $\mu$ และ variance $\sigma^2$; standardization เปลี่ยนค่าเป็น z-score เพื่อเทียบกับ $N(0,1)$.

## Why this concept matters

Normal model เป็นแกนของ classical inference, CLT approximations และ regression/ANOVA error models.

## Core Idea

ถ้า $X\sim N(\mu,\sigma^2)$ จะมี bell-shaped symmetric density. Standardization ใช้ระยะห่างจาก mean วัดเป็นหน่วยของ standard deviation.

## Mathematical Formulation / Technical Detail

$Z=\frac{X-\mu}{\sigma}\sim N(0,1)$.

สำหรับ sample mean จาก normal population: $\bar X\sim N(\mu,\sigma^2/n)$.

## Worked / Practical Example

ถ้า $X\sim N(100,15^2)$ และสังเกต $X=130$, z-score = $(130-100)/15=2$.

## Assumptions / When to use

Normality เป็น model assumption ไม่ใช่สิ่งที่เกิดกับข้อมูลทุกชุด. การใช้ z/t inference ต้องพิจารณา sampling design และ sample size ด้วย.

## Common Mistakes

- คิดว่า z-score ต้องอยู่ใน [-3,3]
- คิดว่า symmetric data = normal โดยอัตโนมัติ
- ใช้ population SD กับ sample SD สลับกัน

## Cross-check / Corrections

No major correction beyond emphasizing that normality is a model assumption and z-score is unbounded.

## Quick Review

- **Concept:** Normal distribution เป็น continuous symmetric distribution ที่กำหนดด้วย mean $\mu$ และ variance $\sigma^2$; standardization เปลี่ยนค่าเป็น z-score เพื่อเทียบกับ $N(0,1)$.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Sampling Distribution and Central Limit Theorem]]
- [[Student t Chi-Square and F Distributions]]
- [[Confidence Interval for a Population Mean]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[1Probability_mod]] | Normal distribution / standard normal sections | distribution and z standardization |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
