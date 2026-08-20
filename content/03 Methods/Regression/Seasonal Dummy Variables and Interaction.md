---
title: "Seasonal Dummy Variables and Interaction"
aliases:
  - Seasonal Dummies
  - Interaction Terms
topic_number: 22
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[07-Regression-Categorical_260629_205921]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Seasonal Dummy Variables and Interaction

> [!abstract] Summary
> Seasonal dummies model fixed seasonal intercept shifts; interaction termsทำให้ effect ของ predictor หนึ่งขึ้นกับค่าของอีก predictor.

## Why this concept matters

Regression can encode calendar seasonalityและ heterogeneous relationshipsได้โดยตรง แต่ต้องเข้าใจ baseline และจำนวน parameters.

## Core Idea

- Monthly seasonalityใช้ 11 dummies + intercept; quarterlyใช้ 3.
- Seasonal dummy assumes seasonal patternคงรูป (fixed effects) ตลอดเวลา เว้นแต่เพิ่ม interactions/time variation.
- Interaction $xD$ ทำให้ slope ของ $x$ ต่างระหว่าง categories.
- Main effects ต้องตีความ ณ baseline/zero ของ interacting variable.

## Mathematical Formulation / Technical Detail

Quarterly dummies:

$$
y_t=\beta_0+\beta_2D_{Q2,t}+\beta_3D_{Q3,t}+\beta_4D_{Q4,t}+\varepsilon_t
$$

โดย Q1 baseline.

Interaction:

$$
y=\beta_0+\beta_1x+\beta_2D+\beta_3(xD)+\varepsilon.
$$

Slope baseline = $\beta_1$; slope D=1 = $\beta_1+\beta_3$.

## Worked / Practical Example

ถ้า promotion effect $\beta_1=5$ ใน non-holiday และ interaction holiday×promotion = 3, effect ของ promotion during holiday = 8 units ต่อหนึ่งหน่วย promotion.

## Assumptions and Interpretation

- Dummy seasonalityเหมาะเมื่อ seasonal periodไม่ใหญ่มาก.
- Interactionเพิ่ม flexibilityแต่เพิ่ม varianceและ interpretation complexity.

## When to use

- calendar effects.
- แตก slope ตาม segment/regime.
- benchmark harmonic regressionสำหรับ short seasonality.

## When not to use / Limitations

- long seasonal period เช่น 365 จะใช้ dummiesจำนวนมาก.
- changing seasonality อาจเหมาะกับ STL/MSTL.

## Common Mistakes

- ลืม main effectsแต่ใส่ interactionโดยไม่มีเหตุผลเชิงโมเดล.
- ตีความ main effectโดยไม่ระบุ baseline.
- ใช้ dummy 12 ตัวพร้อม intercept.

## Quick Review

- **Concept:** Seasonal dummies model fixed seasonal intercept shifts; interaction termsทำให้ effect ของ predictor หนึ่งขึ้นกับค่าของอีก predictor.
- **สิ่งที่ต้องจำ:** Monthly seasonalityใช้ 11 dummies + intercept; quarterlyใช้ 3.
- **การใช้งาน:** calendar effects.
- **ข้อควรระวัง:** ลืม main effectsแต่ใส่ interactionโดยไม่มีเหตุผลเชิงโมเดล.

## Related Notes

- [[Multi-level Categorical Regression]]
- [[Harmonic Regression]]
- [[Dynamic Harmonic Regression]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[07-Regression-Categorical_260629_205921]] | Seasonal dummy variables / interaction section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `07-Regression-Categorical_260629_205921.pdf` — Seasonal dummy variables / interaction section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
