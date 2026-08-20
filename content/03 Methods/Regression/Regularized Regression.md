---
title: "Regularized Regression"
aliases:
  - Penalized Regression
  - Regularization
topic_number: 34
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

# Regularized Regression

> [!abstract] Summary
> Regularized regression เพิ่ม penaltyต่อขนาด coefficientsเพื่อ trade off fitกับ complexity ช่วยลด variance, จัดการ multicollinearity และบางวิธีทำ feature selection.

## Why this concept matters

เมื่อ predictorsจำนวนมากหรือสัมพันธ์กัน OLS coefficientsอาจ unstable; shrinkageยอมเพิ่ม biasเล็กน้อยเพื่อแลก varianceลดลงและ predictionดีขึ้น.

## Core Idea

- Ridgeใช้ L2 penalty, Lassoใช้ L1, Elastic Netผสมสองแบบ.
- Predictorsควร scale/standardizeก่อน penaltyเพื่อให้หน่วยไม่กำหนดความแรงของ shrinkage.
- Interceptมักไม่ penalize.
- Regularization strengthเป็น hyperparameterที่เลือกด้วย CV.

## Mathematical Formulation / Technical Detail

Generic penalized objective:

$$
\min_{\beta_0,\beta}
\frac1n\sum_{i=1}^n(y_i-\beta_0-x_i^\top\beta)^2
+\lambda P(\beta).
$$

Standardization:

$$
z_{ij}=\frac{x_{ij}-\bar x_j}{s_j}.
$$

## Worked / Practical Example

Gas-price exampleมี predictorsเช่น crude, lagged gas price, PDI, CPIที่ correlated. OLS coefficientsอาจเปลี่ยน sign/sizeเมื่อ sampleเปลี่ยน; regularizationทำให้ estimatesเสถียรขึ้น.

## Assumptions and Interpretation

- Mean/SDสำหรับ scalingต้องคำนวณจาก training dataเท่านั้น.
- Penalty choiceควรสัมพันธ์กับ goal เช่น stability vs sparsity.

## When to use

- many/correlated predictors.
- prediction-first regression.
- high-dimensional feature sets.

## When not to use / Limitations

- regularizationไม่แก้ leakage/endogeneity/misspecified target.
- ไม่ควรดู zero coefficientsแล้วสรุป causal irrelevance.

## Common Mistakes

- standardizeด้วย full datasetก่อน split.
- เลือก lambdaจาก test set.
- เปรียบ coefficient magnitudeก่อน scaling.

## Quick Review

- **Concept:** Regularized regression เพิ่ม penaltyต่อขนาด coefficientsเพื่อ trade off fitกับ complexity ช่วยลด variance, จัดการ multicollinearity และบางวิธีทำ feature selection.
- **สิ่งที่ต้องจำ:** Ridgeใช้ L2 penalty, Lassoใช้ L1, Elastic Netผสมสองแบบ.
- **การใช้งาน:** many/correlated predictors.
- **ข้อควรระวัง:** standardizeด้วย full datasetก่อน split.

## Related Notes

- [[Ridge Regression]]
- [[Lasso Regression]]
- [[Elastic Net]]
- [[Group and Sparse Group Lasso]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[11-RegularizedRegression_260718_091112]] | Motivation / feature scaling / OLS limitations section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `11-RegularizedRegression_260718_091112.pdf` — Motivation / feature scaling / OLS limitations section

## External References

- [scikit-learn User Guide — Linear Models (Ridge, Lasso, Elastic Net, Logistic Regression).](https://scikit-learn.org/stable/modules/linear_model.html)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น

## DADS6003 Enrichment — Bias–Variance View of Regularization

DADS6003 Week 6 ใช้ภาพ coefficient paths และ geometry เพื่ออธิบายว่า penalty บีบ parameter space อย่างไร: Ridge บีบ coefficients อย่างต่อเนื่อง ส่วน Lasso สามารถชนแกนและทำ coefficient เป็นศูนย์ได้; Elastic Net ผสมคุณสมบัติทั้งสอง.

> [!note] Heuristic, not universal law
> คำแนะนำเช่น “Ridge เป็น good default” หรือ “Lasso เมื่อเชื่อว่ามี features สำคัญไม่กี่ตัว” เป็น heuristic ที่มีประโยชน์ แต่ final choice และ $\lambda$ ควรเลือกจาก validation/CV และเป้าหมายของงาน.

### Additional Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 6 - Regularization]] | Slides 3–27 | under/overfit, L1/L2 geometry, coefficient paths, Elastic Net |
