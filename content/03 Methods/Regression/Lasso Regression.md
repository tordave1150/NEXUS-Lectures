---
title: "Lasso Regression"
aliases:
  - Lasso
  - L1 Regularization
topic_number: 36
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[11-RegularizedRegression_260718_091112]]"
  - "[[DADS6003 Week 6 - Regularization]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Lasso Regression

> [!abstract] Summary
> Lasso ใช้ L1 penalty ทำให้บาง coefficientsถูก shrinkเป็นศูนย์พอดี จึงทำ regularizationและ embedded feature selectionพร้อมกัน.

## Why this concept matters

Lassoมีประโยชน์เมื่อเชื่อว่า signal sparse แต่เมื่อ predictors correlatedแรงอาจเลือกหนึ่งตัวและทิ้งตัวอื่นอย่างไม่เสถียร.

## Core Idea

- L1 geometryสร้าง exact zeros.
- $\lambda$ ควบคุม sparsity.
- Feature selectionของ Lassoเป็น prediction-drivenไม่ใช่ causal screening.
- เมื่อ $p>n$ Lassoยัง fitได้แต่จำนวน selected featuresและ stabilityต้องระวัง.

## Mathematical Formulation / Technical Detail

Lasso objective:

$$
\min_{\beta_0,\beta}
\frac1n\sum_i(y_i-\beta_0-x_i^\top\beta)^2
+\lambda\sum_{j=1}^p|\beta_j|.
$$

## Worked / Practical Example

ถ้ามี lag features 1–20 แต่ true predictive signalอยู่บาง lags Lassoอาจ setหลาย coefficientsเป็น zero. หาก lag 4และ lag 8 correlatedสูง selectionอาจสลับกันระหว่าง folds.

## Assumptions and Interpretation

- Standardize features.
- CV errorและ selection stabilityควรดูคู่กัน.

## When to use

- sparse prediction.
- feature screeningเมื่อ pมาก.

## When not to use / Limitations

- highly correlated groupsที่อยากเก็บร่วมกัน → Elastic Net/Group Lassoอาจดีกว่า.

## Common Mistakes

- ตีความ selected=importantทาง causal.
- เลือก lambda.minเสมอโดยไม่คิด sparsity/1-SE tradeoff.
- ไม่ตรวจ stabilityข้าม folds.

## Quick Review

- **Concept:** Lasso ใช้ L1 penalty ทำให้บาง coefficientsถูก shrinkเป็นศูนย์พอดี จึงทำ regularizationและ embedded feature selectionพร้อมกัน.
- **สิ่งที่ต้องจำ:** L1 geometryสร้าง exact zeros.
- **การใช้งาน:** sparse prediction.
- **ข้อควรระวัง:** ตีความ selected=importantทาง causal.

## Related Notes

- [[Regularized Regression]]
- [[Ridge Regression]]
- [[Elastic Net]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[11-RegularizedRegression_260718_091112]] | Lasso regression section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `11-RegularizedRegression_260718_091112.pdf` — Lasso regression section

## External References

- [scikit-learn User Guide — Linear Models (Ridge, Lasso, Elastic Net, Logistic Regression).](https://scikit-learn.org/stable/modules/linear_model.html)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น

## DADS6003 Enrichment

L1 geometry มีมุมที่แกน จึงทำให้ optimum สามารถเกิดที่ coefficient เท่ากับศูนย์และทำ embedded feature selection ได้. เนื่องจาก L1 penalty ไม่ differentiable ที่ศูนย์ practical solvers มักใช้ coordinate descent หรือ proximal-style methods แทนการคิดว่า plain gradient descent ใช้ได้โดยไม่มีข้อพิจารณา.

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 6 - Regularization]] | Slides 14–18, 22–27 | Lasso sparsity, use cases and geometry |
