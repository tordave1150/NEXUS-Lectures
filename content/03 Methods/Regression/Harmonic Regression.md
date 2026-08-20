---
title: "Harmonic Regression"
aliases:
  - Fourier Regression
  - Harmonic Regression
  - Fourier Terms
topic_number: 28
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

# Harmonic Regression

> [!abstract] Summary
> Harmonic regressionใช้ sine-cosine Fourier pairsเป็น predictorsเพื่อแทน smooth seasonalityด้วย parametersจำนวนน้อยกว่า seasonal dummies โดยเฉพาะเมื่อ seasonal periodยาว.

## Why this concept matters

Fourier basis compresses seasonal shape; ค่า $K$ ควบคุมความละเอียดของ curveและเป็น tuning parameter.

## Core Idea

- แต่ละ harmonic $k$ ใช้ sineและcosineหนึ่งคู่.
- $K$ สูงขึ้นทำให้ seasonal shape flexibleขึ้นแต่เสี่ยง overfit.
- สำหรับ integer period $m$, $K$ ไม่เกินประมาณ $m/2$ เนื่องจาก redundancy.
- Harmonic regressionอย่างง่ายมักสมมติ residuals white noise.

## Mathematical Formulation / Technical Detail

สำหรับ seasonal period $m$:

$$
y_t=\beta_0+
\sum_{k=1}^{K}
\left[
a_k\sin\left(\frac{2\pi kt}{m}\right)
+b_k\cos\left(\frac{2\pi kt}{m}\right)
\right]+\varepsilon_t.
$$

## Worked / Practical Example

Monthly series $m=12$, $K=2$ ใช้ 4 Fourier predictors. Curveจะ smoothกว่าการใช้ 11 month dummies และลดจำนวน parameters.

## Assumptions and Interpretation

- Fourier terms represent deterministic periodic pattern.
- Trend/external predictorsสามารถเพิ่มเข้า regressionได้.

## When to use

- long but smooth seasonality.
- ลด dimensionalityจาก dummies.
- multiple seasonal periodsโดยใส่ Fourier termsแต่ละ period.

## When not to use / Limitations

- abrupt seasonal shapesอาจต้อง Kสูงหรือ alternative.
- residual autocorrelationต้องแก้ด้วย DHR.

## Common Mistakes

- เลือก Kจาก training fitอย่างเดียว.
- คิดว่า K=m ให้รายละเอียดเพิ่มเสมอ.
- ลืม time index regularity.

## Quick Review

- **Concept:** Harmonic regressionใช้ sine-cosine Fourier pairsเป็น predictorsเพื่อแทน smooth seasonalityด้วย parametersจำนวนน้อยกว่า seasonal dummies โดยเฉพาะเมื่อ seasonal periodยาว.
- **สิ่งที่ต้องจำ:** แต่ละ harmonic $k$ ใช้ sineและcosineหนึ่งคู่.
- **การใช้งาน:** long but smooth seasonality.
- **ข้อควรระวัง:** เลือก Kจาก training fitอย่างเดียว.

## Related Notes

- [[Seasonal Dummy Variables and Interaction]]
- [[Dynamic Harmonic Regression]]
- [[Complex Seasonality]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[09-ComplexSeasonality_DynamicHarmonicReg_260711_130747]] | Fourier terms / harmonic regression section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `09-ComplexSeasonality_DynamicHarmonicReg_260711_130747.pdf` — Fourier terms / harmonic regression section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
