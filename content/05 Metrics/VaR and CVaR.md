---
title: "VaR and CVaR"
aliases:
  - Value at Risk
  - Conditional Value at Risk
  - Expected Shortfall
topic_number: 50
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[02-probabilistic-forecast]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# VaR and CVaR

> [!abstract] Summary
> VaR คือ loss quantileที่ระดับ confidenceหนึ่ง ส่วน CVaR/Expected Shortfallสรุป average severityใน tailเกิน VaR (สำหรับ continuous case), จึงให้ข้อมูล tail riskมากกว่า VaRจุดเดียว.

## Why this concept matters

Risk-averse decisionsต้องสนใจ distribution tail ไม่ใช่แค่ expected loss.

## Core Idea

- กำหนด signให้ชัด: ใน note นี้ $L$ เป็น loss ค่ามาก=แย่.
- VaR$_\alpha$คือ $\alpha$-quantileของ loss.
- CVaRสำหรับ continuous distributionคือ conditional meanเหนือ VaR.
- Expected Shortfallมีคุณสมบัติด้าน coherent riskที่ VaRไม่มีบางข้อ.

## Mathematical Formulation / Technical Detail

For continuous loss $L$:

$$
VaR_\alpha=F_L^{-1}(\alpha).
$$

$$
CVaR_\alpha=E[L\mid L\ge VaR_\alpha].
$$

ถ้า $L\sim N(\mu,\sigma^2)$:

$$
VaR_\alpha=\mu+\sigma z_\alpha,
$$

$$
ES_\alpha=\mu+\sigma\frac{\phi(z_\alpha)}{1-\alpha}.
$$

## Worked / Practical Example

Loss mean=-2.5, sd=3.7 และ α=0.90: VaR≈-2.5+3.7(1.2816)≈2.24 ตาม lecture. แปลว่า 90th percentileของ lossประมาณ 2.24 ภายใต้ normal model.

## Assumptions and Interpretation

- สำหรับ discrete distributions นิยาม conditional mean tailต้องระวัง massที่ VaR; optimization/general ES definitionแม่นกว่า.
- VaR/CVaRขึ้นกับ distribution modelและ tail assumptions.

## When to use

- financial/operational tail risk.
- risk-constrained inventory/capacity.

## When not to use / Limitations

- อย่าใช้ normal formulaหาก tails/skewไม่เหมาะโดยไม่ validate.
- CVaRของ gain variableมี sign conventionต่างจาก loss.

## Common Mistakes

- สลับเครื่องหมาย profit/loss.
- คิดว่า VaRคือ maximum possible loss.
- รายงาน CVaRโดยไม่ระบุ alpha.

## Quick Review

- **Concept:** VaR คือ loss quantileที่ระดับ confidenceหนึ่ง ส่วน CVaR/Expected Shortfallสรุป average severityใน tailเกิน VaR (สำหรับ continuous case), จึงให้ข้อมูล tail riskมากกว่า VaRจุดเดียว.
- **สิ่งที่ต้องจำ:** กำหนด signให้ชัด: ใน note นี้ $L$ เป็น loss ค่ามาก=แย่.
- **การใช้งาน:** financial/operational tail risk.
- **ข้อควรระวัง:** สลับเครื่องหมาย profit/loss.

## Related Notes

- [[Probabilistic Forecasting]]
- [[Quantile Forecast and Quantile Score]]
- [[CRPS]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[02-probabilistic-forecast]] | Risk analysis: VaR and CVaR section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `02-probabilistic-forecast.pdf` — Risk analysis: VaR and CVaR section

## External References

- [Gneiting, T. & Raftery, A.E. (2007), Strictly Proper Scoring Rules, Prediction, and Estimation, JASA 102(477), 359–378.](https://doi.org/10.1198/016214506000001437)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
