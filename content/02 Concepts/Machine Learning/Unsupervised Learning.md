---
title: "Unsupervised Learning"
aliases:
  - Unsupervised ML
topic_number: 62
domain:
  - Data Science
  - Machine Learning
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - unsupervised-learning
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Unsupervised Learning

> [!abstract] Summary
> Unsupervised Learning วิเคราะห์ \(X\) ที่ไม่มี target label เพื่อค้นหา structure เช่น clusters, low-dimensional representation, density หรือ anomalies.

## Why this concept matters

ช่วย exploratory analysis, segmentation, representation learning และ preprocessing แต่ evaluation ยากกว่า supervised learning เพราะไม่มี ground truth target โดยตรง.

## Core Idea

- ข้อมูลอยู่ในรูป \(D=\{x_i\}_{i=1}^{n}\).
- งานสำคัญ: clustering, dimensionality reduction, density estimation, anomaly detection.
- คุณภาพของ representation/cluster ต้องตีความร่วมกับ domain objective; metric ภายในอย่าง silhouette ไม่ได้พิสูจน์ business usefulness.

## Mathematical Formulation / Technical Detail

ไม่มี objective เดียวสำหรับ unsupervised learning. ตัวอย่าง k-means minimize within-cluster sum of squares:

\[
\min_{\mu_1,\dots,\mu_K}\sum_i\min_k\|x_i-\mu_k\|_2^2.
\]

PCA หา directions ที่อธิบาย variance สูงสุดภายใต้ orthogonality constraints.

## Worked / Practical Example

Customer segmentation อาจ cluster ลูกค้าตาม usage/spend แล้วตรวจว่า clusters มีพฤติกรรมและ action ที่แตกต่างจริงหรือไม่; ไม่ควรตั้งชื่อ persona จาก cluster ก่อน validation.

## When to use

- ไม่มี label แต่ต้องการค้นหา structure.
- ใช้สร้าง features/embeddings ก่อน downstream task.

## Limitations / Assumptions

- Cluster IDs ไม่มี inherent semantic meaning.
- Scaling และ distance metric เปลี่ยนผลได้มาก.
- ผลลัพธ์อาจ unstable และขึ้นกับ hyperparameters.

## Common Mistakes

- ตีความ cluster เป็น 'truth' โดยไม่ตรวจ stability/domain validity.
- ใช้ target information แอบเข้า feature engineering แล้วเรียกว่า unsupervised.

## Cross-check / Corrections

- ไม่พบ correction สำคัญ; เพิ่มเฉพาะ context และ implementation caveats.

## Quick Review

- **Concept:** Unsupervised Learning วิเคราะห์ \(X\) ที่ไม่มี target label เพื่อค้นหา structure เช่น clusters, low-dimensional representation, density หรือ anomalies.
- **จำให้ได้:** ข้อมูลอยู่ในรูป \(D=\{x_i\}_{i=1}^{n}\).
- **ใช้งาน:** ไม่มี label แต่ต้องการค้นหา structure.
- **ระวัง:** ตีความ cluster เป็น 'truth' โดยไม่ตรวจ stability/domain validity.

## Related Notes

- [[Machine Learning Fundamentals]]
- [[Feature Scaling]]
- [[K-Nearest Neighbors]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 1 - Introduction]] | Slides 10–11 | unsupervised tasks and examples |

## External References

- scikit-learn User Guide: https://scikit-learn.org/stable/unsupervised_learning.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
