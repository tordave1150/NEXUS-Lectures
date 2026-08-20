---
title: "Regression Confidence vs Prediction Intervals"
topic_number: 159
domain:
  - Statistics
  - Regression
language: th
source_type:
  - lecture
tags:
  - statistics
  - regression
  - confidence-interval
  - prediction-interval
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Regression Confidence vs Prediction Intervals

> [!abstract] Summary
> ใน regression, confidence interval ที่ $x_0$ เป้าหมายคือ **mean response** $E[Y|x_0]$ ส่วน prediction interval เป้าหมายคือ **new individual observation**; prediction interval จึงกว้างกว่าเพราะรวม irreducible observation noise.

## Why this concept matters

ช่วยป้องกันการใช้ช่วงผิดชนิดเมื่อต้องตอบคำถาม “ค่าเฉลี่ยของกลุ่ม” กับ “ค่ารายบุคคลครั้งถัดไป”.

## Core Idea

Point prediction $\hat y(x_0)$ เหมือนกัน แต่ uncertainty ต่าง: CI mean response มีเฉพาะ uncertainty จากการ estimate regression function; PI new response เพิ่ม residual variance ของ observation ใหม่.

## Mathematical Formulation / Technical Detail

Simple regression:
$SE_{mean}=s\sqrt{1/n+(x_0-\bar x)^2/S_{xx}}$.
$SE_{pred}=s\sqrt{1+1/n+(x_0-\bar x)^2/S_{xx}}$.
Intervals = $\hat y_0\pm t^*SE$.

## Worked / Practical Example

ถ้าต้องการ average spending ของลูกค้าที่ age=40 ใช้ confidence interval for mean response; ถ้าต้องการ spending ของลูกค้าคนใหม่หนึ่งคน age=40 ใช้ prediction interval.

## Assumptions / When to use

Classical formulas assume regression model/error structure. Extrapolation far outside observed x range ทำให้ model uncertainty/risk สูงและ formula ไม่แก้ model misspecification.

## Common Mistakes

- ใช้ “prediction interval” เรียก CI ของ mean response
- คิดว่า interval widths เท่ากันเพราะ point estimate เท่ากัน
- สับสนกับ [[Prediction Intervals]] ใน time-series forecasting ซึ่งมี horizon-dependent forecast uncertainty

## Cross-check / Corrections

NIST explicitly distinguishes mean-response confidence interval from single-response prediction interval and notes prediction uncertainty includes residual noise; canonical noteรักษาความแตกต่างนี้ชัดเจน.

## Quick Review

- **Concept:** ใน regression, confidence interval ที่ $x_0$ เป้าหมายคือ **mean response** $E[Y|x_0]$ ส่วน prediction interval เป้าหมายคือ **new individual observation**; prediction interval จึงกว้างกว่าเพราะรวม irreducible observation noise.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Regression Inference]]
- [[Simple Linear Regression]]
- [[Prediction Intervals]]
- [[Confidence Intervals]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[8Correlation-Regression1_2_68_260502_155920]] | Regression confidence and prediction interval sections | mean-response vs new-response intervals |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
