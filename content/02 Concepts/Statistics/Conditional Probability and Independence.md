---
title: "Conditional Probability and Independence"
topic_number: 128
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - probability
  - independence
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Conditional Probability and Independence

> [!abstract] Summary
> Conditional probability ปรับ probability เมื่อมีข้อมูลว่า event อื่นเกิดแล้ว ส่วน independence หมายถึงข้อมูลของ event หนึ่งไม่เปลี่ยน probability ของอีก event.

## Why this concept matters

แนวคิดนี้เป็นฐานของ Bayes theorem, likelihood, contingency tables และ probabilistic graphical reasoning.

## Core Idea

Conditional probability:
$P(A|B)$ อ่านว่า probability ของ A เมื่อทราบว่า B เกิด.

Independence ต้องตรวจจาก factorization ของ joint probability ไม่ใช่จากการที่ events ไม่ซ้อนกัน.

## Mathematical Formulation / Technical Detail

$P(A|B)=\frac{P(A\cap B)}{P(B)}$, เมื่อ $P(B)>0$.

A และ B independent ถ้า
$P(A\cap B)=P(A)P(B)$
หรือเทียบเท่า $P(A|B)=P(A)$ เมื่อ conditional probability นิยามได้.

## Worked / Practical Example

ถ้าเหตุการณ์ฝนตกมี $P(R)=0.3$ และ $P(R|C)=0.3$ เมื่อทราบว่าโยนเหรียญออกหัว C, เหตุการณ์ทั้งสองสอดคล้องกับ independence.

## Assumptions / When to use

ต้องระบุ conditioning event ให้ชัด และแยก statistical independence จาก causal independence.

## Common Mistakes

- สับสน $P(A|B)$ กับ $P(B|A)$
- สรุป independent เพราะ correlation = 0
- สรุป independent เพราะ events mutually exclusive

## Cross-check / Corrections

No major source contradiction; note adds the standard factorization definition so independence can be checked formally.

## Quick Review

- **Concept:** Conditional probability ปรับ probability เมื่อมีข้อมูลว่า event อื่นเกิดแล้ว ส่วน independence หมายถึงข้อมูลของ event หนึ่งไม่เปลี่ยน probability ของอีก event.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Probability Foundations]]
- [[Events and Probability Axioms]]
- [[Bayes Theorem]]
- [[Chi-Square Test of Independence and Homogeneity]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[1Probability_mod]] | Probability properties and event sections | conditional/event reasoning |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
