---
title: "Permutation Tests"
topic_number: 149
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - resampling
  - permutation-test
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Permutation Tests

> [!abstract] Summary
> Permutation test สร้าง null distribution โดย reassign/reorder labels หรือ pairings ตาม invariance/exchangeability ที่ $H_0$ อนุญาต แล้วเปรียบเทียบ observed statistic กับ distribution นั้น.

## Why this concept matters

เป็น resampling-based inference ที่ลด reliance บน parametric distribution แต่ exactness ขึ้นกับ permutation scheme และ null hypothesis.

## Core Idea

ไม่ได้มี permutation แบบเดียวสำหรับทุกปัญหา: independent groups, paired samples และ association tests ต้อง permute คนละ object. Exact test enumerate distinct rearrangements; randomized test sample เพียงบางส่วน.

## Mathematical Formulation / Technical Detail

Generic p-value = proportion ของ null statistics ที่ extreme อย่างน้อย observed statistic (พร้อม convention สำหรับ equality/finite randomization). Number of distinct permutations มักเล็กกว่า $n!$ สำหรับ two-group partition เพราะ order ภายในกลุ่มไม่สำคัญต่อหลาย statistics.

## Worked / Practical Example

สอง independent groups ขนาด $n_1,n_2$: pool observations แล้ว reassign เป็น groups ขนาดเดิมในทุก distinct partition หรือสุ่ม subset ของ partitions.

## Assumptions / When to use

ต้องมี exchangeability/random assignment structure ภายใต้ null ที่ justify permutation. Dependent/heteroskedastic structures อาจต้อง studentization หรือ specialized scheme.

## Common Mistakes

- permute raw values อย่างเดียวแล้ว statistic invariant จึงไม่ได้ null distribution ที่มีความหมาย
- คิดว่าทุก permutation test มี $n!$ distinct states
- คิดว่า nonparametric = assumption-free

## Cross-check / Corrections

Lecture correctly emphasizes exchangeability แต่ statement ว่า “สุ่มแบบใดก็ได้/อาจไม่ต้อง random sample” ต้องตีความระวัง: validity ยังต้องมี randomization/exchangeability mechanism ที่สอดคล้องกับ null. SciPy official docs แยก independent, samples และ pairings permutation schemes ชัดเจน.

## Quick Review

- **Concept:** Permutation test สร้าง null distribution โดย reassign/reorder labels หรือ pairings ตาม invariance/exchangeability ที่ $H_0$ อนุญาต แล้วเปรียบเทียบ observed statistic กับ distribution นั้น.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Hypothesis Testing Fundamentals]]
- [[Bootstrap Resampling]]
- [[Two-Sample and Paired Tests]]
- [[Pearson Correlation]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[5PermutationTest]] | Permutation-test principle / exchangeability / examples | permutation inference |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
