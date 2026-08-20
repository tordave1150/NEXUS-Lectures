---
title: "ML Time-Series Feature Engineering"
aliases:
  - Time Series Feature Engineering
  - Lag Rolling Fourier Features
topic_number: 54
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[S2-ML_260725_130143]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# ML Time-Series Feature Engineering

> [!abstract] Summary
> ML time-series forecastingแปลง temporal historyเป็น supervised features เช่น lags, rolling statistics, trend index, calendar/Fourier features แล้วใช้ chronological validation.

## Why this concept matters

คุณภาพของ feature engineeringขึ้นกับ information availability; featureที่แตะ targetปัจจุบัน/อนาคตโดยไม่ตั้งใจคือ leakageและทำให้ validationดูดีเกินจริง.

## Core Idea

- Lag featuresต้องมาจากอดีตที่ available.
- Rolling meanสำหรับทำนาย $y_t$ ควรใช้ valuesก่อน t เช่น rolling meanของ $y_{t-1},...,y_{t-k}$.
- Calendar/Fourier features known futureได้.
- Scaling fitบน training foldเท่านั้น.
- One-step vs multi-step deploymentต้องกำหนด feature availabilityต่างกัน.

## Mathematical Formulation / Technical Detail

Valid lag:

$$
x_{t,1}=y_{t-1}.
$$

Past-only rolling mean:

$$
MA_k^{past}(t)=\frac1k\sum_{j=1}^{k}y_{t-j}.
$$

Fourier seasonal feature:

$$
\sin(2\pi t/m),\quad \cos(2\pi t/m).
$$

## Worked / Practical Example

ถ้าต้อง forecast Cement ที่ quarter t, feature `ma4` ต้องไม่รวม Cement_t. ควร shiftก่อน rolling เช่น meanของ t-1..t-4. ใน expanding-window CV preprocessingทุก foldเรียนจากอดีตเท่านั้น.

## Assumptions and Interpretation

- Feature timestampsต้อง auditเทียบ prediction timestamp.
- Forecasted external variablesต้องไม่ถูกแทนด้วย actual future valuesใน validation.

## When to use

- tree/linear/NN modelsสำหรับ time series.
- rich calendar/lag/rolling features.

## When not to use / Limitations

- เมื่อ recursive multi-step featuresต้องใช้ own predictions error accumulationจะเกิด.
- small data + many engineered featuresเสี่ยง overfit.

## Common Mistakes

- rolling targetรวม current rowแล้วใช้ predict current target.
- normalizeก่อน split.
- random CV.
- ใช้ centered moving averageที่มี future observations.

## Cross-check / Correction

> [!warning] Verification note
> โค้ด lecture ที่สร้าง `ma4 = slide_dbl(Cement, mean, .before=3)` แล้วใช้ `Cement` เป็น targetในแถวเดียวกัน มีความเสี่ยง target leakage เพราะ rolling meanรวม `Cement_t`. สำหรับการทำนาย $y_t$ ต้อง shift/lag rolling featureให้ใช้เฉพาะ $y_{t-1}$ และอดีตกว่า เว้นแต่ datasetถูกจัดให้ row t ใช้ forecast t+1 อย่างชัดเจน.

## Quick Review

- **Concept:** ML time-series forecastingแปลง temporal historyเป็น supervised features เช่น lags, rolling statistics, trend index, calendar/Fourier features แล้วใช้ chronological validation.
- **สิ่งที่ต้องจำ:** Lag featuresต้องมาจากอดีตที่ available.
- **การใช้งาน:** tree/linear/NN modelsสำหรับ time series.
- **ข้อควรระวัง:** rolling targetรวม current rowแล้วใช้ predict current target.

## Related Notes

- [[Lagged Variables and Lag Plots]]
- [[Time Series Cross Validation]]
- [[Regularized Regression]]
- [[Ensemble Learning]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[S2-ML_260725_130143]] | ML models for time series — feature engineering / expanding-window CV | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `S2-ML_260725_130143.pdf` — ML models for time series — feature engineering / expanding-window CV

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
