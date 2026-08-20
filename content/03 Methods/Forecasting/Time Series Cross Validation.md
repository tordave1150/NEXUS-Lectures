---
title: "Time Series Cross Validation"
aliases:
  - TS Cross Validation
  - Rolling Forecast Origin
  - Forward Chaining
topic_number: 10
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

# Time Series Cross Validation

> [!abstract] Summary
> Time Series Cross Validation ประเมิน forecasting model โดยเลื่อน forecast origin ไปข้างหน้าตามเวลาและไม่ให้ข้อมูลอนาคตรั่วเข้า training set.

## Why this concept matters

Single train/test split อาจไวต่อช่วงเวลาที่เลือก; rolling-origin evaluation ใช้หลาย forecast origins เพื่อวัด performance เสถียรกว่า.

## Core Idea

- Expanding window เพิ่ม training set เมื่อเวลาเดินหน้า.
- Rolling window รักษาขนาด training window คงที่เพื่อเน้น recent regime.
- สามารถประเมินหลาย horizons แยกกัน เช่น $h=1,\ldots,8$.
- Preprocessing/feature scaling ต้อง fit ภายในแต่ละ fold เพื่อป้องกัน leakage.

## Mathematical Formulation / Technical Detail

สำหรับ forecast origin $T_i$ สร้าง

$$
\hat y_{T_i+h|T_i}
$$

แล้ว error

$$
e_{i,h}=y_{T_i+h}-\hat y_{T_i+h|T_i}.
$$

จากนั้น aggregate เช่น

$$
RMSE_h=\sqrt{\frac1N\sum_i e_{i,h}^2}.
$$

## Worked / Practical Example

ถ้าต้อง deploy one-step-ahead forecast ทุกวัน ให้ทำ expanding-window CV ที่แต่ละ fold train ถึงวัน $t$ และ validate ที่ $t+1$. ถ้าจะ forecast 7 วันพร้อมกัน ควรประเมิน metrics ตาม horizon 1–7.

## Assumptions and Interpretation

- Fold ordering ต้องรักษาเวลา.
- Hyperparameter tuning ต้องใช้ validation folds ภายใน training period; final test ต้องไม่ถูกใช้เลือก model.

## When to use

- เลือก model/hyperparameters สำหรับ forecasting.
- ประเมิน horizon-specific accuracy.
- เปรียบเทียบ statistical และ ML models อย่างแฟร์.

## When not to use / Limitations

- ไม่เหมาะใช้ random K-fold แบบมาตรฐานถ้ามันทำให้ future observations เข้า training ของ past validation.
- ถ้ามี concept drift มาก expanding window อาจให้น้ำหนัก regime เก่ามากเกินไป.

## Common Mistakes

- Scale/normalize ก่อนแบ่ง folds โดยใช้ข้อมูลทั้งหมด.
- เลือก model จาก test set ซ้ำ ๆ.
- เปรียบเทียบ models ที่มี training periods ไม่เท่ากันโดยไม่ตั้งใจ.

## Quick Review

- **Concept:** Time Series Cross Validation ประเมิน forecasting model โดยเลื่อน forecast origin ไปข้างหน้าตามเวลาและไม่ให้ข้อมูลอนาคตรั่วเข้า training set.
- **สิ่งที่ต้องจำ:** Expanding window เพิ่ม training set เมื่อเวลาเดินหน้า.
- **การใช้งาน:** เลือก model/hyperparameters สำหรับ forecasting.
- **ข้อควรระวัง:** Scale/normalize ก่อนแบ่ง folds โดยใช้ข้อมูลทั้งหมด.

## Related Notes

- [[Forecast Accuracy Metrics]]
- [[ML Time-Series Feature Engineering]]
- [[Dynamic Regression ARIMAX]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[03-FCToolbox]] | Time-series cross-validation section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `03-FCToolbox.pdf` — Time-series cross-validation section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
