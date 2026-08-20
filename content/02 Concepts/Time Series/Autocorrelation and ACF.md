---
title: "Autocorrelation and ACF"
aliases:
  - Autocorrelation
  - ACF
  - Correlogram
topic_number: 8
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

# Autocorrelation and ACF

> [!abstract] Summary
> Autocorrelation วัด linear association ระหว่าง series กับ lagged version ของตัวเอง; ACF plot แสดง autocorrelation หลาย lags เพื่ออ่าน memory, trend และ seasonality.

## Why this concept matters

ACF เป็นเครื่องมือสำคัญในการ diagnose time-series structure, residuals และ stationarity/differencing decisions.

## Core Idea

- $r_k$ คือ sample autocorrelation ที่ lag $k$ และอยู่ระหว่าง -1 ถึง 1.
- Trend มักทำให้ ACF decay ช้าและเป็นบวกหลาย lags.
- Seasonality มักสร้าง spikes ที่ seasonal lags และ multiples.
- ACF ใกล้ศูนย์ไม่ได้แปล independence; มันบอกว่าไม่มี linear autocorrelation ที่ lag นั้น.

## Mathematical Formulation / Technical Detail

Sample ACF โดยแนวคิด:

$$
r_k=
\frac{\sum_{t=k+1}^{T}(y_t-\bar y)(y_{t-k}-\bar y)}
{\sum_{t=1}^{T}(y_t-\bar y)^2}.
$$

สำหรับ white noise เส้นประมาณ

$$
\pm\frac{1.96}{\sqrt{T}}
$$

มักใช้เป็น marginal reference bounds.

## Worked / Practical Example

Quarterly series ที่มี seasonal period 4 อาจเห็น ACF สูงที่ lag 4, 8, 12. Series ที่มี strong trend อาจเห็น lag 1,2,3 สูงและค่อย ๆ decay.

## Assumptions and Interpretation

- Approximate ACF bounds ใช้เป็น heuristic ภายใต้ white-noise assumptions.
- การดูหลาย lags พร้อมกันทำให้โอกาสมี spike หลุดเส้นโดยบังเอิญเพิ่มขึ้น.

## When to use

- ตรวจ seasonality/trend.
- ตรวจ residual autocorrelation.
- ช่วยเลือก differencing/model structure ร่วมกับ PACF และ diagnostics.

## When not to use / Limitations

- อย่าตัดสิน white noise จาก spike เดียวอย่างกลไก.
- ACF ไม่ตรวจ nonlinear dependence ทุกชนิด.

## Common Mistakes

- พูดว่า spike นอก $\pm2/\sqrt T$ ทุกอัน 'significant' โดยไม่สน multiple testing/dependence.
- สรุปว่าระหว่าง variables มี causalityจาก ACF.
- ใช้ ACF ของ nonstationary trend series แล้วตีความเหมือน stationary ARMA.

## Cross-check / Correction

> [!warning] Verification note
> เส้น ±2/√T เป็น approximate marginal bounds ไม่ใช่กฎตายตัวสำหรับตัดสิน white noise ทั้งชุด; portmanteau tests และ residual context ควรใช้ร่วมกัน.

## Quick Review

- **Concept:** Autocorrelation วัด linear association ระหว่าง series กับ lagged version ของตัวเอง; ACF plot แสดง autocorrelation หลาย lags เพื่ออ่าน memory, trend และ seasonality.
- **สิ่งที่ต้องจำ:** $r_k$ คือ sample autocorrelation ที่ lag $k$ และอยู่ระหว่าง -1 ถึง 1.
- **การใช้งาน:** ตรวจ seasonality/trend.
- **ข้อควรระวัง:** พูดว่า spike นอก $\pm2/\sqrt T$ ทุกอัน 'significant' โดยไม่สน multiple testing/dependence.

## Related Notes

- [[White Noise and Residual Diagnostics]]
- [[AR MA ARMA]]
- [[ARIMA]]
- [[Complex Seasonality]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[03-FCToolbox]] | Autocorrelation function section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `03-FCToolbox.pdf` — Autocorrelation function section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
