---
title: "Forecast Accuracy Metrics"
aliases:
  - Forecast Error Metrics
  - MAE RMSE MAPE MASE
  - Forecast Evaluation Metrics
topic_number: 3
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

# Forecast Accuracy Metrics

> [!abstract] Summary
> Forecast accuracy metrics แปลงความคลาดเคลื่อนระหว่าง actual และ forecast ให้เป็นตัวเลขสำหรับเปรียบเทียบ model โดย metric แต่ละตัวให้ความสำคัญกับ error ต่างกัน.

## Why this concept matters

ไม่มี metric เดียวที่ดีที่สุดทุกกรณี การเลือก metric ต้องสอดคล้องกับ unit, business loss, outliers, zeros และความต้องการเปรียบเทียบข้าม series.

## Core Idea

- กำหนด forecast error เป็น $e_t=y_t-\hat y_t$; ค่า positive หมายถึง under-forecast.
- MAE robust กว่า RMSE ต่อ large errors เพราะไม่ square error.
- RMSE ลงโทษ large errors มากและอยู่ในหน่วยเดียวกับ target.
- MAPE scale-free แต่มีปัญหาเมื่อ actual ใกล้ศูนย์/เท่าศูนย์.
- MASE scale-free โดย scale error เทียบกับ naïve หรือ seasonal naïve training error.
- MBE ใช้ดู bias แต่ positive/negative errors สามารถหักล้างกันได้.

## Mathematical Formulation / Technical Detail

ตัวอย่างสูตร:

$$
MAE=\frac1n\sum_{t=1}^n|e_t|,\qquad
MSE=\frac1n\sum e_t^2,\qquad
RMSE=\sqrt{MSE}.
$$

$$
MBE=\frac1n\sum e_t.
$$

$$
MAPE=\frac{100}{n}\sum\left|\frac{e_t}{y_t}\right|.
$$

สำหรับ non-seasonal MASE:

$$
MASE=
\frac{\frac1n\sum|e_t|}
{\frac1{T-1}\sum_{t=2}^{T}|y_t-y_{t-1}|}.
$$

Seasonal series มักใช้ denominator จาก seasonal naïve difference $|y_t-y_{t-m}|$.

## Worked / Practical Example

ถ้า model A มี MAE=8 และ RMSE=30 แต่ model B มี MAE=10 และ RMSE=18 แสดงว่า A โดยทั่วไป error เล็กกว่า แต่มี large misses บางครั้งรุนแรงกว่า B. หาก large miss มีต้นทุนสูง RMSE อาจสะท้อน objective ได้ดีกว่า.

## Assumptions and Interpretation

- Metric ต้องคำนวณบน genuine forecasts เช่น validation/test/CV เมื่อใช้เลือก model.
- MASE < 1 หมายถึงโดยเฉลี่ย absolute error ต่ำกว่า benchmark ที่ใช้ scale.
- Theil's U แบบ ratio ต้องระบุ definition เพราะมีหลาย convention.

## When to use

- MAE เมื่ออยากตีความ average absolute miss ในหน่วยจริง.
- RMSE เมื่อ large errors มีต้นทุนสูงเป็นพิเศษ.
- MASE เมื่อต้องเปรียบเทียบหลาย series ต่าง scale.
- MBE ใช้เสริมเพื่อดู systematic under/over forecast.

## When not to use / Limitations

- MAPE ไม่เหมาะเมื่อ actual มี zero หรือใกล้ zero.
- อย่าเลือก metric เพราะคุ้นเคยโดยไม่เชื่อมกับ decision cost.

## Common Mistakes

- พูดว่า metric 'ยิ่งมากยิ่งดี' — error metrics โดยทั่วไปยิ่งต่ำยิ่งดี.
- ใช้ residual training error แทน test forecast error.
- ใช้ MBE เพียงตัวเดียวแล้วสรุปว่า model แม่น เพราะ error อาจหักล้างกัน.
- ใช้ sMAPE โดยไม่ระบุสูตร เพราะมีหลาย definition.

## Cross-check / Correction

> [!warning] Verification note
> Hyndman & Koehler (2006) ชี้ข้อจำกัดของ percentage-based measures หลายชนิดและเสนอ MASE สำหรับการเปรียบเทียบข้าม series; sMAPE จึงไม่ควรถูกใช้เป็น default เพียงเพราะเป็น 'symmetric'.

## Quick Review

- **Concept:** Forecast accuracy metrics แปลงความคลาดเคลื่อนระหว่าง actual และ forecast ให้เป็นตัวเลขสำหรับเปรียบเทียบ model โดย metric แต่ละตัวให้ความสำคัญกับ error ต่างกัน.
- **สิ่งที่ต้องจำ:** กำหนด forecast error เป็น $e_t=y_t-\hat y_t$; ค่า positive หมายถึง under-forecast.
- **การใช้งาน:** MAE เมื่ออยากตีความ average absolute miss ในหน่วยจริง.
- **ข้อควรระวัง:** พูดว่า metric 'ยิ่งมากยิ่งดี' — error metrics โดยทั่วไปยิ่งต่ำยิ่งดี.

## Related Notes

- [[Benchmark Forecasting Methods]]
- [[Time Series Cross Validation]]
- [[Quantile Forecast and Quantile Score|Quantile Score]]
- [[CRPS]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[01-TSoverview]] | Model evaluation / forecast error measurement section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `01-TSoverview.pdf` — Model evaluation / forecast error measurement section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)
- [Hyndman, R.J. & Koehler, A.B. (2006), Another look at measures of forecast accuracy, International Journal of Forecasting 22(4), 679–688.](https://doi.org/10.1016/j.ijforecast.2006.03.001)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
