---
title: "Transformations and Adjustments"
aliases:
  - Time Series Transformations
  - Box-Cox Transformation
  - Data Adjustments
topic_number: 6
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[02-TSDecomposition]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Transformations and Adjustments

> [!abstract] Summary
> Transformations เปลี่ยน scale ของข้อมูลเพื่อทำ variance/pattern ให้ model ง่ายขึ้น ส่วน adjustments แก้ผลของ calendar, population, inflation หรือ known structural effects ก่อน modeling.

## Why this concept matters

Model มักทำงานดีขึ้นเมื่อ variance คงที่ขึ้นและ pattern เป็น additive มากขึ้น แต่ต้อง back-transform forecast อย่างระมัดระวัง.

## Core Idea

- Log transform มีประโยชน์เมื่อ variation เพิ่มตาม level และข้อมูลเป็นบวก.
- Box-Cox เป็น family ที่รวม log และ power transforms.
- Calendar adjustment เช่น trading days หรือ working days ต้องสะท้อน business process.
- การ back-transform mean forecast อาจมี bias เพราะ nonlinear transformation.

## Mathematical Formulation / Technical Detail

Box-Cox transform แบบมาตรฐาน:

$$
w_t=
\begin{cases}
\log(y_t), & \lambda=0,\\
\frac{y_t^\lambda-1}{\lambda}, & \lambda\ne0.
\end{cases}
$$

สำหรับ lognormal case หากโมเดลบน log-scale ให้ mean $\mu$ และ variance $\sigma^2$:

$$
E(Y)=\exp(\mu+\sigma^2/2)
$$

ไม่ใช่เพียง $\exp(\mu)$.

## Worked / Practical Example

ยอดขายที่มี standard deviation เพิ่มตาม mean อาจ log-transform ก่อน fit model. หลัง forecast บน log scale ถ้าต้องการ median forecast ใช้ exponentiate ได้ตรง ๆ แต่ถ้าต้องการ mean อาจต้อง bias adjustment.

## Assumptions and Interpretation

- Transformation ต้อง fit/เลือกจาก training data และใช้เหมือนกันกับ future/test.
- การตีความ coefficients ต้องเปลี่ยนตาม transformed scale.

## When to use

- ใช้ stabilize variance.
- ใช้ลด right skew.
- ใช้ทำ multiplicative pattern ให้ใกล้ additive.

## When not to use / Limitations

- Log ใช้ไม่ได้ตรง ๆ กับค่าติดลบ; log(y+1) เป็น pragmatic trick ไม่ใช่ universal solution.
- อย่าปรับข้อมูลโดยใช้ future information.

## Common Mistakes

- คิดว่า back-transform point forecast แล้วได้ mean เสมอ.
- ใช้ log(y+1) โดยไม่พิจารณาความหมายของหน่วยและ zero.
- ปรับ inflation/calendar ซ้ำซ้อนกับ predictors ที่ model อยู่แล้ว.

## Cross-check / Correction

> [!warning] Verification note
> Bias adjustment ไม่จำเป็นเสมอ: exponentiating a log-scale location forecast มักให้ median บน original scale; ถ้าต้องการ mean ต้องพิจารณา predictive distribution.

## Quick Review

- **Concept:** Transformations เปลี่ยน scale ของข้อมูลเพื่อทำ variance/pattern ให้ model ง่ายขึ้น ส่วน adjustments แก้ผลของ calendar, population, inflation หรือ known structural effects ก่อน modeling.
- **สิ่งที่ต้องจำ:** Log transform มีประโยชน์เมื่อ variation เพิ่มตาม level และข้อมูลเป็นบวก.
- **การใช้งาน:** ใช้ stabilize variance.
- **ข้อควรระวัง:** คิดว่า back-transform point forecast แล้วได้ mean เสมอ.

## Related Notes

- [[Time Series Decomposition]]
- [[Log Transformation and Elasticity]]
- [[Probabilistic Forecasting]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[02-TSDecomposition]] | Transformations & adjustments section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `02-TSDecomposition.pdf` — Transformations & adjustments section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
