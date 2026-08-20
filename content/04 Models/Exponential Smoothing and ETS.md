---
title: "Exponential Smoothing and ETS"
aliases:
  - Exponential Smoothing
  - ETS
  - SES Holt Holt-Winters
topic_number: 11
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[04-ETS]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Exponential Smoothing and ETS

> [!abstract] Summary
> Exponential smoothing สร้าง forecast จาก weighted averages ของอดีต โดยให้น้ำหนักลดลงแบบ exponential; family หลักครอบคลุม SES, Holt, damped trend และ seasonal methods.

## Why this concept matters

ETS เป็นหนึ่งใน classical forecasting families ที่แข็งแรงมาก โดย model components สอดคล้องกับ level, trend และ seasonality ที่เห็นใน series.

## Core Idea

- SES เหมาะกับ level-only series.
- Holt เพิ่ม trend state.
- Damped trend ลดการ extrapolate trend แบบไม่จำกัดใน long horizon.
- Holt-Winters เพิ่ม seasonal state.
- Smoothing parameters ควบคุมว่ารัฐ (state) จะตอบสนองต่อ observation ใหม่เร็วเพียงใด.

## Mathematical Formulation / Technical Detail

SES component form:

$$
\hat y_{t+h|t}=\ell_t,
$$

$$
\ell_t=\alpha y_t+(1-\alpha)\ell_{t-1},\quad 0\le\alpha\le1.
$$

Holt linear:

$$
\hat y_{t+h|t}=\ell_t+h b_t.
$$

โดยมี level smoothing และ trend smoothing แยกกัน.

## Worked / Practical Example

ถ้า $\alpha$ ใกล้ 1, SES ให้น้ำหนัก observation ล่าสุดสูงและตอบสนองเร็ว; ถ้า $\alpha$ ใกล้ 0, level state เปลี่ยนช้า. เมื่อ $\alpha=1$ SES point forecast คล้าย naïve.

## Assumptions and Interpretation

- Exponential smoothing weights decay with age.
- Optimal parameters และ initial states ควร estimate จาก objective เช่น likelihood/SSE มากกว่าตั้งตามใจ.

## When to use

- short-to-medium horizon business series.
- series ที่ pattern อธิบายด้วย level/trend/seasonality ได้ดี.

## When not to use / Limitations

- ไม่เหมาะถ้าต้อง model exogenous predictors โดยตรง.
- complex seasonality ยาวมากอาจต้อง DHR/MSTL/TBATS แทน.

## Common Mistakes

- คิดว่า exponential smoothing = moving average window แบบ equal weights.
- ตั้ง smoothing parameter สูงแล้วสรุปว่า 'ดีกว่า' โดยไม่ validate.
- ใช้ undamped Holt extrapolate trend ไกลโดยไม่ดู plausibility.

## Quick Review

- **Concept:** Exponential smoothing สร้าง forecast จาก weighted averages ของอดีต โดยให้น้ำหนักลดลงแบบ exponential; family หลักครอบคลุม SES, Holt, damped trend และ seasonal methods.
- **สิ่งที่ต้องจำ:** SES เหมาะกับ level-only series.
- **การใช้งาน:** short-to-medium horizon business series.
- **ข้อควรระวัง:** คิดว่า exponential smoothing = moving average window แบบ equal weights.

## Related Notes

- [[ETS Models and Model Selection]]
- [[Benchmark Forecasting Methods]]
- [[ARIMA]]
- [[Time Series Decomposition]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[04-ETS]] | Exponential smoothing methods section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `04-ETS.pdf` — Exponential smoothing methods section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
