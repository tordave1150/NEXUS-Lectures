---
title: "K-Means Clustering"
topic_number: 112
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - kmeans
  - clustering
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# K-Means Clustering

> [!abstract] Summary
> K-Means แบ่ง observations เป็น K clusters โดย minimize within-cluster squared distances to centroids ผ่านการสลับ assign points และ update centroids.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Choose K centroids/init.
- Assignment step: nearest centroid.
- Update step: centroid = cluster mean.
- Repeat until convergence/stopping.

## Technical Detail

Objective: \(\sum_i \|x_i-\mu_{c_i}\|^2\). Feature scaling สำคัญเพราะ Euclidean distance sensitive to scale. Initialization and K selection affect result.

## Practical Example

Customer features standardized → K-Means → inspect centroids and cluster sizes.

## When to use

เหมาะกับ roughly compact/spherical clusters ใน metric space.

## Limitations / Assumptions

- Sensitive to scale/outliers/initialization.
- Requires K.
- Poor for non-convex or variable-density clusters.

## Common Mistakes

- เรียก sum of Euclidean distances ว่า WSSSE; SSE ต้อง sum **squared** distances.
- evaluate training compactness อย่างเดียวโดยไม่ inspect stability/business meaning.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lab function takes `sqrt` then sums distances but labels WSSSE; canonical note corrects distinction between within-cluster **sum of squared errors** and sum of Euclidean distances.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** K-Means แบ่ง observations เป็น K clusters โดย minimize within-cluster squared distances to centroids ผ่านการสลับ assign points และ update centroids.
- **Use when:** เหมาะกับ roughly compact/spherical clusters ใน metric space.
- **Main caution:** เรียก sum of Euclidean distances ว่า WSSSE; SSE ต้อง sum **squared** distances.

## Related Notes

- [[Unsupervised Learning]]
- [[Feature Scaling]]
- [[Spark ML and MLlib]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 7 - Machine Learning with Spark]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 7 Lab - Machine Learning with Spark]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
