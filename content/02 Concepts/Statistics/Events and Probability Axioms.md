---
title: "Events and Probability Axioms"
topic_number: 127
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - probability
  - set-theory
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Events and Probability Axioms

> [!abstract] Summary
> Event algebra ใช้ union, intersection และ complement ร่วมกับ probability axioms เพื่อคำนวณโอกาสของเหตุการณ์ที่ซับซ้อน.

## Why this concept matters

เป็นสะพานจาก set theory ไปสู่ conditional probability, independence และ statistical models.

## Core Idea

สำหรับ events $A,B\subseteq S$:
- $A\cup B$: A หรือ B เกิด
- $A\cap B$: A และ B เกิด
- $A^c$: A ไม่เกิด
- mutually exclusive: $A\cap B=\varnothing$

## Mathematical Formulation / Technical Detail

Kolmogorov axioms:
1. $P(A)\ge 0$
2. $P(S)=1$
3. ถ้า $A_i$ mutually exclusive แบบนับได้: $P(\cup_i A_i)=\sum_iP(A_i)$

ผลตามมา:
$P(A^c)=1-P(A)$

$P(A\cup B)=P(A)+P(B)-P(A\cap B)$.

## Worked / Practical Example

ถ้า $P(A)=0.4$, $P(B)=0.5$, $P(A\cap B)=0.2$ จะได้ $P(A\cup B)=0.7$.

## Assumptions / When to use

ใช้กับ probability space ที่นิยาม event ชัดเจน. Mutually exclusive ไม่เหมือน independent.

## Common Mistakes

- ใช้ $P(A)+P(B)$ สำหรับ union ทั้งที่ events ซ้อนกัน
- คิดว่า mutually exclusive = independent
- เขียน axiom เป็น $P(A)>0$ จนตัด event ที่ probability 0 ออก

## Cross-check / Corrections

ข้อความ extraction ใน lecture ปรากฏ $P(A)>0$; canonical axiom ใช้ **non-negativity $P(A)\ge0$**. Event ที่เป็นไปไม่ได้มี probability 0 และใน continuous models event บางแบบอาจมี probability 0 แม้ไม่ใช่ logical impossibility.

## Quick Review

- **Concept:** Event algebra ใช้ union, intersection และ complement ร่วมกับ probability axioms เพื่อคำนวณโอกาสของเหตุการณ์ที่ซับซ้อน.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Probability Foundations]]
- [[Conditional Probability and Independence]]
- [[Bayes Theorem]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[1Probability_mod]] | Event operations / probability axioms sections | event algebra and axioms |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
