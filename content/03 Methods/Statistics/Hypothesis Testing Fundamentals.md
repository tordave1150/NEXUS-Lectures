---
title: "Hypothesis Testing Fundamentals"
topic_number: 144
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - inference
  - hypothesis-testing
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Hypothesis Testing Fundamentals

> [!abstract] Summary
> Hypothesis testing ประเมินว่าข้อมูลขัดแย้งกับ null hypothesis มากเพียงใดผ่าน test statistic และ sampling/null distribution; การไม่ปฏิเสธ $H_0$ ไม่เท่ากับพิสูจน์ว่า $H_0$ จริง.

## Why this concept matters

เป็น framework กลางของ t-tests, proportion tests, chi-square, ANOVA, correlation tests และ permutation tests.

## Core Idea

กำหนด $H_0$ และ $H_1$ ก่อนดูผล, เลือก statistic ที่มี behavior ภายใต้ $H_0$ ทราบหรือประมาณได้, แล้ววัด extremeness ของ observed statistic.

## Mathematical Formulation / Technical Detail

Decision rule อาจเขียนผ่าน critical region หรือ p-value. ที่ระดับ $\alpha$, reject $H_0$ เมื่อ p-value ≤ $\alpha$ ตาม convention ที่กำหนดล่วงหน้า.

## Worked / Practical Example

ทดสอบ $H_0:\mu=100$ vs $H_1:\mu\ne100$. ถ้า sample mean ห่างจาก 100 มากเมื่อเทียบกับ SE จะได้ test statistic magnitude ใหญ่และ p-value เล็ก.

## Assumptions / When to use

Hypotheses ต้องสัมพันธ์กับ scientific question และ test assumptions. Equality typically belongs in null for standard point-null testing.

## Common Mistakes

- พูด “accept $H_0$” แทน “fail to reject”
- เขียน direction ของ $H_0/H_1$ ไม่ตรง research claim
- เลือก one-sided test หลังเห็นข้อมูล

## Cross-check / Corrections

Lecture มีตัวอย่างบางบรรทัดที่ทิศของ $H_0/H_1$ ไม่สอดคล้องกับข้อความวิจัย (เช่น claim “มากกว่า” แต่ alternative แสดง “น้อยกว่า”). Canonical note ใช้ principle ว่า alternative ต้อง encode research direction และ null ต้องเป็น complement ที่รวม boundary/equality ตาม test definition.

## Quick Review

- **Concept:** Hypothesis testing ประเมินว่าข้อมูลขัดแย้งกับ null hypothesis มากเพียงใดผ่าน test statistic และ sampling/null distribution; การไม่ปฏิเสธ $H_0$ ไม่เท่ากับพิสูจน์ว่า $H_0$ จริง.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Type I Type II Errors and Statistical Power]]
- [[p-values Critical Values and Tail Direction]]
- [[Confidence Intervals]]
- [[Permutation Tests]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[4TestHypo]] | Hypothesis / null-alternative / testing logic sections | testing framework |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
