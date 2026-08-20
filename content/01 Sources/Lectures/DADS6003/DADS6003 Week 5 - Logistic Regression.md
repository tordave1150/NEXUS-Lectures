---
title: "DADS6003 Week 5 - Logistic Regression"
source_type: lecture
course: DADS6003
document: "DADS6003_week5_logistic_reg_260301_155827.pdf"
author: "Ekarat Rattagan"
language:
  - en
  - th-annotations
reliability: "Moderate → High after cross-check"
status: reviewed
created: 2026-08-08
updated: 2026-08-08
tags:
  - source
  - lecture
  - dads6003
---

# Week 5: Logistic Regression

## Document Metadata

- **Course:** DADS6003
- **Lecturer:** Ekarat Rattagan
- **File:** `DADS6003_week5_logistic_reg_260301_155827.pdf`
- **Slides:** 1–17
- **Type:** Lecture PDF with handwritten annotations
- **Drive:** https://drive.google.com/file/d/1Er-t_WSTJBsuy8J_aLxj9AdJxVSbRKXA/view
- **Reliability:** Moderate as lecture material; important formulas, definitions and worked examples cross-checked against official scikit-learn documentation and Stanford CS229 material.

## Topics / Slide Map

| Topic | Location |
|---|---|
| Sigmoid and logistic model | Slides 2–4 |
| Decision boundaries | Slides 5–6 |
| Log loss / negative log-likelihood | Slides 7–13 |
| Odds and logit interpretation | Slides 14–16 |

## Canonical Notes

- [[Logistic Regression]]
- [[Likelihood MLE NLL]]
- [[Classification Metrics]]

## Reliability / Cross-check Notes

- 0.5 เป็น default threshold ที่พบบ่อย แต่ไม่ใช่ threshold ที่เหมาะที่สุดทุก business problem; threshold ควรสัมพันธ์กับ cost ของ FP/FN และ metric ที่สนใจ.
- Cross-entropy/log-loss เป็น negative log-likelihood สำหรับ Bernoulli logistic model และทำให้ linear logistic objective เป็น convex เมื่อใช้ convex penalty.

> [!warning] Use lecture as a learning source, not as unquestioned ground truth
> สูตร, numerical example, terminology และ rule of thumb ที่มีผลต่อการใช้งานจริงจะถูกเก็บใน canonical note หลัง cross-check แล้ว หาก lecture ขัดกับ standard reference canonical note จะเก็บทั้ง original claim และ correction อย่างชัดเจน.

## Source Traceability

Canonical notesที่ link มายัง source นี้ควรอ้างรูปแบบ:
`[Source: DADS6003_week5_logistic_reg_260301_155827.pdf, slide <n>]`
