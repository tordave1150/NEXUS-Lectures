---
title: "Type I Type II Errors and Statistical Power"
topic_number: 145
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - inference
  - power
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Type I Type II Errors and Statistical Power

> [!abstract] Summary
> Type I error คือ reject $H_0$ ทั้งที่จริง, Type II error คือ fail to reject $H_0$ ทั้งที่ false; power คือ probability ที่ test ตรวจพบ effect ภายใต้ alternative ที่กำหนด.

## Why this concept matters

ช่วยให้เข้าใจว่าการควบคุม false positives มี trade-off กับ false negatives และ sample size.

## Core Idea

$\alpha$ เป็น design-level probability ของ Type I error ภายใต้ $H_0$. $\beta$ ขึ้นกับ specific alternative/effect size, variability, n และ test. Power = $1-\beta$.

## Mathematical Formulation / Technical Detail

$\alpha=P(\text{reject }H_0\mid H_0\text{ true})$.
$\beta(\theta)=P(\text{fail to reject }H_0\mid \theta\in H_1)$.
Power$(\theta)=1-\beta(\theta)$.

## Worked / Practical Example

เพิ่ม sample size โดยทั่วไปทำให้ SE ลดลงและสามารถเพิ่ม power ต่อ effect size เดิม โดยไม่จำเป็นต้องเพิ่ม $\alpha$.

## Assumptions / When to use

Power ต้องอ้างอิง effect size/alternative; ไม่มี “power ของ test” เป็นตัวเลขเดียวโดยไม่ระบุ scenario.

## Common Mistakes

- ตีความ $\alpha$ เป็น probability ว่า $H_0$ จริง
- คิดว่า $\beta$ คงที่ทุก alternative
- ใช้ observed p-value เป็น power

## Cross-check / Corrections

No major source correction; note clarifies conditional nature of $\alpha,\beta$ and that power is a function of the alternative/effect size.

## Quick Review

- **Concept:** Type I error คือ reject $H_0$ ทั้งที่จริง, Type II error คือ fail to reject $H_0$ ทั้งที่ false; power คือ probability ที่ test ตรวจพบ effect ภายใต้ alternative ที่กำหนด.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Hypothesis Testing Fundamentals]]
- [[p-values Critical Values and Tail Direction]]
- [[Bias Variance Tradeoff]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[4TestHypo]] | Error table / significance / power sections | Type I, II and power |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
