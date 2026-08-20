---
title: "Chi-Square Goodness-of-Fit Test"
topic_number: 150
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - hypothesis-testing
  - chi-square
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Chi-Square Goodness-of-Fit Test

> [!abstract] Summary
> Chi-square goodness-of-fit test เปรียบเทียบ observed category/bin counts กับ expected counts ภายใต้ specified probability model.

## Why this concept matters

ใช้ตรวจ categorical proportions หรือ distributional adequacy หลังจัด continuous data เป็น bins.

## Core Idea

คำนวณ expected counts $E_i=np_i$ (หรือจาก fitted distribution) แล้ววัด Pearson discrepancy $\sum (O_i-E_i)^2/E_i$. Large discrepancies ชี้ว่าข้อมูลไม่สอดคล้องกับ null model.

## Mathematical Formulation / Technical Detail

$\chi^2=\sum_{i=1}^k\frac{(O_i-E_i)^2}{E_i}$.
ถ้า probabilities specified fully, df มัก $k-1$; ถ้าประมาณ parameters จากข้อมูล df ลดลงตามจำนวน parameters ภายใต้ formulation ที่ใช้.

## Worked / Practical Example

Fair die: 6 categories, expected count = n/6. ถ้า observed counts ห่างจาก expected มาก aggregate statistic จะใหญ่.

## Assumptions / When to use

Chi-square reference distribution เป็น approximation และต้องมี expected counts เพียงพอ. Binning choice มีผลต่อ power/result.

## Common Mistakes

- ตรวจ “observed count ≥5” แทน expected count
- เปลี่ยน bins หลังดู data เพื่อให้ p-value ถูกใจ
- ใช้ df $k-1$ ทั้งที่ประมาณ distribution parameters

## Cross-check / Corrections

NIST confirms that grouping/bins affect power and chi-square approximation needs adequate sample size. Rule “ทุก cell ≥5” เป็น heuristic ไม่ใช่ universal law; canonical noteเน้น expected counts และ design context.

## Quick Review

- **Concept:** Chi-square goodness-of-fit test เปรียบเทียบ observed category/bin counts กับ expected counts ภายใต้ specified probability model.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Hypothesis Testing Fundamentals]]
- [[Student t Chi-Square and F Distributions]]
- [[Chi-Square Test of Independence and Homogeneity]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[6ChiSquare_2_68_260328_154515]] | Goodness-of-fit sections and examples | Pearson chi-square GOF |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
