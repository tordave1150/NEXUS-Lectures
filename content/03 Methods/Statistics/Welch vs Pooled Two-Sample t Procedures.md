---
title: "Welch vs Pooled Two-Sample t Procedures"
topic_number: 160
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - inference
  - t-test
  - welch
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Welch vs Pooled Two-Sample t Procedures

> [!abstract] Summary
> Welch and pooled two-sample t procedures ต่างกันที่ variance model: Welch ไม่บังคับ population variances เท่ากัน ขณะที่ pooled procedure สมมติ common variance แล้วรวมข้อมูลเพื่อ estimate variance เดียว.

## Why this concept matters

การเลือก procedure ควรขึ้นกับ design/model ไม่ใช่เลือกจาก p-value ที่ต้องการ และ Welch เป็น robust default ที่นิยมเมื่อ equality ไม่ได้รับการ justify.

## Core Idea

Welch standard error = $\sqrt{S_1^2/n_1+S_2^2/n_2}$ และใช้ Satterthwaite df. Pooled ใช้ $S_p^2=[(n_1-1)S_1^2+(n_2-1)S_2^2]/(n_1+n_2-2)$.

## Mathematical Formulation / Technical Detail

Welch df:
$\nu\approx\frac{(S_1^2/n_1+S_2^2/n_2)^2}{(S_1^2/n_1)^2/(n_1-1)+(S_2^2/n_2)^2/(n_2-1)}$.

## Worked / Practical Example

ถ้า group variances และ sizes ต่างกันมาก pooled SE สามารถผิด scale ได้; Welch ปรับแต่ละ variance แยกกัน.

## Assumptions / When to use

ทั้งสองเป็น independent-sample procedures. Paired data ต้องใช้ paired-difference analysis. Pooled methodต้องมี common-variance model ที่สมเหตุผล.

## Common Mistakes

- ทำ pretest variance แล้วเลือก t-test แบบ mechanical โดยไม่ดู design
- คิดว่า equal sample sizes = equal variances
- ใช้ pooled formula เพราะ “เป็นสูตรมาตรฐาน” ทุกกรณี

## Cross-check / Corrections

Lecture แยก $\sigma_1=\sigma_2$ vs unequal cases อย่างชัดเจน; canonical noteจัดชื่อเป็น pooled vs Welch เพื่อเชื่อมกับ software/statistical practice.

## Quick Review

- **Concept:** Welch and pooled two-sample t procedures ต่างกันที่ variance model: Welch ไม่บังคับ population variances เท่ากัน ขณะที่ pooled procedure สมมติ common variance แล้วรวมข้อมูลเพื่อ estimate variance เดียว.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Confidence Interval for Difference of Means]]
- [[Two-Sample and Paired Tests]]
- [[One-Way ANOVA]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[2ConfidenceInterval_mod]] | Two-independent-means CI sections | Welch and pooled intervals |
| [[4TestHypo]] | Two-sample mean tests | Welch and pooled tests |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
