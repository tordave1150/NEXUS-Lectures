---
title: "Dynamic Harmonic Regression"
aliases:
  - DHR
  - Fourier Terms with ARIMA Errors
topic_number: 29
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

# Dynamic Harmonic Regression

> [!abstract] Summary
> Dynamic Harmonic Regression (DHR) ใช้ Fourier termsแทน seasonality และ ARIMA errorsจับ short-term serial dependence จึงเหมาะกับ long/complex seasonality.

## Why this concept matters

DHR แยก deterministic smooth seasonal patternออกจาก stochastic residual dynamicsและสามารถเพิ่ม external predictors/trendได้.

## Core Idea

- Seasonality encodedด้วย Fourier pairs.
- Non-seasonal ARIMA errorsจับ remaining autocorrelation.
- เลือก $K$ ด้วย AICc/CVและตรวจ residuals.
- หลาย seasonal periodsสามารถใส่ Fourier blocksหลายชุด.

## Mathematical Formulation / Technical Detail

Single period:

$$
y_t=\beta_0+
\sum_{k=1}^{K}\left[
a_k\sin(2\pi kt/m)+b_k\cos(2\pi kt/m)
\right]+\eta_t,
$$

โดย

$$
\eta_t\sim ARIMA(p,d,q).
$$

## Worked / Practical Example

Monthly restaurant expenditureอาจ log-transform แล้วใช้ Fourier $K=2$ + ARIMA errors. ถ้า seasonal dummy regressionเหลือ ACF1สูงแต่ DHR residualsใกล้ white noise DHRใช้ temporal informationได้ครบกว่า.

## Assumptions and Interpretation

- DHR assumes seasonal basis pattern fixed unless coefficients/time interactionsเปลี่ยน.
- ARIMA errorควร non-seasonalเมื่อ Fourier termsจัด seasonalityแล้วใน common formulation.

## When to use

- long seasonal periods.
- multiple seasonality.
- ต้องการ parsimonious seasonal regression + stochastic errors.

## When not to use / Limitations

- seasonal patternที่ evolveเร็วอาจ MSTLเหมาะกว่า.
- Kสูงมากเพิ่ม overfitting.

## Common Mistakes

- ใช้ threshold |ACF1|>0.3 เป็น universal law; เป็นเพียง rough heuristic.
- เลือก Kจาก test set.
- ซ้ำ seasonal ARIMA termsกับ Fourierจน modelไม่จำเป็นซับซ้อน.

## Cross-check / Correction

> [!warning] Verification note
> ค่า |ACF1| > 0.3 ที่ปรากฏใน lecture ควรเก็บเป็น rough diagnostic guideline ไม่ใช่ universal statistical cutoff; ใช้ residual ACFทั้งชุดและ Ljung-Boxร่วมด้วย.

## Quick Review

- **Concept:** Dynamic Harmonic Regression (DHR) ใช้ Fourier termsแทน seasonality และ ARIMA errorsจับ short-term serial dependence จึงเหมาะกับ long/complex seasonality.
- **สิ่งที่ต้องจำ:** Seasonality encodedด้วย Fourier pairs.
- **การใช้งาน:** long seasonal periods.
- **ข้อควรระวัง:** ใช้ threshold |ACF1|>0.3 เป็น universal law; เป็นเพียง rough heuristic.

## Related Notes

- [[Harmonic Regression]]
- [[MSTL Decomposition]]
- [[Dynamic Regression ARIMAX]]
- [[Complex Seasonality]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[09-ComplexSeasonality_DynamicHarmonicReg_260711_130747]] | Dynamic harmonic regression section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `09-ComplexSeasonality_DynamicHarmonicReg_260711_130747.pdf` — Dynamic harmonic regression section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
