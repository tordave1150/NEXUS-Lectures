---
title: "ETS Models and Model Selection"
aliases:
  - ETS State Space Models
  - ETS Taxonomy
  - ETS Model Selection
topic_number: 12
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[04-ETS]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# ETS Models and Model Selection

> [!abstract] Summary
> ETS state-space framework ระบุ Error, Trend และ Seasonal components อย่างเป็นระบบ ทำให้ exponential smoothing methods มี probabilistic model, likelihood และ prediction intervals.

## Why this concept matters

การมี statistical model ชัดเจนช่วยให้ estimate parameters, compare candidate specifications ด้วย information criteria และสร้าง forecast distributions.

## Core Idea

- ETS notation มักเขียน ETS(E,T,S) เช่น ETS(A,A,N).
- Error อาจ additive (A) หรือ multiplicative (M).
- Trend อาจ none (N), additive (A), damped additive (Ad) และบาง frameworks มี multiplicative forms.
- Seasonality อาจ none/additive/multiplicative.
- AICc นิยมใช้เลือก candidate ETS models ภายใต้ likelihood framework.

## Mathematical Formulation / Technical Detail

ตัวอย่าง ETS(A,N,N):

$$
y_t=\ell_{t-1}+\varepsilon_t,\qquad
\ell_t=\ell_{t-1}+\alpha\varepsilon_t.
$$

Point forecast ยังเทียบเท่า SES แต่ state-space form ทำให้ error distribution และ forecast variance ถูกนิยาม.

## Worked / Practical Example

Series level-only อาจเลือก ETS(A,N,N). Series มี trend ไม่มี seasonalityอาจเลือก ETS(A,A,N) หรือ damped variant. Selection ควรตรวจ AICc, residual diagnostics และ out-of-sample accuracyร่วมกัน.

## Assumptions and Interpretation

- Information criteria เปรียบเทียบ models fitted บน response/data เดียวกันภายใต้ comparable likelihood.
- Lowest AICc ไม่รับประกันดีที่สุดบน future data; validation ยังมีคุณค่า.

## When to use

- automatic ETS model search.
- ต้องการ probabilistic forecasts จาก exponential smoothing family.

## When not to use / Limitations

- อย่าเปรียบเทียบ AIC ระหว่าง models ที่ใช้คนละ response transformation/คนละ observations โดยไม่ระวัง.
- multiplicative error/seasonality ต้องตรวจข้อจำกัดของ data.

## Common Mistakes

- สับสน 'method' กับ stochastic state-space model.
- เลือกจาก AIC อย่างเดียวไม่ดู residuals.
- คิดว่า multiplicative components ใช้ได้กับ zero/negative series แบบตรง ๆ.

## Quick Review

- **Concept:** ETS state-space framework ระบุ Error, Trend และ Seasonal components อย่างเป็นระบบ ทำให้ exponential smoothing methods มี probabilistic model, likelihood และ prediction intervals.
- **สิ่งที่ต้องจำ:** ETS notation มักเขียน ETS(E,T,S) เช่น ETS(A,A,N).
- **การใช้งาน:** automatic ETS model search.
- **ข้อควรระวัง:** สับสน 'method' กับ stochastic state-space model.

## Related Notes

- [[Exponential Smoothing and ETS]]
- [[AIC AICc BIC]]
- [[Prediction Intervals]]
- [[ETS vs ARIMA]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[04-ETS]] | ETS taxonomy / methods vs models / model selection section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `04-ETS.pdf` — ETS taxonomy / methods vs models / model selection section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
