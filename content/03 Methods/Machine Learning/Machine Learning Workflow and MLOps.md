---
title: "Machine Learning Workflow and MLOps"
aliases:
  - ML Workflow
  - MLOps
topic_number: 64
domain:
  - Data Science
  - Machine Learning
language: th
source_type:
  - lecture
tags:
  - machine-learning
  - mlops
  - workflow
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Machine Learning Workflow and MLOps

> [!abstract] Summary
> ML workflow เชื่อม business objective → data → problem formulation → training/validation → deployment → monitoring; MLOps ทำให้วงจรนี้ reproducible, observable และ maintainable.

## Why this concept matters

Model ที่ดีใน notebook อาจล้มใน production หาก feature pipeline ไม่ตรง, data drift, latency, versioning หรือ monitoring ไม่ดี.

## Core Idea

- เริ่มจาก desired outcome และ decision ที่ model จะสนับสนุน.
- กำหนด target, features, split strategy และ metric ก่อน model search.
- version data/code/model; track experiments; validate schema and leakage.
- หลัง deploy ต้อง monitor performance, drift, calibration, latency และ failure modes.

## Mathematical Formulation / Technical Detail

สามารถมอง production objective เป็น constrained optimization:

\[
\text{maximize business utility}
\quad \text{s.t.}\quad
\text{accuracy, latency, cost, fairness, reliability constraints}.
\]

ดังนั้น offline metric เป็นเพียงส่วนหนึ่งของ system objective.

## Worked / Practical Example

Fraud model AUC ดีขึ้น 1% แต่ latency เพิ่ม 500 ms และ false positives กระทบลูกค้า อาจทำให้ system outcome แย่ลง. Workflow ต้องประเมิน model + decision threshold + operations ร่วมกัน.

## When to use

- โปรเจกต์ ML ที่ต้องใช้งานต่อเนื่อง/หลายคน.
- model ที่ต้อง retrain หรือ monitor หลัง deployment.

## Limitations / Assumptions

- MLOps tooling ไม่ทดแทน statistical validation.
- Drift detection ไม่ได้บอกสาเหตุโดยอัตโนมัติ.
- Feedback loops อาจเปลี่ยน distribution หลัง deploy.

## Common Mistakes

- สร้าง model ก่อนกำหนด action/business KPI.
- ไม่มี holdout/test ที่ untouched.
- ไม่มี reproducible preprocessing pipeline.

## Cross-check / Corrections

- ไม่พบ correction สำคัญ; เพิ่มเฉพาะ context และ implementation caveats.

## Quick Review

- **Concept:** ML workflow เชื่อม business objective → data → problem formulation → training/validation → deployment → monitoring; MLOps ทำให้วงจรนี้ reproducible, observable และ maintainable.
- **จำให้ได้:** เริ่มจาก desired outcome และ decision ที่ model จะสนับสนุน.
- **ใช้งาน:** โปรเจกต์ ML ที่ต้องใช้งานต่อเนื่อง/หลายคน.
- **ระวัง:** สร้าง model ก่อนกำหนด action/business KPI.

## Related Notes

- [[Machine Learning Fundamentals]]
- [[Train Validation Test Split]]
- [[Cross Validation]]
- [[Classification Metrics]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 1 - Introduction]] | Slides 14–16 | ML process, MLOps, representation/optimization/evaluation |

## External References

- Software Engineering for Machine Learning: https://www.microsoft.com/en-us/research/publication/software-engineering-for-machine-learning-a-case-study/
- scikit-learn Common Pitfalls: https://scikit-learn.org/stable/common_pitfalls.html

## Verification Status

**High confidence** — lecture content was cross-checked against official scikit-learn documentation and/or Stanford CS229 materials; corrections above override conflicting lecture statements.
