---
title: "Benchmark Forecasting Methods"
aliases:
  - Benchmark Methods
  - Baseline Forecasting Methods
  - Simple Forecasting Methods
topic_number: 2
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[01-TSoverview]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Benchmark Forecasting Methods

> [!abstract] Summary
> Benchmark methods คือ baseline ง่าย ๆ เช่น Mean, Naïve, Seasonal Naïve และ Drift ซึ่งใช้ตรวจว่า model ที่ซับซ้อนเพิ่ม predictive value จริงหรือไม่.

## Why this concept matters

Forecasting model ที่ซับซ้อนควรชนะ baseline บนข้อมูลที่ไม่ถูกใช้ฝึก มิฉะนั้น complexity อาจไม่ได้สร้างประโยชน์.

## Core Idea

- Mean ใช้ historical average เป็น forecast ทุก horizon.
- Naïve ใช้ค่าล่าสุดเป็น forecast.
- Seasonal Naïve ใช้ค่าล่าสุดของ season เดียวกัน.
- Drift ต่อเส้นจากจุดแรกถึงจุดล่าสุดด้วย average historical change.

## Mathematical Formulation / Technical Detail

สูตรหลัก:

$$
\text{Mean: }\hat y_{T+h|T}=\frac1T\sum_{t=1}^T y_t
$$

$$
\text{Naïve: }\hat y_{T+h|T}=y_T
$$

$$
\text{Drift: }\hat y_{T+h|T}=y_T+h\frac{y_T-y_1}{T-1}
$$

Seasonal naïve เลือก observation ล่าสุดที่อยู่ season เดียวกับ $T+h$.

## Worked / Practical Example

Lecture example มี training demand 190, 260, 330, 480, 570, 710, 650, 690. Mean = 485, Naïve = 690, seasonal naïve สำหรับ 4 quarters ถัดไป = 570, 710, 650, 690 และ drift ประมาณ 761, 833, 904, 976.

## Assumptions and Interpretation

- Baseline ที่เหมาะควรสัมพันธ์กับ structure ของ series เช่น SNaïve สำหรับ seasonal data.
- การเลือก final model ต้องใช้ out-of-sample evaluation ไม่ใช่ visual judgement อย่างเดียว.

## When to use

- ใช้เป็น minimum benchmark ใน forecasting project.
- ใช้ตรวจว่าความซับซ้อนของ ARIMA/ETS/ML/NN ให้ improvement จริงหรือไม่.

## When not to use / Limitations

- อย่าใช้ Mean เพียง baseline เดียวเมื่อมี strong seasonality.
- Drift extrapolates trend ต่อไป จึงเสี่ยงเมื่อ trend เปลี่ยน.

## Common Mistakes

- คิดว่า 'Naïve' แปลว่า model แย่.
- เปรียบเทียบเฉพาะ training error.
- สับสน Drift กับ OLS linear trend regression.

## Quick Review

- **Concept:** Benchmark methods คือ baseline ง่าย ๆ เช่น Mean, Naïve, Seasonal Naïve และ Drift ซึ่งใช้ตรวจว่า model ที่ซับซ้อนเพิ่ม predictive value จริงหรือไม่.
- **สิ่งที่ต้องจำ:** Mean ใช้ historical average เป็น forecast ทุก horizon.
- **การใช้งาน:** ใช้เป็น minimum benchmark ใน forecasting project.
- **ข้อควรระวัง:** คิดว่า 'Naïve' แปลว่า model แย่.

## Related Notes

- [[Forecast Accuracy Metrics]]
- [[ARIMA|Random Walk]]
- [[Exponential Smoothing and ETS|ETS]]
- [[ARIMA]]
- [[Time Series Cross Validation]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[01-TSoverview]] | Benchmark forecasting methods section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `01-TSoverview.pdf` — Benchmark forecasting methods section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
