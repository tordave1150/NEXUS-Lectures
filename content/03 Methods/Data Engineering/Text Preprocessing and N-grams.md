---
title: "Text Preprocessing and N-grams"
topic_number: 114
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - tokenization
  - ngrams
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Text Preprocessing and N-grams

> [!abstract] Summary
> Text preprocessing transforms documents into tokens/features through tokenization, normalization, stop-word handling and n-gram extraction, with choices driven by downstream task.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Tokenizer splits text into tokens.
- Stop-word removal may reduce common noise but can remove meaning.
- N-grams retain short local sequences.
- Preprocessing should be fit/applied consistently across train/test.

## Technical Detail

Unigram ignores local word order; bigram/trigram expand vocabulary and sparsity but can capture phrases such as “not good”.

## Practical Example

`not good` sentiment can be lost if `not` removed; bigram preserves phrase effect.

## When to use

ใช้กับ classical NLP/feature pipelines.

## Limitations / Assumptions

- Tokenization varies by language/domain.
- N-gram dimensionality grows rapidly.

## Common Mistakes

- remove negation as stopword for sentiment.
- fit vocabulary using test data.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture says Tokenizer lowercases; exact behavior is transformer/version-specific. Canonical note treats lowercasing as a separate normalization choice rather than universal tokenizer definition.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Text preprocessing transforms documents into tokens/features through tokenization, normalization, stop-word handling and n-gram extraction, with choices driven by downstream task.
- **Use when:** ใช้กับ classical NLP/feature pipelines.
- **Main caution:** remove negation as stopword for sentiment.

## Related Notes

- [[Text Analytics]]
- [[TF-IDF and CountVectorizer]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 8 - Text Analytics]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
