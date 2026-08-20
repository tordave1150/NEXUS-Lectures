---
title: "Lagged Variables and Lag Plots"
aliases:
  - Lagged Variables
  - Lag Features
  - Lag Plot
topic_number: 7
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[03-FCToolbox]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Lagged Variables and Lag Plots

> [!abstract] Summary
> Lagged variable $y_{t-k}$ คือค่าของ series ย้อนหลัง $k$ periods และ lag plot ใช้ดูความสัมพันธ์ระหว่าง $y_t$ กับอดีตของมัน.

## Why this concept matters

Lags เป็น building block ของ ARIMA, dynamic regression และ ML feature engineering; การมอง lag plots ช่วยเห็น persistence และ seasonality.

## Core Idea

- Lag 1 คือ $y_{t-1}$, lag 2 คือ $y_{t-2}$.
- Lag plot วาง $y_t$ เทียบกับ $y_{t-k}$ เพื่อดู linear/nonlinear dependence.
- Seasonal data มักมี relationship ชัดที่ seasonal lags เช่น 4,8 สำหรับ quarterly.
- Feature construction ต้องป้องกัน leakage: lag ต้องใช้ข้อมูลที่มี ณ prediction time เท่านั้น.

## Mathematical Formulation / Technical Detail

Lag operator:

$$
B^k y_t = y_{t-k}.
$$

ตัวอย่าง quarterly seasonal lag:

$$
y_{t-4}
$$

คือ observation ของ quarter เดียวกันในปีก่อน.

## Worked / Practical Example

Beer production quarterly อาจมี strong positive relationship ที่ lag 4 และ 8 เพราะ quarter เดียวกันข้ามปีมี pattern คล้ายกัน; lag 2 อาจมี negative relation หาก peak กับ trough อยู่ห่างกันครึ่ง cycle.

## Assumptions and Interpretation

- Lag plot แสดง association ไม่ใช่ causation.
- Trend สามารถสร้าง high lag correlation แม้ไม่มี causal memory โดยตรง.

## When to use

- ใช้ exploratory analysis.
- สร้าง autoregressive features.
- ตรวจ seasonal dependence.

## When not to use / Limitations

- ไม่ควรสร้าง lag ที่ต้องใช้ future target ใน production.
- high-dimensional lag sets อาจ overfit.

## Common Mistakes

- ตีความ correlation ที่ lag เป็น causal effect.
- ลืม drop/handle warm-up rows ที่ lag ยังไม่มีค่า.
- ใช้ random CV หลังสร้าง lag จนเกิด leakage.

## Quick Review

- **Concept:** Lagged variable $y_{t-k}$ คือค่าของ series ย้อนหลัง $k$ periods และ lag plot ใช้ดูความสัมพันธ์ระหว่าง $y_t$ กับอดีตของมัน.
- **สิ่งที่ต้องจำ:** Lag 1 คือ $y_{t-1}$, lag 2 คือ $y_{t-2}$.
- **การใช้งาน:** ใช้ exploratory analysis.
- **ข้อควรระวัง:** ตีความ correlation ที่ lag เป็น causal effect.

## Related Notes

- [[Autocorrelation and ACF]]
- [[AR MA ARMA]]
- [[ML Time-Series Feature Engineering]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[03-FCToolbox]] | Lagged variables / lag plot section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `03-FCToolbox.pdf` — Lagged variables / lag plot section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
