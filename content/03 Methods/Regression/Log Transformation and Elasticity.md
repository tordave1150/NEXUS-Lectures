---
title: "Log Transformation and Elasticity"
aliases:
  - Log Regression
  - Elasticity
  - Log-Log Model
topic_number: 32
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[10-NonlinearRegression_260711_160649 (1)]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Log Transformation and Elasticity

> [!abstract] Summary
> Log transformation ใช้กับ positive variablesเพื่อ stabilize variance, ลด right skew และ model proportional/multiplicative relationships; ใน log-log regression slope คือ elasticity.

## Why this concept matters

หลาย business effectsเป็นเปอร์เซ็นต์มากกว่าหน่วยคงที่ เช่น advertisingเพิ่ม 1%สัมพันธ์กับ salesเปลี่ยนเป็นเปอร์เซ็นต์.

## Core Idea

- Log-log: coefficient $\beta_1$ คือ elasticityโดยตรง.
- Log-level: x เพิ่ม 1 unitทำให้ y เปลี่ยนประมาณ $100\beta_1$% เมื่อ coefficientเล็ก.
- Level-log: x เพิ่ม 1% ทำให้ y เปลี่ยนประมาณ $\beta_1/100$ units.
- Back-transform predictionsต้องแยก medianกับ mean.

## Mathematical Formulation / Technical Detail

Log-log:

$$
\log y=\beta_0+\beta_1\log x+\varepsilon.
$$

ดังนั้น

$$
\frac{\partial\log y}{\partial\log x}=\beta_1.
$$

การเพิ่ม $x$ 1% เชื่อมกับ $y$ เพิ่มประมาณ $\beta_1$% สำหรับ small changes.

## Worked / Practical Example

ถ้า $\log Sales=6.392+0.0953\log Advertising$ การเพิ่ม advertising 1%สัมพันธ์กับ expected/conditional log responseประมาณ 0.0953% changeใน sales ตาม model; เป็น association ไม่ใช่ causal elasticityโดยอัตโนมัติ.

## Assumptions and Interpretation

- Log requires positive values unlessใช้ alternative transform.
- Interpretationของ meanบน original scaleขึ้นกับ error distribution.

## When to use

- multiplicative relationships.
- heteroskedastic dataที่ varianceเพิ่มตาม level.
- elasticity interpretation.

## When not to use / Limitations

- zero/negative valuesโดยไม่มี justified transform.
- เมื่อ additive effectใน original unitsสำคัญและ logทำให้ communicationยาก.

## Common Mistakes

- บอกว่า log(y+1) เป็นวิธีถูกต้องเสมอสำหรับ zero.
- back-transformด้วย expแล้วเรียก expected meanเสมอ.
- ตีความ elasticityเป็น causality.

## Quick Review

- **Concept:** Log transformation ใช้กับ positive variablesเพื่อ stabilize variance, ลด right skew และ model proportional/multiplicative relationships; ใน log-log regression slope คือ elasticity.
- **สิ่งที่ต้องจำ:** Log-log: coefficient $\beta_1$ คือ elasticityโดยตรง.
- **การใช้งาน:** multiplicative relationships.
- **ข้อควรระวัง:** บอกว่า log(y+1) เป็นวิธีถูกต้องเสมอสำหรับ zero.

## Related Notes

- [[Transformations and Adjustments]]
- [[Nonlinear Regression]]
- [[Prediction Intervals]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[10-NonlinearRegression_260711_160649 (1)]] | Log transformation / coefficient interpretation section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `10-NonlinearRegression_260711_160649 (1).pdf` — Log transformation / coefficient interpretation section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
