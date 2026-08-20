---
title: "Multiple Comparisons and Post Hoc Tests"
topic_number: 154
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - anova
  - multiple-comparisons
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Multiple Comparisons and Post Hoc Tests

> [!abstract] Summary
> หลัง global ANOVA reject $H_0$, multiple-comparison procedures ช่วยระบุว่าคู่/contrast ใดแตกต่างโดยจัดการ multiplicity ตามวิธีที่เลือก.

## Why this concept matters

การดู pairwise p-values แบบไม่ปรับหลายคู่เพิ่ม family-wise false-positive risk.

## Core Idea

Lecture lists LSD, Tukey HSD, Duncan, Bonferroni, Scheffé, Dunnett. แต่ละ method optimizeคนละ objective: all pairwise, comparisons-to-control, arbitrary contrasts หรือ error-rate trade-off.

## Mathematical Formulation / Technical Detail

Bonferroni family-wise control ใช้ per-comparison $\alpha/m$ สำหรับ $m$ tests. Tukey HSD ใช้ studentized-range distribution สำหรับ all pairwise mean comparisons ภายใต้ classical ANOVA assumptions.

## Worked / Practical Example

ถ้ามี 5 groups จะมี 10 pairwise comparisons. ใช้ unadjusted 0.05 ทุกคู่ทำให้ probability of at least one false positive สูงกว่า 0.05 ภายใต้ global null.

## Assumptions / When to use

เลือก post hoc method ให้ตรง analysis plan. Planned contrasts ที่กำหนดล่วงหน้าอาจไม่ต้องใช้ strategy เดียวกับ exploratory all-pairs testing.

## Common Mistakes

- ทำ post hoc ทุกครั้งแม้ global question ไม่ต้องการ pairwise
- เรียกทุก correction ว่า Bonferroni
- เลือก method หลังเห็นว่าอันไหนให้ significance มากที่สุด

## Cross-check / Corrections

Lecture groups methods together; canonical note stresses that they are not interchangeable and choice depends on contrast family/control objective.

## Quick Review

- **Concept:** หลัง global ANOVA reject $H_0$, multiple-comparison procedures ช่วยระบุว่าคู่/contrast ใดแตกต่างโดยจัดการ multiplicity ตามวิธีที่เลือก.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[One-Way ANOVA]]
- [[ANOVA Decomposition and F Test]]
- [[Type I Type II Errors and Statistical Power]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[7ANOVA_2_68_260425_131156]] | Multiple comparison / post hoc sections | post-ANOVA procedures |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
