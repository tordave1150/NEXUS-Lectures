---
title: "Spark SQL and DataFrames"
topic_number: 109
domain:
  - Data Science
  - Data Engineering
language: th
source_type:
  - lecture
  - lab
tags:
  - spark-sql
  - dataframe
status: reviewed
created: 2026-08-09
updated: 2026-08-09
---

# Spark SQL and DataFrames

> [!abstract] Summary
> Spark DataFrame คือ distributed table-like abstraction ที่มี named columns/schema ทำให้ Spark SQL optimizer สามารถ plan/optimize structured computations ได้เหนือ RDD-level object operations.

## Why this concept matters

หัวข้อนี้ช่วยเชื่อม Big Data architecture กับการใช้งานจริง และทำให้เลือก storage / compute / ingestion / analytical abstraction ได้ตาม workload แทนการจำชื่อเครื่องมือแยกส่วน.

## Core Idea

- Schema enables type/column-aware planning.
- DataFrames are immutable logical datasets.
- select/filter/groupBy/orderBy are common transformations/actions combinations.
- SQL and DataFrame APIs share execution engine.

## Technical Detail

Current-style mental model คือ `SparkSession` เป็น entry point หลักสำหรับ DataFrame/SQL workflows; lecture `SQLContext`/`registerAsTable` examples เป็น legacy API style.

## Practical Example

อ่าน Parquet/CSV → DataFrame → filter/groupBy → write partitioned output หรือ register temp view เพื่อ SQL query.

## When to use

ใช้กับ structured/semi-structured ETL, aggregation, feature prep และ SQL analytics.

## Limitations / Assumptions

- Schema inference can be expensive/ambiguous; explicit schema often better for production.
- Python UDFs can reduce optimizer/codegen benefits.

## Common Mistakes

- แปลงทุกอย่างเป็น RDD โดยไม่จำเป็น.
- ใช้ legacy `registerAsTable` blindly.

## Cross-check / Corrections

> [!warning] Source cross-check
> Canonical note mark `SQLContext` และ `registerAsTable` ใน lecture/lab เป็น legacy style; เน้น SparkSession/DataFrame semantics โดยไม่คัดลอก old setup commands.

> [!note] Version-sensitive software
> สำหรับ Hadoop ecosystem / Spark / Kafka / Hive / HBase และ tooling ที่มี API/command ใน lecture ให้ยึด **core concept** ใน note นี้ ส่วน exact setup command หรือ API signature ต้องตรวจตาม version ของ environment ที่ใช้งานจริง. Lab ในชุดนี้มีหลายส่วนที่เป็น legacy environment และถูกเก็บเพื่อการเรียนรู้ย้อนหลังเท่านั้น.

## Quick Review

- **Concept:** Spark DataFrame คือ distributed table-like abstraction ที่มี named columns/schema ทำให้ Spark SQL optimizer สามารถ plan/optimize structured computations ได้เหนือ RDD-level object operations.
- **Use when:** ใช้กับ structured/semi-structured ETL, aggregation, feature prep และ SQL analytics.
- **Main caution:** แปลงทุกอย่างเป็น RDD โดยไม่จำเป็น.

## Related Notes

- [[Apache Spark]]
- [[Spark RDD]]
- [[Spark ML and MLlib]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[BigData 6 - Spark SQL]] | Relevant lecture/lab section | Concept, examples, caveats |
| [[BigData 6 Lab - Spark SQL]] | Relevant lecture/lab section | Concept, examples, caveats |

## External Verification

> [!cite] Verified with official Apache Spark documentation
> The lab's `SQLContext` examples are Spark 1.x-era style. Official Spark API documentation states that **SparkSession replaced SQLContext as the structured-data entry point starting in Spark 2.0**. Canonical examples should therefore prefer `SparkSession` unless reproducing the legacy lab environment.
>
> Reference: [PySpark — SparkSession](https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.SparkSession.html)

## Verification Status

**Moderate–High conceptual confidence.** Source-derived concepts were reconciled internally across lecture + lab files. Version-specific commands/APIs are explicitly treated as legacy/version-sensitive rather than silently presented as current.
