---
title: "Introduction to Time Series Forecasting"
aliases:
  - Time Series Forecasting
  - Introduction to Time Series
  - TS Forecasting
topic_number: 1
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

# Introduction to Time Series Forecasting

> [!abstract] Summary
> Time Series Forecasting คือการใช้ข้อมูลที่เรียงตามเวลาเพื่อประมาณค่าที่จะเกิดในอนาคต โดยต้องรักษาความหมายของลำดับเวลา frequency และ forecast horizon.

## Why this concept matters

Time ordering ทำให้ observations อาจพึ่งพาอดีตของตนเอง การเข้าใจ index, frequency, trend, seasonality และ uncertainty จึงเป็นพื้นฐานก่อนเลือก model.

## Core Idea

- Time index บอกว่า observation เกิดเมื่อใด และ $h$ คือ forecast horizon.
- Time series ต่างจาก cross-sectional data เพราะ ordering มีความหมาย.
- รูปแบบพื้นฐานที่ควรมองหา ได้แก่ level, trend, seasonality และ cycle.
- การ forecast ไม่เท่ากับ causal explanation; ถ้าต้องการอธิบายสาเหตุอาจต้องใช้ predictors.

## Mathematical Formulation / Technical Detail

ให้ข้อมูลถึงเวลา $T$ เป็น $y_1,\ldots,y_T$ แล้ว forecast $h$ ช่วงข้างหน้าเขียนเป็น

$$
\hat y_{T+h|T}.
$$

ตัวห้อยหลังเครื่องหมาย `|` ระบุข้อมูลที่ใช้สร้าง forecast. เช่น $\hat y_{T+1|T}$ คือ one-step-ahead forecast.

## Worked / Practical Example

ถ้าข้อมูลรายไตรมาสสิ้นสุดที่ 2002 Q4 และต้อง forecast 2003 Q1 จะมี $h=1$; ถ้าจะ forecast 2003 Q4 จะมี $h=4$. ก่อนเลือก model ควร plot series และถามว่ามี trend หรือ seasonal period $m=4$ หรือไม่.

## Assumptions and Interpretation

- หลาย classical forecasting methods ออกแบบมาสำหรับ regularly spaced observations.
- Missing date ไม่ได้แปลว่า zero; ต้องอาศัย domain knowledge.
- Forecast uncertainty มักเพิ่มเมื่อ horizon ไกลขึ้น.

## When to use

- ใช้เป็นกรอบเริ่มต้นเมื่อเจอ time-series dataset ใหม่.
- ใช้กำหนด forecasting objective, horizon และ data preparation plan.

## When not to use / Limitations

- ไม่ใช้ time-series method โดยไม่ตรวจ temporal ordering.
- ไม่ควรสรุป causality จาก trend ในกราฟเวลา.

## Common Mistakes

- Randomly shuffle train/test จนอาจเกิด future-to-past leakage.
- เติม missing period เป็น 0 โดยไม่ตรวจความหมายทางธุรกิจ.
- มอง point forecast เป็นค่าที่จะเกิดขึ้นแน่นอน.

## Cross-check / Correction

> [!warning] Verification note
> คำว่า “standard time-series methods assume equal spacing” ควรตีความว่า classical methods จำนวนมากต้องการ/สมมติ regular spacing ไม่ใช่ว่า time series ทุกชนิดบนโลกต้องมีช่วงเวลาห่างเท่ากัน.

## Quick Review

- **Concept:** Time Series Forecasting คือการใช้ข้อมูลที่เรียงตามเวลาเพื่อประมาณค่าที่จะเกิดในอนาคต โดยต้องรักษาความหมายของลำดับเวลา frequency และ forecast horizon.
- **สิ่งที่ต้องจำ:** Time index บอกว่า observation เกิดเมื่อใด และ $h$ คือ forecast horizon.
- **การใช้งาน:** ใช้เป็นกรอบเริ่มต้นเมื่อเจอ time-series dataset ใหม่.
- **ข้อควรระวัง:** Randomly shuffle train/test จนอาจเกิด future-to-past leakage.

## Related Notes

- [[Benchmark Forecasting Methods]]
- [[Forecast Accuracy Metrics]]
- [[Time Series Decomposition]]
- [[Time Series Cross Validation]]
- [[Probabilistic Forecasting]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[01-TSoverview]] | Introduction / early slides | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `01-TSoverview.pdf` — Introduction / early slides

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
