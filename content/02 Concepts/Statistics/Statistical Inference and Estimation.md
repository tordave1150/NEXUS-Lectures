---
title: "Statistical Inference and Estimation"
topic_number: 135
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - inference
  - estimation
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Statistical Inference and Estimation

> [!abstract] Summary
> Statistical inference ใช้ sample เพื่อเรียนรู้ population parameter ผ่าน estimation และ hypothesis testing โดยต้องคำนึงถึง sampling uncertainty.

## Why this concept matters

เป็นกรอบรวมที่ทำให้แยก parameter, estimand, estimator, estimate และ sampling distribution ออกจากกัน.

## Core Idea

- **Estimand / parameter** $\theta$: ปริมาณของ population ที่ต้องการรู้
- **Estimator** $\hat\theta(X_1,\dots,X_n)$: random statistic
- **Estimate**: ค่าที่ estimator ให้เมื่อใส่ observed sample
- Point estimation ให้ค่าหนึ่ง; interval estimation ให้ช่วง uncertainty

## Mathematical Formulation / Technical Detail

Bias: $Bias(\hat\theta)=E[\hat\theta]-\theta$.
Standard error: $SE(\hat\theta)=\sqrt{Var(\hat\theta)}$.
MSE: $E[(\hat\theta-\theta)^2]=Var(\hat\theta)+Bias^2$.

## Worked / Practical Example

Sample mean $\bar X$ เป็น estimator ของ $\mu$; หลังเก็บข้อมูลแล้ว $\bar x=12.4$ คือ estimate.

## Assumptions / When to use

Inference ที่มีความหมายต้องมี sampling/assignment mechanism หรือ model assumptions ที่รองรับการอ้างจาก sample ไป population/process.

## Common Mistakes

- เรียก parameter ว่า statistic
- คิดว่า estimate ไม่มี uncertainty
- ตีความ unbiased ว่า estimator “แม่น” ในทุก sample

## Cross-check / Corrections

Lecture emphasizes estimation vs testing; canonical note adds standard bias/SE/MSE language to unify later resampling notes.

## Quick Review

- **Concept:** Statistical inference ใช้ sample เพื่อเรียนรู้ population parameter ผ่าน estimation และ hypothesis testing โดยต้องคำนึงถึง sampling uncertainty.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Sampling Distribution and Central Limit Theorem]]
- [[Confidence Intervals]]
- [[Hypothesis Testing Fundamentals]]
- [[Jackknife Resampling]]
- [[Bootstrap Resampling]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[2ConfidenceInterval_mod]] | Statistical inference / point and interval estimation | framework |
| [[3Jackknife_Bootstrap]] | Classical estimation review | estimator properties |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
