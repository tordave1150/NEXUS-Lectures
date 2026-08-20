---
title: "Group and Sparse Group Lasso"
aliases:
  - Group Lasso
  - Sparse Group Lasso
  - SGL
topic_number: 38
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[11-RegularizedRegression_260718_091112]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Group and Sparse Group Lasso

> [!abstract] Summary
> Group Lassoเลือกหรือตัด predictorsเป็นกลุ่ม ส่วน Sparse Group Lassoเพิ่ม L1 penaltyเพื่อให้เกิด sparsityทั้งระดับกลุ่มและภายในกลุ่ม.

## Why this concept matters

มีประโยชน์เมื่อ featuresมี structureเชิง domain เช่น dummy setของ categorical variable, Fourier pair, lag block หรือ sensor group.

## Core Idea

- Group Lassoใช้ group-wise L2 normภายใต้ outer L1-like sum.
- Sparse Group Lassoผสม group penaltyกับ element-wise L1.
- Group definitionsต้องกำหนดก่อน fitจาก domain/design ไม่ใช่จาก test outcome.
- Scalingระหว่าง groupsสำคัญ; penalty weightsมักปรับตาม group size.

## Mathematical Formulation / Technical Detail

Group Lasso schematic:

$$
\min_\beta L(\beta)+\lambda\sum_{g=1}^G w_g\|\beta_g\|_2.
$$

Sparse Group Lasso:

$$
\min_\beta L(\beta)+
\lambda\left[
(1-\alpha)\sum_g w_g\|\beta_g\|_2+
\alpha\|\beta\|_1
\right].
$$

## Worked / Practical Example

Seasonality represented by sine/cosine pairสามารถเป็น groupเพื่อให้ modelเก็บหรือตัด harmonicเป็นคู่. Sparse Group Lassoยังอนุญาตบาง coefficientใน groupลดเป็น zero.

## Assumptions and Interpretation

- Groupsอาจ overlapใน extensionsแต่ standard formulationมัก non-overlapping.
- Hyperparametersต้อง cross-validate.

## When to use

- structured feature selection.
- one-hot groups, Fourier pairs, sensor blocks.

## When not to use / Limitations

- groupingผิดเชิง domainอาจบังคับ selectionที่ไม่เหมาะ.
- small groupsจำนวนมากอาจแทบไม่ต่าง Lasso.

## Common Mistakes

- ใช้ Group Lassoแต่ไม่ปรับ penaltyตาม group size.
- เอา correlated variablesมาจัด groupหลังดู test results.
- สรุป selected groupsเป็น causal drivers.

## Quick Review

- **Concept:** Group Lassoเลือกหรือตัด predictorsเป็นกลุ่ม ส่วน Sparse Group Lassoเพิ่ม L1 penaltyเพื่อให้เกิด sparsityทั้งระดับกลุ่มและภายในกลุ่ม.
- **สิ่งที่ต้องจำ:** Group Lassoใช้ group-wise L2 normภายใต้ outer L1-like sum.
- **การใช้งาน:** structured feature selection.
- **ข้อควรระวัง:** ใช้ Group Lassoแต่ไม่ปรับ penaltyตาม group size.

## Related Notes

- [[Regularized Regression]]
- [[Lasso Regression]]
- [[Elastic Net]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[11-RegularizedRegression_260718_091112]] | Extensions: Group & Sparse Group Lasso | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `11-RegularizedRegression_260718_091112.pdf` — Extensions: Group & Sparse Group Lasso

## External References

- [Yuan, M. & Lin, Y. (2006), Model Selection and Estimation in Regression with Grouped Variables, JRSSB 68(1), 49–67.](https://doi.org/10.1111/j.1467-9868.2005.00532.x)
- [Simon, N., Friedman, J., Hastie, T. & Tibshirani, R. (2013), A Sparse-Group Lasso, JCGS 22(2), 231–245.](https://doi.org/10.1080/10618600.2012.681250)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
