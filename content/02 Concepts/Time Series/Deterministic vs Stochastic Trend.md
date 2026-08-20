---
title: "Deterministic vs Stochastic Trend"
aliases:
  - Deterministic Trend
  - Stochastic Trend
topic_number: 24
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[08-DynamicRegression_260627_151638]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Deterministic vs Stochastic Trend

> [!abstract] Summary
> Deterministic trend model trend เป็นฟังก์ชันเวลา เช่น linear $\beta_0+\beta_1t$ ส่วน stochastic trendเกิดจาก integrated process เช่น ARIMA ที่มี unit root/differencing.

## Why this concept matters

สอง model อาจ fit historical growthคล้ายกัน แต่ long-horizon uncertainty แตกต่างมาก เพราะ stochastic trendสะสม shocks.

## Core Idea

- Deterministic trend กลับเข้าสู่เส้น trendหลัง shockชั่วคราวเมื่อ error stationary.
- Stochastic trend shockมี permanent effectต่อ level และ forecast varianceโตกับ horizon.
- Deterministic trendสามารถมี ARMA errorsเพื่อจับ short-term autocorrelation.
- Differencing $d=1$ เป็น signature ของ stochastic trendใน ARIMA framework.

## Mathematical Formulation / Technical Detail

Deterministic:

$$
y_t=\beta_0+\beta_1t+\eta_t,\qquad \eta_t\sim ARMA.
$$

Stochastic trend ตัวอย่าง random walk with drift:

$$
y_t=c+y_{t-1}+\varepsilon_t.
$$

## Worked / Practical Example

ยอดขายที่เพิ่มประมาณ 10 ต่อเดือนอาจ fit ได้ทั้ง linear trend และ random walk with drift. หาก shock ใหญ่เกิดขึ้น deterministic modelคาดว่ากลับสู่ trend path; stochastic modelยอมให้ level ใหม่ persist.

## Assumptions and Interpretation

- การเลือกควรพิจารณา economics/domain, unit-root evidence และ forecast performance.
- Long-horizon intervalsจาก deterministic trendอาจแคบเกินถ้า true processมี stochastic trend.

## When to use

- เปรียบเทียบ trend assumptions.
- forecast horizonsยาวที่ uncertaintyเรื่อง growthสำคัญ.

## When not to use / Limitations

- unit-root tests มี powerจำกัดและไม่ควรใช้เป็นคำตอบเดียว.
- structural breaksอาจทำให้ stochastic/deterministic distinctionยุ่งยาก.

## Common Mistakes

- คิดว่า trend lineใน plotพิสูจน์ deterministic trend.
- สับสน ARMA errorsกับ ARIMA errorsที่มี differencing.
- เลือกจาก in-sample fitอย่างเดียว.

## Quick Review

- **Concept:** Deterministic trend model trend เป็นฟังก์ชันเวลา เช่น linear $\beta_0+\beta_1t$ ส่วน stochastic trendเกิดจาก integrated process เช่น ARIMA ที่มี unit root/differencing.
- **สิ่งที่ต้องจำ:** Deterministic trend กลับเข้าสู่เส้น trendหลัง shockชั่วคราวเมื่อ error stationary.
- **การใช้งาน:** เปรียบเทียบ trend assumptions.
- **ข้อควรระวัง:** คิดว่า trend lineใน plotพิสูจน์ deterministic trend.

## Related Notes

- [[Dynamic Regression ARIMAX]]
- [[ARIMA]]
- [[Prediction Intervals]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[08-DynamicRegression_260627_151638]] | Deterministic and stochastic trend section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `08-DynamicRegression_260627_151638.pdf` — Deterministic and stochastic trend section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
