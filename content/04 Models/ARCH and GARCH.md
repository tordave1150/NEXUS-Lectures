---
title: "ARCH and GARCH"
aliases:
  - ARCH
  - GARCH
  - Conditional Volatility
topic_number: 51
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[S1-StatFC_260725_130111]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# ARCH and GARCH

> [!abstract] Summary
> ARCH/GARCH modelsทำให้ conditional varianceเปลี่ยนตามเวลาและจับ volatility clustering; ARCHใช้ past squared shocks ส่วน GARCHเพิ่ม past conditional varianceเพื่อ memoryที่ยาวขึ้น.

## Why this concept matters

ใน financial/economic series varianceไม่คงที่แม้ conditional meanเรียบ; forecasting volatilityสำคัญต่อ risk, intervalsและdecisions.

## Core Idea

- Model meanและvarianceแยกกัน: $\varepsilon_t=\sigma_t z_t$.
- ARCH(1) varianceขึ้นกับ $\varepsilon_{t-1}^2$.
- GARCH(1,1)เพิ่ม $\sigma_{t-1}^2$.
- Positivity constraintsช่วยให้ varianceไม่ติดลบ.
- สำหรับ standard GARCH(1,1), $\alpha+\beta<1$ เป็นเงื่อนไข covariance stationarityที่พบบ่อย.

## Mathematical Formulation / Technical Detail

ARCH(1):

$$
\varepsilon_t=\sigma_t z_t,\quad E(z_t)=0,\ Var(z_t)=1
$$

$$
\sigma_t^2=\omega+\alpha\varepsilon_{t-1}^2.
$$

GARCH(1,1):

$$
\sigma_t^2=\omega+\alpha\varepsilon_{t-1}^2+\beta\sigma_{t-1}^2.
$$

## Worked / Practical Example

Return seriesอาจมีช่วง quietสลับ burst. Large shockเมื่อวานเพิ่ม conditional varianceวันนี้ผ่าน $\alpha\varepsilon_{t-1}^2$; betaสูงทำให้ volatility decayช้า.

## Assumptions and Interpretation

- Usually fit returns/innovations ไม่ใช่ raw trending prices.
- Innovation distributionอาจ normal, Student-t ฯลฯ.
- GARCH(p,q) order conventionต่างกันในบาง literature/software.

## When to use

- financial returns.
- forecast time-varying variance.
- risk modeling.

## When not to use / Limitations

- level forecastingที่ varianceคงที่ไม่จำเป็นต้อง GARCH.
- structural breaksอาจ mimic volatility persistence.

## Common Mistakes

- fit GARCHกับ nonstationary price levelโดยไม่คิด.
- สับสน volatilityกับ directionของ return.
- copy GARCH(p,q) notationข้าม softwareโดยไม่ตรวจ convention.

## Cross-check / Correction

> [!warning] Verification note
> Lecture ระบุถูกต้องว่ามี GARCH(p,q) naming conventionsต่างกันระหว่างแหล่ง/ซอฟต์แวร์ จึงควรเขียน variance equationกำกับทุกครั้ง.

## Quick Review

- **Concept:** ARCH/GARCH modelsทำให้ conditional varianceเปลี่ยนตามเวลาและจับ volatility clustering; ARCHใช้ past squared shocks ส่วน GARCHเพิ่ม past conditional varianceเพื่อ memoryที่ยาวขึ้น.
- **สิ่งที่ต้องจำ:** Model meanและvarianceแยกกัน: $\varepsilon_t=\sigma_t z_t$.
- **การใช้งาน:** financial returns.
- **ข้อควรระวัง:** fit GARCHกับ nonstationary price levelโดยไม่คิด.

## Related Notes

- [[Probabilistic Forecasting]]
- [[VaR and CVaR]]
- [[AR MA ARMA]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[S1-StatFC_260725_130111]] | Heteroskedasticity / ARCH & GARCH section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `S1-StatFC_260725_130111.pdf` — Heteroskedasticity / ARCH & GARCH section

## External References

- [Engle, R.F. (1982), Autoregressive Conditional Heteroscedasticity with Estimates of the Variance of United Kingdom Inflation, Econometrica 50(4), 987–1007.](https://doi.org/10.2307/1912773)
- [Bollerslev, T. (1986), Generalized Autoregressive Conditional Heteroskedasticity, Journal of Econometrics 31(3), 307–327.](https://doi.org/10.1016/0304-4076(86)90063-1)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
