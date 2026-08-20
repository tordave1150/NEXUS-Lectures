---
title: "p-values Critical Values and Tail Direction"
topic_number: 146
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - inference
  - p-value
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# p-values Critical Values and Tail Direction

> [!abstract] Summary
> p-value วัดความ extreme ของข้อมูลภายใต้ null model ตาม test statistic และ alternative ที่กำหนด; critical value เป็น threshold ที่ทำให้ rejection region มีขนาด $\alpha$.

## Why this concept matters

ช่วยแยก evidence measure จาก effect size และป้องกันการตีความ p-value ผิด.

## Core Idea

One-sided test ใช้ tail ที่สอดคล้องกับ directional alternative; two-sided test พิจารณาความ extreme ทั้งสองทิศตาม definition ของ test.

## Mathematical Formulation / Technical Detail

p-value = probability ภายใต้ $H_0$ ของผลลัพธ์/test statistic ที่อย่างน้อย extreme เท่าที่สังเกต ตาม alternative.
Reject rule: p ≤ $\alpha$ หรือ statistic อยู่ใน critical region.

## Worked / Practical Example

p=0.03 ที่ $\alpha=0.05$ หมายถึง observed evidence ขัดกับ null มากพอตาม decision threshold; ไม่ได้หมายถึง “$H_0$ มีโอกาส 3%”.

## Assumptions / When to use

Tail direction ควรกำหนดก่อนดู data. Multiple testing หรือ adaptive analysis เปลี่ยน error control และต้องจัดการเพิ่มเติม.

## Common Mistakes

- p-value = $P(H_0|data)$
- p-value เล็ก = effect ใหญ่
- two-sided p = one-sided p ×2 เสมอทุก test/distribution

## Cross-check / Corrections

Canonical note follows standard null-distribution interpretation and avoids “acceptance region” wordingที่อาจชวนคิดว่าพิสูจน์ $H_0$ ได้; ใช้ non-rejection region เมื่อเหมาะสม.

## Quick Review

- **Concept:** p-value วัดความ extreme ของข้อมูลภายใต้ null model ตาม test statistic และ alternative ที่กำหนด; critical value เป็น threshold ที่ทำให้ rejection region มีขนาด $\alpha$.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Hypothesis Testing Fundamentals]]
- [[Type I Type II Errors and Statistical Power]]
- [[Confidence Intervals]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[4TestHypo]] | Critical region / critical value / one- vs two-tailed sections | decision and p-value interpretation |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
