---
title: "Bootstrap Resampling"
topic_number: 142
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - resampling
  - bootstrap
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Bootstrap Resampling

> [!abstract] Summary
> Bootstrap ประมาณ sampling distribution ของ estimator โดยสุ่มตัวอย่างขนาด $n$ **with replacement** จาก empirical distribution ของ observed sample ซ้ำหลายครั้ง.

## Why this concept matters

ทำให้ประมาณ bias, standard error และ uncertainty ได้เมื่อ analytical sampling distribution ซับซ้อนหรือไม่สะดวก.

## Core Idea

Observed sample ทำหน้าที่เป็น empirical population. แต่ละ bootstrap sample มีขนาดเท่าต้นฉบับและอนุญาต observation ซ้ำ/หาย. คำนวณ statistic ในแต่ละ resample เพื่อได้ bootstrap distribution.

## Mathematical Formulation / Technical Detail

สำหรับ $b=1,\dots,B$ คำนวณ $\hat\theta^{*b}$.
Bootstrap bias ≈ $\bar\theta^*-\hat\theta$.
Bootstrap SE = SD ของ $\hat\theta^{*1},...,\hat\theta^{*B}$.

## Worked / Practical Example

ต้องการ SE ของ median: resample rows with replacement หลายพันครั้ง, คำนวณ median ทุกครั้ง แล้วใช้ SD ของ bootstrap medians.

## Assumptions / When to use

Standard iid bootstrap สมมติ observations exchangeable/iid. Time series, clusters หรือ dependent data ต้องใช้ bootstrap scheme ที่รักษา dependence เช่น block/cluster bootstrap.

## Common Mistakes

- resample โดยไม่คืนที่
- bootstrap features/columns แทน sampling units โดยไม่ตั้งใจ
- ใช้ iid bootstrap กับ time series แล้วทำลาย dependence

## Cross-check / Corrections

Canonical note narrows the lecture claim “ใช้ได้ทุกกรณี”: bootstrap is powerful but resampling scheme must match the data-generating dependence structure and statistic regularity.

## Quick Review

- **Concept:** Bootstrap ประมาณ sampling distribution ของ estimator โดยสุ่มตัวอย่างขนาด $n$ **with replacement** จาก empirical distribution ของ observed sample ซ้ำหลายครั้ง.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Jackknife Resampling]]
- [[Bootstrap Confidence Intervals]]
- [[Time Series Cross Validation]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[3Jackknife_Bootstrap]] | Bootstrap sections | resampling, bias and SE |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
