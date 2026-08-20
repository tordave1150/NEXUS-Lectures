---
title: "Elastic Net"
aliases:
  - ElasticNet
  - L1 L2 Regularization
topic_number: 37
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

# Elastic Net

> [!abstract] Summary
> Elastic Net ผสม L1 และ L2 penalties เพื่อได้ sparsityแบบ Lassoพร้อม grouping/stabilityต่อ correlated predictorsคล้าย Ridge.

## Why this concept matters

เหมาะมากเมื่อ predictorsจำนวนมากและมี correlated clusters เช่น lagged featuresหรือ economic indicators.

## Core Idea

- Mixing parameterกำหนดสัดส่วน L1 vs L2.
- Regularization strengthและ mixingต้อง tune.
- L1 componentสร้าง zeros; L2 componentช่วย correlated featuresอยู่ร่วมกัน.
- Scalingยังจำเป็น.

## Mathematical Formulation / Technical Detail

หนึ่งรูปแบบ objective:

$$
\min_{\beta_0,\beta}
\frac1n\sum_i(y_i-\beta_0-x_i^\top\beta)^2
+\lambda\left[
\alpha\|\beta\|_1+
\frac{1-\alpha}{2}\|\beta\|_2^2
\right].
$$

$\alpha=1$ → Lasso; $\alpha=0$ → Ridge.

## Worked / Practical Example

ชุด lag1, lag2, ma4, ma8 และ macro predictorsอาจ correlated. Elastic Netสามารถเก็บหลาย related featuresพร้อม shrinkแทนการสุ่มเลือกหนึ่งตัวเหมือน Lasso.

## Assumptions and Interpretation

- Parameter namingต่างกันระหว่าง packages เช่น `alpha`, `l1_ratio`, `lambda`; อ่าน documentation.
- Nested/rolling CVเหมาะเมื่อใช้กับ time series.

## When to use

- correlated high-dimensional features.
- ต้องการ compromiseระหว่าง sparsityและ stability.

## When not to use / Limitations

- ถ้า groupsมีความหมายชัดและอยาก selectทั้ง group → Group Lasso.

## Common Mistakes

- สับสน alpha/lambdaข้าม R/Python packages.
- tuneบน test.
- ไม่ standardize.

## Quick Review

- **Concept:** Elastic Net ผสม L1 และ L2 penalties เพื่อได้ sparsityแบบ Lassoพร้อม grouping/stabilityต่อ correlated predictorsคล้าย Ridge.
- **สิ่งที่ต้องจำ:** Mixing parameterกำหนดสัดส่วน L1 vs L2.
- **การใช้งาน:** correlated high-dimensional features.
- **ข้อควรระวัง:** สับสน alpha/lambdaข้าม R/Python packages.

## Related Notes

- [[Ridge Regression]]
- [[Lasso Regression]]
- [[Group and Sparse Group Lasso]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[11-RegularizedRegression_260718_091112]] | Elastic net section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `11-RegularizedRegression_260718_091112.pdf` — Elastic net section

## External References

- [scikit-learn User Guide — Linear Models (Ridge, Lasso, Elastic Net, Logistic Regression).](https://scikit-learn.org/stable/modules/linear_model.html)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น

## DADS6003 Enrichment

Elastic Net ผสม L1 และ L2 เหมาะเมื่ออยากได้ทั้ง sparsity และ stability โดยเฉพาะเมื่อ predictors มี correlation สูง. ทั้ง mixing ratio และ overall regularization strength เป็น hyperparameters ที่ต้อง tune จากข้อมูล training/validation เท่านั้น.

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 6 - Regularization]] | Slides 20–27 | Elastic Net intuition, geometry and comparison |
