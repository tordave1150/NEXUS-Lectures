---
title: "AIC AICc BIC"
aliases:
  - AIC
  - AICc
  - BIC
  - Information Criteria
topic_number: 46
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[13-probabilistic-forecast_260725_090945]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# AIC AICc BIC

> [!abstract] Summary
> AIC, AICc และ BIC เปรียบเทียบ candidate likelihood modelsโดย trade off goodness of fitกับจำนวน parameters; ค่ายิ่งต่ำดีกว่าในชุด modelsที่ comparable.

## Why this concept matters

Information criteriaช่วยเลือก complexityโดยไม่ต้อง hold outข้อมูลทุกครั้ง แต่เป็น relative criteria ไม่ใช่ absolute goodness score.

## Core Idea

- AICเน้น estimated predictive information loss.
- AICcเพิ่ม small-sample correctionและเข้าใกล้ AICเมื่อ nใหญ่.
- BICลงโทษ complexityแรงขึ้นประมาณ $k\log n$.
- ต้องนับ free parametersให้สอดคล้องกับ likelihood/software เช่น residual varianceอาจถูกนับ.

## Mathematical Formulation / Technical Detail

ให้ maximized log-likelihood $\ell(\hat\theta)$ และจำนวน parameters $k$:

$$
AIC=2k-2\ell(\hat\theta).
$$

$$
BIC=k\log n-2\ell(\hat\theta).
$$

$$
AICc=AIC+\frac{2k(k+1)}{n-k-1}.
$$

## Worked / Practical Example

ถ้า linear model AIC=52.20 และ quadratic=52.13 ความต่าง 0.07 เล็กมาก แม้ quadraticต่ำกว่าเล็กน้อย modelง่ายยัง defensibleหาก interpretabilityสำคัญ. อย่าตีความ 0.07 ว่า improvementใหญ่.

## Assumptions and Interpretation

- เปรียบ modelsบน response, observations และ likelihoodฐานเดียวกัน.
- AIC difference—not raw magnitude—isสิ่งที่มีความหมายในการ ranking.

## When to use

- select ARIMA/ETS/lag order/candidate regression.
- small nใช้ AICcเป็น defaultที่ดี.

## When not to use / Limitations

- ไม่ใช้ AICเปรียบ modelคนละ target scaleหลัง transformationโดยไม่ปรับ likelihood/Jacobian.
- ไม่ใช่ substituteของ out-of-sample validationทุกกรณี.

## Common Mistakes

- พูดว่า AICยิ่งมากยิ่งดี — ที่ถูกคือยิ่งต่ำยิ่งดี.
- นับ parametersไม่ครบ.
- ตีความ AICเป็น probabilityหรือ accuracy percentage.

## Quick Review

- **Concept:** AIC, AICc และ BIC เปรียบเทียบ candidate likelihood modelsโดย trade off goodness of fitกับจำนวน parameters; ค่ายิ่งต่ำดีกว่าในชุด modelsที่ comparable.
- **สิ่งที่ต้องจำ:** AICเน้น estimated predictive information loss.
- **การใช้งาน:** select ARIMA/ETS/lag order/candidate regression.
- **ข้อควรระวัง:** พูดว่า AICยิ่งมากยิ่งดี — ที่ถูกคือยิ่งต่ำยิ่งดี.

## Related Notes

- [[Likelihood MLE NLL]]
- [[ETS Models and Model Selection]]
- [[Time Series Cross Validation]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[13-probabilistic-forecast_260725_090945]] | Information criteria / model selection section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `13-probabilistic-forecast_260725_090945.pdf` — Information criteria / model selection section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
