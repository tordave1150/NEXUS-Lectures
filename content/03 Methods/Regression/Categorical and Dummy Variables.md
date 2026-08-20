---
title: "Categorical and Dummy Variables"
aliases:
  - Dummy Variables
  - Indicator Variables
  - Categorical Regression
topic_number: 20
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[07-Regression-Categorical_260629_205921]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Categorical and Dummy Variables

> [!abstract] Summary
> Dummy/indicator variables แปลง categorical levels ให้เข้าสู่ regression โดยใช้ 0/1 coding และตีความ coefficient เทียบกับ baseline category.

## Why this concept matters

Categorical predictors เช่น gender, route type, mode, holiday หรือ customer segment มีผลต่อ target ได้โดยไม่ควรถูก encode เป็นตัวเลขต่อเนื่องแบบมีระยะห่างปลอม.

## Core Idea

- Binary factor ต้องใช้ indicator หนึ่งตัวเมื่อ model มี intercept.
- Baseline category คือกรณี indicator=0.
- Dummy coefficient เป็น difference in intercept เทียบ baseline เมื่อ predictors อื่นคงที่.
- การเปลี่ยน baseline เปลี่ยน coefficient representationแต่ fitted valuesไม่เปลี่ยน.

## Mathematical Formulation / Technical Detail

Binary dummy:

$$
D_i=
\begin{cases}
1,& \text{category A}\\
0,& \text{baseline B}
\end{cases}
$$

Regression:

$$
\hat y=\beta_0+\beta_1x+\beta_2D.
$$

Baseline: $\hat y=\beta_0+\beta_1x$; category A: $\hat y=(\beta_0+\beta_2)+\beta_1x$.

## Worked / Practical Example

Bank salary example: ถ้า Female coefficient = -8011.89 หลังคุม years experience ผลหมายถึง predicted salary ต่ำกว่า baseline male ประมาณ 8012 ใน specification นี้ ไม่ได้พิสูจน์ causal discrimination เพราะ omitted variables/design ยังสำคัญ.

## Assumptions and Interpretation

- Category labels nominal ไม่ควร encode 1,2,3 แล้วใช้ slope เว้นแต่ ordinal structureถูก model อย่างตั้งใจ.
- Inference ตีความ conditional on variables ที่ใส่ใน model.

## When to use

- binary categories.
- holiday/event indicators.
- policy/regime flags.

## When not to use / Limitations

- ไม่ใช้ dummy codingเป็นเครื่องมือแก้ confoundingทั้งหมด.
- high-cardinality categoriesอาจต้อง regularization/hierarchical methods.

## Common Mistakes

- สร้าง dummy ครบทุก levelพร้อม intercept (dummy-variable trap).
- ตีความ baselineว่า 'ไม่มีผล'.
- สรุป causal effect จาก observational regression.

## Quick Review

- **Concept:** Dummy/indicator variables แปลง categorical levels ให้เข้าสู่ regression โดยใช้ 0/1 coding และตีความ coefficient เทียบกับ baseline category.
- **สิ่งที่ต้องจำ:** Binary factor ต้องใช้ indicator หนึ่งตัวเมื่อ model มี intercept.
- **การใช้งาน:** binary categories.
- **ข้อควรระวัง:** สร้าง dummy ครบทุก levelพร้อม intercept (dummy-variable trap).

## Related Notes

- [[Multi-level Categorical Regression]]
- [[Seasonal Dummy Variables and Interaction]]
- [[Logistic Regression]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[07-Regression-Categorical_260629_205921]] | Two-level dummy variable section | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `07-Regression-Categorical_260629_205921.pdf` — Two-level dummy variable section

## External References

- [Hyndman, R.J. & Athanasopoulos, G. (2021), Forecasting: Principles and Practice, 3rd ed. Online updated 9 Mar 2026.](https://otexts.com/fpp3/)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น
