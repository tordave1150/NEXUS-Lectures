---
title: "Additive vs Multiplicative Seasonality"
aliases:
  - Additive Seasonality
  - Multiplicative Seasonality
topic_number: 5
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

# Additive vs Multiplicative Seasonality

> [!abstract] Summary
> Additive seasonality เหมาะเมื่อ seasonal effect มีขนาดค่อนข้างคงที่เป็นหน่วยจริง ส่วน multiplicative seasonality เหมาะเมื่อ seasonal amplitude เปลี่ยนตามระดับของ series เป็นสัดส่วน.

## Why this concept matters

การเลือก additive หรือ multiplicative มีผลต่อ interpretation, seasonal adjustment และการ forecast.

## Core Idea

- Additive seasonal component วัดผลเพิ่ม/ลดเป็นหน่วยของ target.
- Multiplicative seasonal factor วัดเป็นอัตราส่วนเทียบกับ local level.
- Additive seasonal components ในหนึ่ง cycle มักถูก normalize ให้รวมประมาณ 0.
- Multiplicative seasonal factors มัก normalize ให้เฉลี่ยประมาณ 1 หรือรวมประมาณ $m$.

## Mathematical Formulation / Technical Detail

Additive:

$$
y_t=T_t+S_t+R_t.
$$

Multiplicative:

$$
y_t=T_tS_tR_t.
$$

Seasonal adjustment:

$$
y_t^{adj}=y_t-S_t
$$

สำหรับ additive และ

$$
y_t^{adj}=\frac{y_t}{S_t}
$$

สำหรับ multiplicative.

## Worked / Practical Example

ถ้า Friday seasonal factor = 1.40 แปลว่า Friday อยู่ประมาณ 40% เหนือ level ปกติหลังตีความในโครงสร้าง multiplicative. ถ้า Sunday additive component = -1,894 แปลว่าประมาณ 1,894 หน่วยต่ำกว่า local level หลังคุม components อื่น.

## Assumptions and Interpretation

- Multiplicative form ต้องระวัง zero/negative values.
- Log transformation สามารถเปลี่ยน multiplicative relationships บางแบบให้ใกล้ additive: $\log y_t=\log T_t+\log S_t+\log R_t$.

## When to use

- Additive เมื่อ seasonal swing คงที่เป็นหน่วย.
- Multiplicative เมื่อ seasonal swing โตตามระดับของ series.

## When not to use / Limitations

- Multiplicative ไม่เหมาะตรง ๆ เมื่อ series มี zero/negative โดยไม่มี transformation ที่เหมาะสม.

## Common Mistakes

- เลือกจากชื่อ method แทนการดู amplitude กับ level.
- ตีความ factor 1.4 ว่าเพิ่ม 1.4 หน่วย แทน 40%.
- ลืม normalize seasonal components.

## Quick Review

- **Concept:** Additive seasonality เหมาะเมื่อ seasonal effect มีขนาดค่อนข้างคงที่เป็นหน่วยจริง ส่วน multiplicative seasonality เหมาะเมื่อ seasonal amplitude เปลี่ยนตามระดับของ series เป็นสัดส่วน.
- **สิ่งที่ต้องจำ:** Additive seasonal component วัดผลเพิ่ม/ลดเป็นหน่วยของ target.
- **การใช้งาน:** Additive เมื่อ seasonal swing คงที่เป็นหน่วย.
- **ข้อควรระวัง:** เลือกจากชื่อ method แทนการดู amplitude กับ level.

## Related Notes

- [[Time Series Decomposition]]
- [[Transformations and Adjustments]]
- [[MSTL Decomposition]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[02-TSDecomposition]] | Seasonality / seasonal components section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `02-TSDecomposition.pdf` — Seasonality / seasonal components section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
