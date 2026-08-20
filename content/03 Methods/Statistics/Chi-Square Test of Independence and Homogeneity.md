---
title: "Chi-Square Test of Independence and Homogeneity"
topic_number: 151
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - categorical-data
  - chi-square
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Chi-Square Test of Independence and Homogeneity

> [!abstract] Summary
> Chi-square independence และ homogeneity ใช้ contingency tables และ Pearson chi-square statistic เดียวกัน แต่ต่างกันที่ sampling design และคำถามเชิงประชากร.

## Why this concept matters

ช่วยวิเคราะห์ความสัมพันธ์ระหว่าง categorical variables และเปรียบเทียบ category distributions ระหว่าง populations/groups.

## Core Idea

Independence: sample จาก population เดียวแล้วถามว่า row/column variables independent หรือไม่. Homogeneity: samples จากหลาย populations/groups แล้วถามว่า category proportions เหมือนกันหรือไม่.

## Mathematical Formulation / Technical Detail

Expected cell under independence/homogeneity:
$E_{ij}=\frac{(\text{row }i\text{ total})(\text{column }j\text{ total})}{n}$.
Statistic $\chi^2=\sum_{ij}(O_{ij}-E_{ij})^2/E_{ij}$, df $(r-1)(c-1)$.

## Worked / Practical Example

เพศ × preference table: expected count ของ cell คำนวณจาก marginal totals; large deviation aggregate ให้ evidence against independence.

## Assumptions / When to use

Observations ต้อง independent ตาม sampling unit; small expected counts อาจต้อง exact/Monte Carlo alternatives. Effect size เช่น Cramér's V อาจต้องรายงานเพิ่มสำหรับ practical strength.

## Common Mistakes

- บอกว่า significant chi-square แปลว่า causal relationship
- ใช้ percentages โดยไม่เก็บ sample-size weights
- สับสน independence vs homogeneity โดยไม่ดู design

## Cross-check / Corrections

Canonical note separates the two tests by design even though formula/df coincide; lecture appropriately presents them as distinct applications.

## Quick Review

- **Concept:** Chi-square independence และ homogeneity ใช้ contingency tables และ Pearson chi-square statistic เดียวกัน แต่ต่างกันที่ sampling design และคำถามเชิงประชากร.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Conditional Probability and Independence]]
- [[Chi-Square Goodness-of-Fit Test]]
- [[Hypothesis Testing Fundamentals]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[6ChiSquare_2_68_260328_154515]] | Homogeneity / independence sections | contingency-table chi-square |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
