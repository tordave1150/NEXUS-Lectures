---
title: "Spark ML and MLlib"
topic_number: 110
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - spark-ml
  - mllib
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Spark ML and MLlib

> [!abstract] Summary
> Spark machine-learning ecosystem มี DataFrame-based `spark.ml` pipeline APIs และ historical RDD-based `spark.mllib`; canonical workflow ควรแยก modern pipeline abstraction ออกจาก legacy examples ใน lecture.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Estimator.fit(dataset) → Model.
- Transformer.transform(dataset) → new DataFrame.
- Pipeline chains transformers/estimators.
- Vector features support dense/sparse representations.
- Distributed algorithms include regression, classification, clustering, recommendation and feature transforms depending on API.

## Technical Detail

Pipeline abstractionช่วยลด train/serve preprocessing mismatch: tokenizer → feature transform → estimator สามารถ fit/transform เป็น graph เดียว. RDD-based examples เช่น `LogisticRegressionWithSGD` เป็น historical API style.

## Practical Example

Text classification pipeline: Tokenizer → HashingTF → IDF → LogisticRegression.

## When to use

ใช้เมื่อ dataset ใหญ่และ preprocessing/modeling อยู่ใน Spark ecosystem.

## Limitations / Assumptions

- Distributed ML ไม่ได้ดีกว่า single-node ML เมื่อ data fit memory และ algorithm overhead สูง.
- Algorithm coverage differs from scikit-learn/deep learning ecosystems.

## Common Mistakes

- ประเมินบน training set อย่างเดียว.
- ใช้ deprecated/legacy RDD-based class เป็น default ใหม่.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture เรียก MLlib กับ Spark ML เป็นสอง libraries; canonical note ใช้ distinction “RDD-based legacy API vs DataFrame-based ML pipeline API” เพื่อไม่สร้างความเข้าใจว่าเป็นสอง ecosystem ที่เท่าเทียมกันตลอดไป.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Spark machine-learning ecosystem มี DataFrame-based `spark.ml` pipeline APIs และ historical RDD-based `spark.mllib`; canonical workflow ควรแยก modern pipeline abstraction ออกจาก legacy examples ใน lecture.
- **Use when:** ใช้เมื่อ dataset ใหญ่และ preprocessing/modeling อยู่ใน Spark ecosystem.
- **Main caution:** ประเมินบน training set อย่างเดียว.

## Related Notes

- [[Logistic Regression]]
- [[Ridge Regression]]
- [[Lasso Regression]]
- [[Elastic Net]]
- [[K-Means Clustering]]
- [[Alternating Least Squares Recommendation]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 7 - Machine Learning with Spark]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 7 Lab - Machine Learning with Spark]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 8 - Text Analytics]] | Relevant lecture/lab section | Concept, examples, caveats |

## External Verification

> [!cite] Verified with official Apache Spark documentation
> Current MLlib documentation identifies the **DataFrame-based `spark.ml` API as the primary API**. The RDD-based `spark.mllib` API has been in **maintenance mode since Spark 2.0**: bug fixes continue, but new features are directed to the DataFrame-based API. This is why the old `LogisticRegressionWithSGD`, `LabeledPoint`, and related RDD examples are preserved only as historical context.
>
> Reference: [Apache Spark — MLlib Main Guide](https://spark.apache.org/docs/latest/ml-guide.html)

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
