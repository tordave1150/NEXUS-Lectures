---
title: "Jackknife Resampling"
topic_number: 141
domain:
  - Statistics
language: th
source_type:
  - lecture
tags:
  - statistics
  - resampling
  - jackknife
status: reviewed
created: 2026-08-15
updated: 2026-08-15
---

# Jackknife Resampling

> [!abstract] Summary
> Jackknife เป็น deterministic leave-one-out resampling technique สำหรับประเมิน bias และ standard error ของ estimator โดยสร้าง $n$ replicate estimates จาก sample ขนาด $n-1$.

## Why this concept matters

มีคุณค่าทั้งเชิงประวัติศาสตร์และเป็น intuition ว่า estimator เปลี่ยนแค่ไหนเมื่อข้อมูลหนึ่งจุดถูกนำออก.

## Core Idea

สำหรับ $i=1,\dots,n$ สร้าง jackknife sample ที่ตัด observation $i$ ออก แล้วคำนวณ $\hat\theta_{(i)}$. ค่าเฉลี่ย replicate คือ $\bar\theta_{(\cdot)}$.

## Mathematical Formulation / Technical Detail

Bias estimate: $\widehat{Bias}_{jack}=(n-1)(\bar\theta_{(\cdot)}-\hat\theta)$.
Bias-corrected estimate: $\hat\theta_{jack}=n\hat\theta-(n-1)\bar\theta_{(\cdot)}$.
SE: $\sqrt{\frac{n-1}{n}\sum_i(\hat\theta_{(i)}-\bar\theta_{(\cdot)})^2}$.

## Worked / Practical Example

สำหรับ sample mean jackknife replicates แตกต่างเล็กน้อยตามจุดที่ตัดออก; SE jackknife ให้ผลสอดคล้องกับ analytical SE ของ mean.

## Assumptions / When to use

เหมาะกับ smooth statistics หลายแบบ; performance อาจไม่ดีสำหรับ nonsmooth/extreme statistics บางชนิด เช่น sample maximum.

## Common Mistakes

- เรียก jackknife ว่า sampling “with replacement”
- สับสน leave-one-out CV กับ jackknife inference
- คิดว่า bias correction รับประกัน unbiased ทุกกรณี

## Cross-check / Corrections

Lecture อธิบาย jackknife เป็น resampling; canonical note ระบุชัดว่า standard delete-1 jackknife เป็น deterministic leave-one-out ไม่ใช่ random bootstrap resampling.

## Quick Review

- **Concept:** Jackknife เป็น deterministic leave-one-out resampling technique สำหรับประเมิน bias และ standard error ของ estimator โดยสร้าง $n$ replicate estimates จาก sample ขนาด $n-1$.
- **Key question:** ต้องรู้ว่าข้อมูล/การออกแบบการสุ่มรองรับสมมติฐานของวิธีนี้หรือไม่
- **Practice:** แยก parameter, estimator, uncertainty และ decision rule ออกจากกันให้ชัด

## Related Notes

- [[Statistical Inference and Estimation]]
- [[Bootstrap Resampling]]
- [[Bootstrap Confidence Intervals]]
- [[Cross Validation]]

## Source Traceability

| Source | Section / Location | Used for |
|---|---|---|
| [[3Jackknife_Bootstrap]] | Jackknife sections | bias correction and SE formulas |

## Verification Status

**Reviewed** — canonical note preserves the lecture framing while flagging assumptions, approximations, or interpretation issues that materially affect use.
