---
title: "Text Analytics"
topic_number: 113
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - text-analytics
  - nlp
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Text Analytics

> [!abstract] Summary
> Text Analytics เปลี่ยน raw text ให้เป็น structured representations เพื่อทำ classification, clustering, sentiment analysis, NER, event extraction, topic modeling และ retrieval/semantic analysis.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Pipeline: clean/tokenize → normalize/filter → feature representation → model/task.
- Text is high-dimensional and sparse under bag-of-words representations.
- Task determines preprocessing and representation.

## Technical Detail

Classical Spark workflow in lecture uses Tokenizer/StopWords/NGram → TF-IDF/CountVectorizer/Word2Vec → classifier or LDA. Modern NLP may use contextual embeddings, but canonical note preserves lecture scope and links conceptually.

## Practical Example

Reviews → tokenize → TF-IDF → logistic regression sentiment classifier.

## When to use

ใช้เมื่อ information of interest อยู่ใน natural-language documents/messages/logs.

## Limitations / Assumptions

- Aggressive preprocessing can remove signal.
- Language/tokenization assumptions matter.
- Bag-of-words loses much word order/context.

## Common Mistakes

- remove all stop words blindly.
- treat sentiment/NER as same representation/problem.

## Cross-check / Corrections

> [!warning] Source cross-check
> Lecture terminology “Sentimental Analysis” corrected to standard **Sentiment Analysis**.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Text Analytics เปลี่ยน raw text ให้เป็น structured representations เพื่อทำ classification, clustering, sentiment analysis, NER, event extraction, topic modeling และ retrieval/semantic analysis.
- **Use when:** ใช้เมื่อ information of interest อยู่ใน natural-language documents/messages/logs.
- **Main caution:** remove all stop words blindly.

## Related Notes

- [[Text Preprocessing and N-grams]]
- [[TF-IDF and CountVectorizer]]
- [[Word2Vec and Word Embeddings]]
- [[Latent Dirichlet Allocation Topic Modeling]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 8 - Text Analytics]] | Relevant lecture/lab section | Concept, examples, caveats |

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
