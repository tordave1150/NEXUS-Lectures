---
title: "Probability Foundations"
topic_number: 126
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - probability
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Probability Foundations

> [!abstract] Summary
> Probability เป็นภาษาสำหรับอธิบายความไม่แน่นอน โดยเริ่มจาก random experiment, outcome, sample space และ event.

## Why this concept matters

แนวคิด probability เป็นฐานของ statistical inference, sampling distributions, hypothesis testing, Bayesian reasoning และ probabilistic forecasting.

## Core Idea

- **Random experiment**: กระบวนการที่ผลลัพธ์ไม่ทราบแน่นอนล่วงหน้า
- **Outcome**: ผลลัพธ์หนึ่งค่าที่เกิดขึ้นจริง
- **Sample space** $S$: เซตของ outcomes ที่เป็นไปได้ทั้งหมด
- **Event** $A$: subset ของ $S$

การนิยาม sample space ให้ถูกต้องสำคัญ เพราะ probability ของ event ขึ้นกับว่าผลลัพธ์ที่เป็นไปได้ถูกกำหนดไว้อย่างไร.

## Mathematical Formulation / Technical Detail

ถ้า $A\subseteq S$, probability เป็นฟังก์ชัน $P(A)$ ที่ให้ค่าระหว่าง 0 และ 1.

ตัวอย่างการโยนลูกเต๋า: $S=\{1,2,3,4,5,6\}$ และ event ได้เลขคู่คือ $A=\{2,4,6\}$.

## Worked / Practical Example

ถ้าลูกเต๋า fair: $P(A)=3/6=0.5$. แต่ถ้าไม่ได้ระบุว่า fair จะสรุปจากจำนวน outcome อย่างเดียวไม่ได้.

## Assumptions / When to use

ใช้เมื่อกำหนด stochastic problem หรือก่อนสร้าง probability model. ต้องกำหนด experiment, sample space และ event ให้สัมพันธ์กับคำถามจริง.

## Common Mistakes

- คิดว่า outcome ที่เขียนได้ทุกตัวมีโอกาสเท่ากันโดยอัตโนมัติ
- สับสน event กับ outcome
- ใช้ sample space ที่ไม่ครอบคลุมความเป็นไปได้ทั้งหมด

## Cross-check / Corrections

Lecture แบ่ง subjective, relative-frequency และ classical approaches. Canonical note เก็บทั้งสามเป็นมุมมองการกำหนด probability แต่ classical counting ใช้ได้เฉพาะกรณี outcomes มีโอกาสเท่ากันตาม model.

## Quick Review

- **Concept:** Probability เป็นภาษาสำหรับอธิบายความไม่แน่นอน โดยเริ่มจาก random experiment, outcome, sample space และ event.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Events and Probability Axioms]]
- [[Conditional Probability and Independence]]
- [[Random Variables PMF PDF CDF]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[1Probability_mod]] | Random experiment / sample space / event sections | foundational definitions |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
