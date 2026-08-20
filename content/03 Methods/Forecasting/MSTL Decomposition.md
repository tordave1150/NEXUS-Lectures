---
title: "MSTL Decomposition"
aliases:
  - MSTL
  - Multiple Seasonal STL
topic_number: 27
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

# MSTL Decomposition

> [!abstract] Summary
> MSTL ขยาย STL เพื่อแยก multiple seasonal components พร้อม trend และ remainder โดย seasonal patternsสามารถ evolve อย่างค่อยเป็นค่อยไป.

## Why this concept matters

MSTL เหมาะสำหรับ exploratory analysisและ decomposition forecastingของ complex seasonal series โดยไม่ต้องสร้าง dummyมหาศาล.

## Core Idea

- MSTL decompositionเป็น additiveบน transformed scaleที่ใช้.
- แต่ละ seasonal componentมี periodของตนเอง.
- Seasonally adjusted seriesนำ seasonal componentsทั้งหมดออก.
- STL/MSTLสามารถใช้ robust fittingเพื่อลดอิทธิพล outliers.

## Mathematical Formulation / Technical Detail

Multiple-season additive representation:

$$
y_t=T_t+S_t^{(1)}+S_t^{(2)}+\cdots+R_t.
$$

Seasonally adjusted:

$$
y_t^{adj}=y_t-\sum_jS_t^{(j)}.
$$

## Worked / Practical Example

Pedestrian dataรายวันอาจแยก weekly componentกับ annual component. Mondayสองวันอาจมี weekly effectใกล้กัน แต่ annual effectต่างกันมาก จึงมี seasonally adjusted valuesต่างกัน.

## Assumptions and Interpretation

- MSTL componentsเป็น estimated smooth patterns ไม่ใช่ causal components.
- Forecasting seasonal componentsมักใช้ seasonal-naïve continuation ขณะที่ adjusted seriesใช้ nonseasonal model.

## When to use

- explore multiple seasonality.
- preprocess/decomposition forecasting.
- robust seasonal adjustment.

## When not to use / Limitations

- ถ้า seasonality fixedและต้องการ parsimonious regression DHRอาจเหมาะกว่า.
- forecast uncertaintyของ two-stage decompositionต้องพิจารณา.

## Common Mistakes

- คิดว่า same weekdayต้องมี total seasonal adjustmentเท่ากัน.
- ลืม transformation/back-transformation bias.
- ตีความ remainderเป็น white noiseโดยไม่ตรวจ.

## Quick Review

- **Concept:** MSTL ขยาย STL เพื่อแยก multiple seasonal components พร้อม trend และ remainder โดย seasonal patternsสามารถ evolve อย่างค่อยเป็นค่อยไป.
- **สิ่งที่ต้องจำ:** MSTL decompositionเป็น additiveบน transformed scaleที่ใช้.
- **การใช้งาน:** explore multiple seasonality.
- **ข้อควรระวัง:** คิดว่า same weekdayต้องมี total seasonal adjustmentเท่ากัน.

## Related Notes

- [[Complex Seasonality]]
- [[Dynamic Harmonic Regression]]
- [[Time Series Decomposition]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[09-ComplexSeasonality_DynamicHarmonicReg_260711_130747]] | MSTL decomposition / decomposition forecasting section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `09-ComplexSeasonality_DynamicHarmonicReg_260711_130747.pdf` — MSTL decomposition / decomposition forecasting section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
