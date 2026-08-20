---
title: "Machine Learning Fundamentals"
aliases:
  - ML Fundamentals
  - Introduction to Machine Learning
topic_number: 60
domain:
  - Data Science
  - Machine Learning
language: th
source_type:
  - lecture
tags:
  - data-science
  - machine-learning
  - foundation
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Machine Learning Fundamentals

> [!abstract] Summary
> Machine Learning (ML) คือการสร้างระบบที่เรียน pattern จาก data เพื่อทำ task โดยวัดความสำเร็จด้วย performance measure และต้อง generalize ไปยังข้อมูลที่ไม่เคยเห็น ไม่ใช่เพียงจำ training set.

## Why this concept matters

หัวข้อนี้เป็นแผนที่ใหญ่ของ ML: ช่วยแยก task, data, model representation, optimization และ evaluation ก่อนลงรายละเอียด algorithm แต่ละชนิด.

## Core Idea

- คิด problem เป็นอย่างน้อย 3 ส่วน: **Task (T)**, **Experience/Data (E)** และ **Performance measure (P)**.
- ML algorithm มีทั้ง representation (model family), objective/loss และ optimization procedure.
- Training performance ไม่พอ; เป้าหมายจริงคือ generalization บน unseen data.
- ชนิดหลักที่ใช้ใน course คือ [[Supervised Learning]], [[Unsupervised Learning]] และ [[Reinforcement Learning]].

## Mathematical Formulation / Technical Detail

ให้ dataset \(D\), model \(f(x;\theta)\) และ loss \(L(y,f(x;\theta))\) การเรียนแบบ supervised มักเขียนเชิง empirical risk เป็น

\[
\hat\theta = \arg\min_\theta \frac{1}{n}\sum_{i=1}^{n}L(y_i,f(x_i;\theta)) + \Omega(\theta),
\]

โดย \(\Omega(\theta)\) เป็น regularization term เมื่อมี. สิ่งสำคัญคือ objective บน training set เป็น proxy ของ expected/generalization risk ไม่ใช่เป้าหมายสุดท้ายเอง.

## Worked / Practical Example

Spam detection: T = classify spam/not-spam, E = labeled emails, P อาจเป็น F1 หรือ cost-weighted metric. ถ้า class imbalance สูง accuracy อาจ misleading จึงต้องเลือก P ให้ตรง business cost.

## When to use

- เริ่มโปรเจกต์ ML ใหม่และต้องกำหนด problem formulation.
- ใช้เป็น prerequisite ก่อนเลือก algorithm หรือ metric.

## Limitations / Assumptions

- คำว่า 'เรียนรู้' ไม่ได้แปลว่า model เข้าใจเหตุผลแบบมนุษย์.
- No Free Lunch: ไม่มี algorithm เดียวดีที่สุดทุก dataset/problem.
- Data quality, leakage และ deployment drift มีผลพอ ๆ กับ model choice.

## Common Mistakes

- เริ่มเลือก model ก่อนนิยาม target/metric.
- ใช้ training accuracy เป็นหลักฐานว่า model ดี.
- สับสน prediction กับ causal inference.

## Cross-check / Corrections

- ไม่พบ correction สำคัญ; เพิ่มเฉพาะ context และ implementation caveats.

## Quick Review

- **Concept:** Machine Learning (ML) คือการสร้างระบบที่เรียน pattern จาก data เพื่อทำ task โดยวัดความสำเร็จด้วย performance measure และต้อง generalize ไปยังข้อมูลที่ไม่เคยเห็น ไม่ใช่เพียงจำ training set.
- **จำให้ได้:** คิด problem เป็นอย่างน้อย 3 ส่วน: **Task (T)**, **Experience/Data (E)** และ **Performance measure (P)**.
- **ใช้งาน:** เริ่มโปรเจกต์ ML ใหม่และต้องกำหนด problem formulation.
- **ระวัง:** เริ่มเลือก model ก่อนนิยาม target/metric.

## Related Notes

- [[Supervised Learning]]
- [[Unsupervised Learning]]
- [[Reinforcement Learning]]
- [[Machine Learning Workflow and MLOps]]
- [[Bias Variance Tradeoff]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 1 - Introduction]] | Slides 3–19 | definitions, ML types, representation/optimization/evaluation |

## External References

- scikit-learn Model Selection: https://scikit-learn.org/stable/model_selection.html
- Stanford CS229 syllabus: https://cs229.stanford.edu/syllabus-fall2020.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
