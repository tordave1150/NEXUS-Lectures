---
title: "White Noise and Residual Diagnostics"
aliases:
  - White Noise
  - Residual Diagnostics
  - Ljung-Box Test
topic_number: 9
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

# White Noise and Residual Diagnostics

> [!abstract] Summary
> Forecast model ที่ดีควรเหลือ residuals ที่ไม่มีข้อมูลเชิงเวลาที่ model ยังใช้ประโยชน์ได้ โดยเป้าหมายหลักคือ residuals มี mean ใกล้ 0 และไม่มี autocorrelation ที่มีโครงสร้าง.

## Why this concept matters

Residual diagnostics ช่วยแยก 'model fit แล้ว' ออกจาก 'model ใช้ information ครบแล้ว'. ถ้า residuals ยังมี pattern forecasting model ยังอาจปรับปรุงได้.

## Core Idea

- White noise โดยพื้นฐานมี mean คงที่ (มัก 0), variance คงที่ และไม่ autocorrelated.
- Gaussian white noise เพิ่ม assumption เรื่อง normal distribution; white noise ทั่วไปไม่จำเป็นต้อง normal.
- Ljung-Box ทดสอบ autocorrelations หลาย lags พร้อมกัน.
- Residual normality ไม่ใช่เงื่อนไขหลักของ unbiased point forecast แต่สำคัญต่อ parametric intervals/inference บางแบบ.

## Mathematical Formulation / Technical Detail

Ljung-Box statistic:

$$
Q^*=T(T+2)\sum_{k=1}^{\ell}\frac{r_k^2}{T-k}.
$$

ภายใต้เงื่อนไขเหมาะสม เปรียบเทียบกับ $\chi^2$ โดย degrees of freedom ต้องปรับตามจำนวน parameters ที่ estimate.

## Worked / Practical Example

ถ้า residual ACF มี spikes ต่อเนื่องที่ lag 12,24 สำหรับ monthly data แปลว่า model อาจยังจับ annual seasonality ไม่ครบ แม้ training RMSE จะต่ำ.

## Assumptions and Interpretation

- เลือก lag $\ell$ ของ Ljung-Box ให้สัมพันธ์กับ sample size และ seasonality.
- p-value สูงไม่ได้พิสูจน์ว่า residuals independent; เพียงไม่มีหลักฐานเพียงพอต่อ autocorrelation ที่ test ตรวจ.

## When to use

- ใช้หลัง fit ทุก forecasting model.
- ใช้เปรียบเทียบว่ามี temporal information เหลือหรือไม่.

## When not to use / Limitations

- อย่าใช้ normality test อย่างเดียวตัดสิน model adequacy.
- อย่า overfit เพียงเพื่อทำทุก ACF spike หาย.

## Common Mistakes

- แปล p-value > 0.05 ว่า 'พิสูจน์ว่า white noise'.
- ใช้ residuals แทน genuine forecast errors เพื่อประเมิน out-of-sample accuracy.
- ไม่ปรับ degrees of freedom เมื่อตรวจ ARIMA residuals.

## Quick Review

- **Concept:** Forecast model ที่ดีควรเหลือ residuals ที่ไม่มีข้อมูลเชิงเวลาที่ model ยังใช้ประโยชน์ได้ โดยเป้าหมายหลักคือ residuals มี mean ใกล้ 0 และไม่มี autocorrelation ที่มีโครงสร้าง.
- **สิ่งที่ต้องจำ:** White noise โดยพื้นฐานมี mean คงที่ (มัก 0), variance คงที่ และไม่ autocorrelated.
- **การใช้งาน:** ใช้หลัง fit ทุก forecasting model.
- **ข้อควรระวัง:** แปล p-value > 0.05 ว่า 'พิสูจน์ว่า white noise'.

## Related Notes

- [[Autocorrelation and ACF]]
- [[Time Series Cross Validation]]
- [[ARIMA]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[03-FCToolbox]] | White noise / residual diagnostics section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `03-FCToolbox.pdf` — White noise / residual diagnostics section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
