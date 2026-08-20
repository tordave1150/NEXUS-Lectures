---
title: "Complex Seasonality"
aliases:
  - Multiple Seasonality
  - Complex Seasonal Patterns
topic_number: 26
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[09-ComplexSeasonality_DynamicHarmonicReg_260711_130747]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Complex Seasonality

> [!abstract] Summary
> Complex seasonality คือ series ที่มี seasonal periods หลายชุดพร้อมกัน เช่น intraday + weekly + annual patternsใน high-frequency data.

## Why this concept matters

Classical single-season ETS/SARIMAอาจจัดการ long/multiple periodsได้ไม่ดี; ต้องเลือก representation ที่ scalable.

## Core Idea

- Half-hourly electricity: daily $m=48$, weekly $m=336$, annualประมาณ 17532.
- Daily dataอาจมี weekly period 7 และ annualประมาณ365.25.
- Seasonal periodsไม่จำเป็น integerตามธรรมชาติ เช่น 365.25 days/year.
- Calendar effects, holidays และ moving eventsอาจซ้อนกับ regular seasonality.

## Mathematical Formulation / Technical Detail

สำหรับ sampling interval $\Delta$, seasonal periodเป็นจำนวน observationsต่อ cycle.

Half-hourly daily:
$$m_d=24\times2=48.$$

Weekly:
$$m_w=7\times48=336.$$

Annual:
$$m_y\approx365.25\times48=17532.$$

## Worked / Practical Example

Parcel volumeรายชั่วโมงอาจมี intraday cutoff peaks, weekend pattern และ annual peaksก่อน Christmas/Chinese New Year. การ modelแค่ weekly seasonalityจะทิ้ง structureไว้ใน residuals.

## Assumptions and Interpretation

- Period selectionต้องสะท้อน actual operational calendar.
- DST, leap years, missing intervals และ non-business hoursต้องจัด time indexอย่างระมัดระวัง.

## When to use

- high-frequency demand/electricity/calls.
- multiple repeating cycles.

## When not to use / Limitations

- simple seasonal dummies/SARIMAอาจ parameter-heavyเมื่อ m ใหญ่.
- periodic patternที่เปลี่ยน abrupt อาจต้อง interventions/regime featuresเพิ่ม.

## Common Mistakes

- บังคับ annual periodเป็น365เสมอโดยไม่ดู sampling/calendar.
- เรียกทุก recurring promotionว่า regular seasonality.
- ลืม interactionระหว่าง seasons.

## Quick Review

- **Concept:** Complex seasonality คือ series ที่มี seasonal periods หลายชุดพร้อมกัน เช่น intraday + weekly + annual patternsใน high-frequency data.
- **สิ่งที่ต้องจำ:** Half-hourly electricity: daily $m=48$, weekly $m=336$, annualประมาณ 17532.
- **การใช้งาน:** high-frequency demand/electricity/calls.
- **ข้อควรระวัง:** บังคับ annual periodเป็น365เสมอโดยไม่ดู sampling/calendar.

## Related Notes

- [[MSTL Decomposition]]
- [[Harmonic Regression]]
- [[Dynamic Harmonic Regression]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[09-ComplexSeasonality_DynamicHarmonicReg_260711_130747]] | Complex seasonality / multiple seasonal periods section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `09-ComplexSeasonality_DynamicHarmonicReg_260711_130747.pdf` — Complex seasonality / multiple seasonal periods section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
