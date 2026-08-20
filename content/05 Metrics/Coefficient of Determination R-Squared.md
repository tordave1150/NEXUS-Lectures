---
title: "Coefficient of Determination R-Squared"
topic_number: 157
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - regression
  - metric
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Coefficient of Determination R-Squared

> [!abstract] Summary
> $R^2$ measures the fraction of response sum-of-squares explained by a regression model relative to an intercept-only baseline; adjusted $R^2$ penalizes adding predictors through degrees of freedom.

## Why this concept matters

ช่วยสรุป in-sample fit แต่ไม่ใช่ forecast accuracy, causal validity หรือ guarantee ว่า model assumptions ถูกต้อง.

## Core Idea

For OLS with intercept, $R^2=1-SSE/SST=SSR/SST$. In simple linear regression with intercept, $R^2=r_{XY}^2$. In multiple regression, $R=\sqrt{R^2}$ is nonnegative multiple correlation between observed and fitted response under standard definitions.

## Mathematical Formulation / Technical Detail

Adjusted $R^2=1-(1-R^2)\frac{n-1}{n-k-1}$ where $k$ = number of predictors (excluding intercept).

## Worked / Practical Example

Model A $R^2=.80$ และ Model B $R^2=.82$ ไม่ได้แปลว่า B forecast ดีกว่า; ต้องดู validation/test performance และ model purpose.

## Assumptions / When to use

Interpretation above assumes conventional OLS with intercept; models without intercept can have nonstandard/negative behavior depending definition.

## Common Mistakes

- บอกว่า $R^2=0.8$ แปลว่า “X ทำให้ Y เปลี่ยน 80%”
- ใช้ training $R^2$ เลือก model ซับซ้อนโดยไม่ validate
- คิดว่า high $R^2$ = unbiased/causal model

## Cross-check / Corrections

Lecture states multiple correlation coefficient notation ambiguously in extraction (“R = R2”). Canonical relation is **$R=\sqrt{R^2}$**, and in simple regression with intercept $R=|r|$.

## Quick Review

- **Concept:** $R^2$ measures the fraction of response sum-of-squares explained by a regression model relative to an intercept-only baseline; adjusted $R^2$ penalizes adding predictors through degrees of freedom.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Simple Linear Regression]]
- [[Multiple Linear Regression]]
- [[Regression Inference]]
- [[Forecast Accuracy Metrics]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[8Correlation-Regression1_2_68_260502_155920]] | Model suitability / R-square sections | R2 and adjusted R2 |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
