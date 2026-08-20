---
title: "Classification Metrics"
aliases:
  - Confusion Matrix
  - Precision Recall F1
  - ROC AUC
topic_number: 58
domain:
  - Data Science
  - Statistics
language: th
source_type:
  - lecture
sources:
  - "[[S2-ML_260725_130143]]"
  - "[[DADS6003 Week 7 - Model Training and Evaluation]]"
tags:
  - data-science
status: reviewed
created: 2026-08-08
updated: 2026-08-08
---

# Classification Metrics

> [!abstract] Summary
> Classification metricsประเมินคนละมุมของ decision: confusion matrixเป็น counts, precision/recallเน้น positive class, F1 balanceสองตัว และ ROC-AUCวัด ranking discriminationข้าม thresholds.

## Why this concept matters

Accuracyอย่างเดียวอาจหลอกเมื่อ class imbalance; metricต้องสัมพันธ์กับ costของ false positive/false negativeและ threshold policy.

## Core Idea

- TP, FP, TN, FNเป็นฐานของ metrics.
- Precision = TP/(TP+FP).
- Recall/Sensitivity = TP/(TP+FN).
- Specificity = TN/(TN+FP).
- F1 = harmonic meanของ precisionและrecall.
- ROC-AUCวัด probabilityที่ random positiveได้ scoreสูงกว่า random negativeใน ranking interpretation.

## Mathematical Formulation / Technical Detail

$$
Accuracy=\frac{TP+TN}{TP+TN+FP+FN}
$$

$$
Precision=\frac{TP}{TP+FP},\quad Recall=\frac{TP}{TP+FN}
$$

$$
F1=2\frac{Precision\cdot Recall}{Precision+Recall}.
$$

## Worked / Practical Example

Fraud rate 1%: modelที่ทำนายทุกเคสเป็น negativeได้ accuracy99%แต่ recall=0. จึงต้องดู precision/recall, PR curve และ business cost.

## Assumptions and Interpretation

- Threshold-dependent metricsต้องระบุ threshold.
- AUCไม่วัด probability calibration.
- Macro/micro/weighted averagingต่างกันใน multiclass.

## When to use

- imbalanced classification.
- threshold selectionร่วมกับ cost matrix.
- compare ranking models.

## When not to use / Limitations

- F1ไม่สน true negatives จึงไม่เหมาะทุก problem.
- ROC-AUCอาจดูดีใน extreme imbalanceแม้ precisionใช้งานต่ำ; PR-AUCอาจ informativeกว่า.

## Common Mistakes

- ใช้ accuracyเพียงตัวเดียว.
- เปรียบ F1คนละ positive-class definition.
- ใช้ AUCเพื่อสรุป calibration.

## Quick Review

- **Concept:** Classification metricsประเมินคนละมุมของ decision: confusion matrixเป็น counts, precision/recallเน้น positive class, F1 balanceสองตัว และ ROC-AUCวัด ranking discriminationข้าม thresholds.
- **สิ่งที่ต้องจำ:** TP, FP, TN, FNเป็นฐานของ metrics.
- **การใช้งาน:** imbalanced classification.
- **ข้อควรระวัง:** ใช้ accuracyเพียงตัวเดียว.

## Related Notes

- [[Logistic Regression]]
- [[KNN and SVM]]
- [[Probabilistic Forecasting]]

## Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[S2-ML_260725_130143]] | Performance measures: confusion matrix, F1, AUC-ROC | Core lecture content, examples, notation |

> [!cite] Primary lecture source
> `S2-ML_260725_130143.pdf` — Performance measures: confusion matrix, F1, AUC-ROC

## External References

- [scikit-learn User Guide — Metrics and scoring.](https://scikit-learn.org/stable/modules/model_evaluation.html)

## Verification Status

**High confidence**

เนื้อหาถูกสังเคราะห์จาก lecture และ cross-check กับแหล่งอ้างอิงภายนอกข้างต้น โดยแยก rule of thumb ออกจากข้อเท็จจริงที่เป็นนิยามหรือสมบัติทางคณิตศาสตร์เมื่อจำเป็น

## DADS6003 Enrichment — MCC, ROC and PR Curve

นอกจาก Accuracy/Precision/Recall/F1 แล้ว DADS6003 เพิ่ม Matthews Correlation Coefficient (MCC):

$$
MCC=\frac{TP\cdot TN-FP\cdot FN}
{\sqrt{(TP+FP)(TP+FN)(TN+FP)(TN+FN)}}.
$$

MCC ใช้ทั้งสี่ช่องของ confusion matrix และมีประโยชน์เมื่อ classes ไม่สมดุล. ROC curve แสดง TPR เทียบ FPR ข้าม thresholds ส่วน Precision–Recall curve มัก informative มากเมื่อ positive class หายาก.

> [!warning] Threshold trade-off
> การเพิ่ม threshold มักลดจำนวน predicted positives จึง *มัก* เพิ่ม precision และลด recall แต่ไม่ใช่ mathematical guarantee ว่า precision จะ monotonic ทุก dataset. ควรตรวจ curve/metric จาก validation data จริง.

### Additional Source Traceability

| Source | Location | Used for |
|---|---|---|
| [[DADS6003 Week 7 - Model Training and Evaluation]] | Slides 10–17 | confusion matrix, MCC, F1, ROC/AUC and PR curve |
