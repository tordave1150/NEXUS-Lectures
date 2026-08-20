---
title: "TF-IDF and CountVectorizer"
topic_number: 115
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - tfidf
  - countvectorizer
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# TF-IDF and CountVectorizer

> [!abstract] Summary
> TF-IDF และ count vectorization แปลง documents เป็น sparse numeric vectors จาก vocabulary; TF-IDF downweights terms ที่พบแพร่หลายข้าม documents.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- CountVectorizer learns vocabulary and produces counts.
- HashingTF avoids explicit vocabulary via hashing.
- IDF weights terms based on document frequency.
- TF-IDF = TF × IDF under a chosen convention.

## Technical Detail

IDF formula differs across libraries (smoothing/offset). Lecture gives Spark-specific smoothed form; canonical note thereforeไม่ยก formula เดียวเป็น universal TF-IDF definition.

## Practical Example

Document “spark data data” → term counts; common corpus-wide words get smaller IDF weight.

## When to use

ใช้กับ classical text classification, similarity, clustering, retrieval baselines.

## Limitations / Assumptions

- High-dimensional sparse vectors.
- Hash collisions with hashing trick.
- Vocabulary drift.

## Common Mistakes

- compare TF-IDF weights across tools without checking formula.
- fit IDF on test corpus.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture formula is retained as **Spark/library convention** rather than universal definition.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** TF-IDF และ count vectorization แปลง documents เป็น sparse numeric vectors จาก vocabulary; TF-IDF downweights terms ที่พบแพร่หลายข้าม documents.
- **Use when:** ใช้กับ classical text classification, similarity, clustering, retrieval baselines.
- **Main caution:** compare TF-IDF weights across tools without checking formula.

## Related Notes

- [[Text Analytics]]
- [[Text Preprocessing and N-grams]]
- [[Word2Vec and Word Embeddings]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 8 - Text Analytics]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
