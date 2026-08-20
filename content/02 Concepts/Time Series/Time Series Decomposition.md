---
title: "Time Series Decomposition"
aliases:
  - TS Decomposition
  - Decomposition
topic_number: 4
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

# Time Series Decomposition

> [!abstract] Summary
> Time Series Decomposition แยก series ออกเป็น trend-cycle, seasonal และ remainder เพื่อช่วยเข้าใจโครงสร้างและอาจช่วย forecasting.

## Why this concept matters

เมื่อแยก components ได้ เราสามารถเห็นว่าการเปลี่ยนแปลงมาจาก long-run movement, repeating seasonal pattern หรือส่วนที่เหลือที่ model ยังอธิบายไม่ได้.

## Core Idea

- Trend-cycle รวม long-term trend กับ cycle ที่แยกออกจากกันได้ยากในทางปฏิบัติ.
- Seasonal component คือ pattern ที่ repeat ด้วย seasonal period.
- Remainder คือส่วนที่เหลือหลังหัก trend-cycle และ seasonality.
- Seasonally adjusted series คือ series ที่นำ seasonal component ออก.

## Mathematical Formulation / Technical Detail

Additive decomposition:

$$
y_t=T_t+S_t+R_t.
$$

Multiplicative decomposition:

$$
y_t=T_tS_tR_t.
$$

สำหรับ additive:

$$
y_t-S_t=T_t+R_t
$$

คือ seasonally adjusted series.

## Worked / Practical Example

ยอดขายไอศกรีมต่ำในฤดูหนาวอาจเป็น seasonal effect; ยอดขายเพิ่มจาก economic boom เป็น non-seasonal movement. การดู seasonally adjusted series ช่วยแยกสองเรื่องนี้.

## Assumptions and Interpretation

- Decomposition เป็น descriptive tool และไม่ควรถูกตีความว่า component ที่แยกได้เป็น causal truth.
- Methods ต่างกันอาจให้ components ต่างกัน เช่น classical decomposition กับ STL/MSTL.

## When to use

- ใช้สำรวจ trend/seasonality.
- ใช้ทำ seasonal adjustment.
- ใช้เป็นส่วนหนึ่งของ decomposition forecasting.

## When not to use / Limitations

- ไม่ควรใช้ classical decomposition แบบแข็งเมื่อ seasonality เปลี่ยนตามเวลาอย่างชัดเจน; STL/MSTL อาจเหมาะกว่า.

## Common Mistakes

- ตีความ remainder ว่า 'random noise' โดยอัตโนมัติทั้งที่อาจยังมี autocorrelation.
- สับสน seasonal adjustment กับการลบ trend.
- คิดว่า decomposition พิสูจน์สาเหตุของ pattern.

## Quick Review

- **Concept:** Time Series Decomposition แยก series ออกเป็น trend-cycle, seasonal และ remainder เพื่อช่วยเข้าใจโครงสร้างและอาจช่วย forecasting.
- **สิ่งที่ต้องจำ:** Trend-cycle รวม long-term trend กับ cycle ที่แยกออกจากกันได้ยากในทางปฏิบัติ.
- **การใช้งาน:** ใช้สำรวจ trend/seasonality.
- **ข้อควรระวัง:** ตีความ remainder ว่า 'random noise' โดยอัตโนมัติทั้งที่อาจยังมี autocorrelation.

## Related Notes

- [[Additive vs Multiplicative Seasonality]]
- [[MSTL Decomposition]]
- [[Transformations and Adjustments]]
- [[Complex Seasonality]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[02-TSDecomposition]] | Overview / decomposition section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `02-TSDecomposition.pdf` — Overview / decomposition section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
