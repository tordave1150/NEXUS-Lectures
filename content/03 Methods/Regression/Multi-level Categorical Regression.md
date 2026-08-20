---
title: "Multi-level Categorical Regression"
aliases:
  - Multi-level Dummy Variables
  - Reference Coding
topic_number: 21
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

# Multi-level Categorical Regression

> [!abstract] Summary
> Categorical predictor ที่มี $m$ levels ใช้ $m-1$ dummy variables เมื่อ model มี intercept โดยเหลือหนึ่ง level เป็น reference/baseline.

## Why this concept matters

Reference coding ทำให้ design matrix full rank และ coefficients ตีความเป็น difference จาก baseline.

## Core Idea

- $m$ levels → $m-1$ indicators + intercept.
- ทุก dummy =0 หมายถึง baseline.
- แต่ละ dummy coefficientเปรียบ categoryนั้นกับ baseline conditional on other predictors.
- สามารถ relevel เพื่อให้ comparison ที่สนใจอ่านง่ายขึ้น.

## Mathematical Formulation / Technical Detail

ถ้า Education มี 5 levels และ level 3 เป็น baseline:

$$
\hat y=\beta_0+\beta_1x+\gamma_1D_1+\gamma_2D_2+\gamma_4D_4+\gamma_5D_5.
$$

ไม่มี $D_3$ เพราะมันถูกแทนโดย intercept/reference.

## Worked / Practical Example

ถ้า $\gamma_5=7005$ แปลว่า education level 5 มี predicted outcome สูงกว่า level 3 ประมาณ 7005 เมื่อ covariates อื่นคงที่.

## Assumptions and Interpretation

- Reference coding เป็นหนึ่งใน contrast schemes; effect coding/orthogonal contrastsอาจใช้ได้เช่นกัน.
- Coefficient interpretationขึ้นกับ contrast scheme.

## When to use

- nominal factor หลายกลุ่ม.
- season/month/day categories เมื่อไม่ต้องการ smooth periodic assumption.

## When not to use / Limitations

- ถ้ามี levels จำนวนมากและข้อมูลน้อยอาจเกิด high variance.
- unknown/new categoriesตอน productionต้องวาง policy.

## Common Mistakes

- คิดว่าต้องสร้าง $m$ dummies เสมอ.
- ลืมบอก baseline.
- ตีความ ordered factorเหมือน nominalโดยไม่พิจารณา structure.

## Quick Review

- **Concept:** Categorical predictor ที่มี $m$ levels ใช้ $m-1$ dummy variables เมื่อ model มี intercept โดยเหลือหนึ่ง level เป็น reference/baseline.
- **สิ่งที่ต้องจำ:** $m$ levels → $m-1$ indicators + intercept.
- **การใช้งาน:** nominal factor หลายกลุ่ม.
- **ข้อควรระวัง:** คิดว่าต้องสร้าง $m$ dummies เสมอ.

## Related Notes

- [[Categorical and Dummy Variables]]
- [[Seasonal Dummy Variables and Interaction]]
- [[Regularized Regression]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[07-Regression-Categorical_260629_205921]] | Multi-level indicator variables section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `07-Regression-Categorical_260629_205921.pdf` — Multi-level indicator variables section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
